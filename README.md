<p align="center">
  <img src="docs/images/logo.svg" alt="Síntese Espectral Explorer" width="80">
</p>

<h1 align="center">🔊 Síntese Espectral Explorer</h1>

<p align="center">
  <strong>Aplicativo interativo para exploração de síntese aditiva e subtrativa</strong><br>
  <em>Ferramenta didática para ensino de acústica musical e síntese sonora</em>
</p>

<p align="center">
  <a href="https://SEU-USUARIO.github.io/sintese-espectral-explorer/">🌐 Demo ao Vivo</a> ·
  <a href="#funcionalidades">✨ Funcionalidades</a> ·
  <a href="#como-usar">📖 Como Usar</a> ·
  <a href="#uso-pedagógico">🎓 Uso Pedagógico</a> ·
  <a href="docs/GUIA_PEDAGOGICO.md">📚 Guia Pedagógico</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="MIT License">
  <img src="https://img.shields.io/badge/plataforma-Web-blue?style=flat-square" alt="Web">
  <img src="https://img.shields.io/badge/dependências-zero-orange?style=flat-square" alt="Zero Dependencies">
  <img src="https://img.shields.io/badge/NICS-UNICAMP-red?style=flat-square" alt="NICS UNICAMP">
</p>

---

## Sobre

