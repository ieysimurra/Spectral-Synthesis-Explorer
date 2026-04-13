# 🔧 Documentação Técnica — Síntese Espectral Explorer

## Visão Geral da Arquitetura

O Síntese Espectral Explorer é uma **aplicação web de arquivo único** (`index.html`) que combina HTML, CSS e JavaScript sem dependências externas (exceto fontes do Google Fonts). Essa escolha garante portabilidade máxima e zero configuração para uso em sala de aula.

---

## Componentes Principais

### 1. Motor de Áudio (Web Audio API)

O grafo de áudio é construído dinamicamente conforme parciais são adicionados:

```
Oscilador₁ → GainNode₁ ─┐
Oscilador₂ → GainNode₂ ──┼→ MasterGain → [Filtro?] → Analyser₁ → Analyser₂ → Destination
Osciladorₙ → GainNodeₙ ─┘
```

**Nodos utilizados:**

| Nodo | Função |
|---|---|
| `OscillatorNode` | Geração de cada parcial via `PeriodicWave` (controle de fase) |
| `GainNode` (por parcial) | Controle de amplitude individual + envelope ADSR |
| `GainNode` (master) | Volume global |
| `BiquadFilterNode` | Filtro no modo subtrativo (LP, HP, BP, Notch) |
| `AnalyserNode` ×2 | Captura de dados para visualização (tempo + frequência) |

**Controle de fase:** Diferente de `OscillatorNode.type = 'sine'`, usamos `createPeriodicWave()` com coeficientes calculados a partir do ângulo de fase desejado:

```javascript
real[1] = cos(phase × π / 180)
imag[1] = sin(phase × π / 180)
```

Isso permite controle individual de fase por parcial — essencial para as demonstrações pedagógicas sobre fase.

**Envelope ADSR:** Implementado via `AudioParam.linearRampToValueAtTime()`:

```
        A         D         S              R
  ┌─────/\────────\─────────────────────\──────┐
  │    /  \        \                     \     │
  │   /    \        ─────────────────     \    │
  │  /      \       (sustain level)        \   │
  └─/────────\──────────────────────────────\──┘
   t₀      t₀+A   t₀+A+D              noteOff
```

### 2. Sistema de Visualização

Quatro canvas independentes renderizados via `requestAnimationFrame`:

#### Forma de Onda (Tempo)

- Fonte: `AnalyserNode.getFloatTimeDomainData()`
- Renderização: Gradiente linear horizontal (verde → azul → rosa)
- Efeito glow: Segunda passagem com largura de linha 8px e opacidade reduzida

#### Espectro (Frequência)

- Fonte: `AnalyserNode.getByteFrequencyData()`
- Escala: Logarítmica (20 Hz – 16 kHz)
- Mapeamento: `bin = round(freq / nyquist × bufferLength)`
- Marcadores: Linhas tracejadas na posição de cada parcial com cor correspondente

#### Espectrograma

- Acumula colunas de dados espectrais em array circular
- Cada coluna: `Uint8Array` do `getByteFrequencyData()`
- Mapeamento de cor: HSL com matiz variável por intensidade (roxo → cyan)
- Faixa: ~35% do buffer (até ~7 kHz)

#### Decomposição de Ondas (Estática)

- **Não usa Web Audio** — cálculo puramente matemático
- Cada parcial: `y(t) = A × sin(2π × f₀ × ratio × t + φ)`
- Resultante: Soma de todos os parciais com normalização
- Pós-filtro: Aplica ganho calculado por `getFilterGain(freq)` em cada parcial

### 3. Modelo de Filtro (Decomposição)

O painel de decomposição usa uma aproximação matemática do comportamento do filtro biquad:

```javascript
// Passa-baixa
gain = 1 / √(1 + (f/fc)^(2×(1 + Q×0.5)))

// Passa-alta
gain = 1 / √(1 + (fc/f)^(2×(1 + Q×0.5)))

// Passa-banda
gain = 1 / √(1 + (Q × (f/fc - fc/f))²)

// Rejeita-banda
gain = 1 - 0.8 / (1 + (Q × (f/fc - fc/f))²)
```

> **Nota:** Essa é uma aproximação visual. O áudio real usa o `BiquadFilterNode` nativo do Web Audio API, que implementa filtros IIR de segunda ordem com precisão de 64 bits.

---

## Paleta de Cores dos Parciais

Os parciais são coloridos ciclicamente com 20 cores distintas otimizadas para contraste em fundo escuro:

```
P1:  #00e5a0  (verde)       P11: #14b8a6  (teal)
P2:  #00b8ff  (azul)        P12: #f43f5e  (vermelho)
P3:  #ff6b9d  (rosa)        P13: #8b5cf6  (roxo)
P4:  #ffd060  (dourado)     P14: #eab308  (amarelo)
P5:  #a78bfa  (lavanda)     P15: #22d3ee  (cyan)
P6:  #f97316  (laranja)     P16: #fb923c  (tangerina)
P7:  #06b6d4  (cyan escuro) P17: #c084fc  (lilás)
P8:  #ec4899  (magenta)     P18: #4ade80  (verde claro)
P9:  #84cc16  (lima)        P19: #f472b6  (pink)
P10: #e879f9  (fúcsia)      P20: #38bdf8  (sky)
```

A mesma cor é usada consistentemente na sidebar, no espectro, e no painel de decomposição.

---

## Performance

### Otimizações Implementadas

- **Canvas com `devicePixelRatio`:** Renderização nítida em telas HiDPI sem perda de performance
- **Reconstrução DOM condicional:** O painel de decomposição só reconstrói elementos HTML quando o número de parciais muda
- **Dois analysers separados:** Permite smoothing diferente para forma de onda (precisa) e espectro (suavizado)
- **Atualização em tempo real via `setTargetAtTime`:** Evita cliques ao mudar parâmetros com som reproduzindo

### Limites Conhecidos

| Aspecto | Limite | Motivo |
|---|---|---|
| Parciais simultâneos | ~20 | Cada parcial = 1 OscillatorNode + 1 GainNode |
| FFT size | 4096 | Resolução espectral de ~10.7 Hz a 44100 Hz |
| Espectrograma | ~350 colunas | Limitado pela largura do canvas |
| Modelo de filtro (decomposição) | Aproximação | Não replica exatamente o BiquadFilter nativo |

---

## Estrutura do Código

O `index.html` está organizado em seções delimitadas por comentários:

```
<style>
  /* CSS organizado por componente:
     Header, Mode Tabs, Main Layout, Sidebar, Panels,
     Controls, Partials, Viz Area, Decomposition, Responsive */
</style>

<body>
  <!-- HTML: Header → Main Grid (Sidebar | Viz | Decomposition) -->
</body>

<script>
  // STATE — variáveis globais
  // AUDIO — initAudio, rebuildAudioGraph, startSound, stopSound
  // CONTROLS — updateGlobal, updateFilter, updatePartialLive
  // PARTIALS — addPartial, removePartial, renderPartials
  // PRESETS — loadPreset, addPartialSilent
  // MODE — setMode
  // FILTER — getFilterGain
  // DECOMPOSITION — drawDecomposition, hexRGBA
  // LIVE VIZ — drawWaveform, drawSpectrum, drawSpectrogram, drawFilterResponse
  // INIT — setup inicial e loops
</script>
```

---

## Compatibilidade de Navegadores

| Navegador | Versão Mínima | Status |
|---|---|---|
| Chrome / Chromium | 66+ | ✅ Totalmente compatível |
| Firefox | 76+ | ✅ Totalmente compatível |
| Safari | 14.1+ | ✅ Compatível (requer interação do usuário para iniciar áudio) |
| Edge | 79+ | ✅ Totalmente compatível |
| Mobile Chrome | 66+ | ⚠️ Funcional, layout adaptado |
| Mobile Safari | 14.5+ | ⚠️ Funcional, requer toque para áudio |

---

## Como Modificar

### Adicionar Novo Preset

Na função `loadPreset()`, adicione um novo case:

```javascript
case 'meu_preset':
  // Array de [ratio, amplitude, fase]
  [[1, 1, 0], [3, 0.5, 0], [5, 0.25, 90]].forEach(
    ([r, a, p]) => addPartialSilent(r, a, p)
  );
  break;
```

E adicione o botão no HTML:

```html
<button class="preset-btn" onclick="loadPreset('meu_preset')">Meu Preset</button>
```

### Adicionar Novo Tipo de Filtro

1. Adicione a `<option>` no select `#filterType`
2. Adicione o case na função `getFilterGain()`
3. O Web Audio `BiquadFilterNode` suporta: `lowpass`, `highpass`, `bandpass`, `notch`, `allpass`, `lowshelf`, `highshelf`, `peaking`

### Modificar Cores

Todas as cores estão definidas em variáveis CSS no `:root` e no array `COLORS` do JavaScript.

---

<p align="center"><em>NICS/UNICAMP — 2026</em></p>