O **Síntese Espectral Explorer** é uma aplicação web interativa desenvolvida para o ensino de síntese sonora nas disciplinas de **Criação Musical com Novos Suportes Tecnológicos** e **Acústica Musical** do [NICS/UNICAMP](https://www.nics.unicamp.br/).

A ferramenta permite que estudantes construam e desconstruam timbres em tempo real, visualizando simultaneamente o comportamento temporal e espectral do som. Não requer instalação — funciona diretamente no navegador.

### Por que esta ferramenta?

| Desafio pedagógico | Como o Explorer resolve |
|---|---|
| Conceitos abstratos de Fourier | Visualização imediata da decomposição em parciais |
| Diferença entre harmônicos e inarmônicos | Código de cores e presets comparativos (órgão vs. sino) |
| Relação tempo × frequência | Três visualizações simultâneas + painel de decomposição |
| Síntese subtrativa é "invisível" | Comparação visual antes/depois do filtro |
| Heterogeneidade de níveis | Interface progressiva: do preset ao controle fino |

---

## Funcionalidades

### 🎛️ Dois Modos de Síntese

- **Aditiva (➕)** — Construa timbres somando senoides individuais (parciais). Controle frequência relativa, amplitude e fase de cada componente.
- **Subtrativa (✂️)** — Parta de um som rico em harmônicos e "esculpa" com filtros digitais (LP, HP, BP, Notch), controlando frequência de corte e ressonância Q.

### 📊 Quatro Visualizações Simultâneas

1. **Forma de Onda (tempo)** — Sinal resultante em tempo real via Web Audio API
2. **Espectro (frequência)** — Análise espectral com escala logarítmica e marcação de parciais
3. **Espectrograma** — Representação tempo × frequência × intensidade
4. **Decomposição de Ondas** — Visualização estática de cada parcial individual + onda resultante + pós-filtro (subtrativa)

### 🎨 Presets Didáticos

| Preset | Tipo | Uso pedagógico |
|---|---|---|
| **Dente-de-serra** | Harmônico | Todos os harmônicos (1/n). Base para subtrativa |
| **Quadrada** | Harmônico | Apenas ímpares. Comparar com serra |
| **Triangular** | Harmônico | Ímpares com decaimento 1/n². Timbre suave |
| **Sino** | Inarmônico | Razões não-inteiras. Espectro de percussão |
| **Órgão** | Harmônico | Registros de órgão. Série harmônica seletiva |
| **Metálico** | Inarmônico | Razões √2. Timbres de placas e barras |

### 🔧 Controles Completos

- **Frequência fundamental** (30–2000 Hz) com atualização em tempo real
- **Envelope ADSR** (Attack, Decay, Sustain, Release)
- **Fase individual** por parcial (0°–360°)
- **Filtro** com 4 tipos, frequência de corte e ressonância Q
- **Ciclos visíveis** para zoom temporal na decomposição
- Até 20 parciais simultâneos

---

## Como Usar

### Acesso Online (GitHub Pages)

Basta acessar:

```
https://SEU-USUARIO.github.io/sintese-espectral-explorer/
```

Nenhuma instalação necessária. Funciona em qualquer navegador moderno (Chrome, Firefox, Safari, Edge).

### Execução Local

```bash
# Clone o repositório
git clone https://github.com/SEU-USUARIO/sintese-espectral-explorer.git

# Acesse a pasta
cd sintese-espectral-explorer

# Abra diretamente no navegador
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows

# OU sirva com servidor local (opcional)
python3 -m http.server 8000
# Acesse http://localhost:8000
```

### Requisitos

- Navegador com suporte a **Web Audio API** (todos os modernos)
- Saída de áudio (fones de ouvido recomendados para aulas)
- Tela com largura mínima de 900px para experiência completa (responsivo para mobile)

---

## Uso Pedagógico

### 🎓 Roteiros de Aula Sugeridos

#### Aula 1 — Introdução à Série Harmônica (45 min)

1. Abra o Explorer com apenas o parcial fundamental (P1)
2. Adicione o 2º harmônico — ouça a oitava, veja no espectro
3. Adicione 3º, 4º, 5º — discuta intervalos musicais
4. Carregue preset "Dente-de-serra" — compare com construção manual
5. **Exercício:** Reproduzir o timbre de "Quadrada" manualmente

#### Aula 2 — Parciais Inarmônicos (45 min)

1. Carregue preset "Sino" — observe razões não-inteiras
2. Mude F₀ — discuta por que sinos não têm "nota" clara
3. Carregue "Metálico" — compare com "Órgão"
4. **Exercício:** Criar timbre de "gongo" com parciais inarmônicos

#### Aula 3 — Síntese Subtrativa (45 min)

1. Mude para modo Subtrativo com preset "Dente-de-serra"
2. Aplique filtro passa-baixa, varie o corte lentamente
3. Observe decomposição: antes vs. depois do filtro
4. Experimente ressonância Q alta — discuta picos
5. **Exercício:** Simular um "wah-wah" variando o corte

#### Aula 4 — Fase e Forma de Onda (30 min)

1. Crie 3 harmônicos com mesma amplitude
2. Mude a fase do 2º parcial de 0° a 180°
3. Observe mudança na forma de onda, mas NÃO no espectro
4. Discuta: por que nosso ouvido é (quase) insensível à fase?

> 📚 Roteiros completos com objetivos, materiais e avaliação disponíveis no [Guia Pedagógico](docs/GUIA_PEDAGOGICO.md).

---

## Arquitetura Técnica

### Tecnologias

| Componente | Tecnologia |
|---|---|
| Áudio | Web Audio API (OscillatorNode, BiquadFilterNode, AnalyserNode) |
| Visualização | Canvas 2D com requestAnimationFrame |
| Interface | HTML/CSS puro (sem frameworks) |
| Fontes | DM Sans + Space Mono (Google Fonts) |
| Deploy | GitHub Pages (arquivo único) |

### Estrutura do Projeto

```
sintese-espectral-explorer/
├── index.html              # Aplicação completa (arquivo único)
├── README.md               # Esta documentação
├── LICENSE                  # Licença MIT
├── CHANGELOG.md            # Histórico de versões
├── .github/
│   └── workflows/
│       └── deploy.yml      # CI/CD para GitHub Pages
└── docs/
    ├── GUIA_PEDAGOGICO.md  # Roteiros de aula detalhados
    ├── TECHNICAL.md        # Documentação técnica detalhada
    ├── CONTRIBUTING.md     # Guia para contribuições
    └── images/
        └── logo.svg        # Logo do projeto
```

### Diagrama de Áudio

```
                    ┌─────────────┐
                    │ Oscilador 1 │──► Gain 1 ─┐
                    └─────────────┘             │
                    ┌─────────────┐             │    ┌────────────┐
                    │ Oscilador 2 │──► Gain 2 ──┼──► │ Master Gain│
                    └─────────────┘             │    └─────┬──────┘
                    ┌─────────────┐             │          │
                    │ Oscilador N │──► Gain N ──┘          │
                    └─────────────┘                        │
                                                           ▼
                                              ┌──── Modo Aditivo? ────┐
                                              │ SIM                NÃO│
                                              ▼                       ▼
                                         ┌─────────┐          ┌────────────┐
                                         │ Analyser │          │   Filtro   │
                                         └────┬────┘          │ Biquad     │
                                              │               └─────┬──────┘
                                              │                     ▼
                                              │               ┌─────────┐
                                              │               │ Analyser │
                                              │               └────┬────┘
                                              ▼                    ▼
                                         ┌──────────────────────────────┐
                                         │     AudioContext.destination  │
                                         │          (alto-falantes)      │
                                         └──────────────────────────────┘
```

### Decomposição Estática — Como Funciona

O painel de decomposição calcula matematicamente cada forma de onda usando:

```
y(t) = A × sin(2π × f₀ × ratio × t + φ)
```

A onda resultante é a soma de todos os parciais:

```
Y(t) = Σ Aᵢ × sin(2π × f₀ × ratioᵢ × t + φᵢ)
```

No modo subtrativo, cada parcial é multiplicado pelo ganho do filtro na sua frequência:

```
Y_filtrado(t) = Σ Aᵢ × G(f₀ × ratioᵢ) × sin(2π × f₀ × ratioᵢ × t + φᵢ)
```

---

## Configuração do GitHub Pages

### Opção 1 — Deploy Automático (Recomendado)

O repositório inclui um workflow GitHub Actions em `.github/workflows/deploy.yml` que publica automaticamente a cada push na branch `main`.

1. Vá em **Settings → Pages** no seu repositório
2. Em **Source**, selecione **GitHub Actions**
3. Faça push — o site será publicado automaticamente

### Opção 2 — Deploy Manual

1. Vá em **Settings → Pages**
2. Em **Source**, selecione **Deploy from a branch**
3. Escolha a branch `main` e pasta `/ (root)`
4. Salve — o site estará disponível em ~1 minuto

---

## Contribuindo

Contribuições são bem-vindas! Veja o [guia de contribuição](docs/CONTRIBUTING.md) para detalhes.

### Ideias para Contribuição

- [ ] Modo de modulação AM/FM
- [ ] Exportação de áudio (WAV)
- [ ] Teclado MIDI virtual
- [ ] Mais presets (clarinete, flauta, piano)
- [ ] Modo de gravação/comparação de timbres
- [ ] Tradução para inglês/espanhol
- [ ] Acessibilidade (screen reader, alto contraste)

---

## Licença

Este projeto é licenciado sob a [MIT License](LICENSE).

Desenvolvido para o **NICS — Núcleo Interdisciplinar de Comunicação Sonora**<br>
**UNICAMP — Universidade Estadual de Campinas**

---

<p align="center">
  <strong>Prof. Ivan Simurra</strong> · NICS/UNICAMP · 2026<br>
  <em>Criação Musical com Novos Suportes Tecnológicos</em>
</p>
