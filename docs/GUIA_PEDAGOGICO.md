# 📚 Guia Pedagógico — Síntese Espectral Explorer

> Roteiros de aula detalhados para uso do aplicativo em disciplinas de graduação e pós-graduação.

---

## Sumário

1. [Contextualização Curricular](#1-contextualização-curricular)
2. [Roteiro 1 — Série Harmônica e Timbre](#2-roteiro-1--série-harmônica-e-timbre)
3. [Roteiro 2 — Parciais Inarmônicos](#3-roteiro-2--parciais-inarmônicos)
4. [Roteiro 3 — Síntese Subtrativa](#4-roteiro-3--síntese-subtrativa)
5. [Roteiro 4 — Fase e Percepção](#5-roteiro-4--fase-e-percepção)
6. [Roteiro 5 — Envelope e Dinâmica Espectral](#6-roteiro-5--envelope-e-dinâmica-espectral)
7. [Exercícios Propostos](#7-exercícios-propostos)
8. [Critérios de Avaliação](#8-critérios-de-avaliação)
9. [Repertório Complementar](#9-repertório-complementar)
10. [Referências Bibliográficas](#10-referências-bibliográficas)

---

## 1. Contextualização Curricular

### Disciplinas Alvo

| Disciplina | Semestre | Conteúdo relacionado |
|---|---|---|
| Criação Musical com Novos Suportes Tecnológicos | Sem. 2 | Síntese sonora (AM, FM, RM, aditiva, subtrativa, granular) |
| Criação Musical com Novos Suportes Tecnológicos | Sem. 3 | Processamento espectral, análise/ressíntese |
| Acústica Musical | Qualquer | Série harmônica, timbre, sistema auditivo |
| Composição I–IV | Avançado | Integração tecnológica, escrita para eletrônica |

### Pré-requisitos dos Alunos

- Nenhum conhecimento prévio de programação
- Conceito básico de frequência e amplitude
- Acesso a navegador web com saída de áudio

### Alinhamento com Objetivos de Aprendizagem

O Explorer atende os seguintes objetivos:

- **Compreender** a decomposição de Fourier de forma intuitiva
- **Relacionar** parâmetros acústicos (frequência, amplitude, fase) com percepção (altura, intensidade, timbre)
- **Distinguir** espectros harmônicos de inarmônicos e suas implicações tímbricas
- **Aplicar** conceitos de filtragem para modelagem de timbre
- **Analisar** relações entre domínio temporal e frequencial

---

## 2. Roteiro 1 — Série Harmônica e Timbre

**Duração:** 1h30 (1 bloco prático)
**Modo:** Síntese Aditiva

### Objetivos

1. Compreender a série harmônica como base do timbre
2. Relacionar número e intensidade de harmônicos com qualidade tímbrica
3. Identificar auditivamente a adição progressiva de parciais

### Preparação

- Projetar o Explorer na tela do estúdio
- Alunos com notebooks individuais acessando a URL do GitHub Pages
- Fones de ouvido para cada aluno

### Desenvolvimento

#### Parte 1 — Construção Progressiva (30 min)

1. **Abra o Explorer** com todos os parciais removidos (preset "Limpar")
2. **Adicione apenas P1** (fundamental, 220 Hz)
   - Reproduza → "O que vocês ouvem?"
   - Mostre a forma de onda (senoide pura) e o espectro (uma única linha)
3. **Adicione P2** (2×, amplitude 0.5)
   - "O que mudou? A altura mudou ou o timbre?"
   - Observe no painel de decomposição: duas senoides → resultante
4. **Adicione P3, P4, P5** progressivamente
   - A cada adição, pause para ouvir e observar
   - Destaque no espectro como as linhas se acumulam
5. **Pergunte:** "Quantos harmônicos precisamos para que soe 'natural'?"

#### Parte 2 — Comparação de Formas de Onda (30 min)

1. **Carregue preset "Dente-de-serra"**
   - Analise o espectro: todos os harmônicos, decaimento 1/n
   - Observe a forma de onda característica no painel de decomposição
2. **Carregue preset "Quadrada"**
   - Compare: apenas harmônicos ímpares
   - "Por que o timbre é diferente se a fundamental é a mesma?"
3. **Carregue preset "Triangular"**
   - Decaimento mais rápido (1/n²)
   - "Por que soa mais suave que a quadrada?"

#### Parte 3 — Exercício Guiado (30 min)

- **Tarefa:** Sem usar presets, construir manualmente uma aproximação de onda quadrada
- **Critério:** Usar pelo menos 5 harmônicos ímpares com amplitudes corretas
- **Discussão:** Comparar resultados entre alunos

### Avaliação Formativa

- Captura de tela do Explorer mostrando a construção manual
- Resposta escrita: "Explique com suas palavras por que um instrumento com mais harmônicos soa mais 'brilhante'"

---

## 3. Roteiro 2 — Parciais Inarmônicos

**Duração:** 1h30
**Modo:** Síntese Aditiva

### Objetivos

1. Distinguir espectros harmônicos de inarmônicos
2. Relacionar inarmonicidade com classes de instrumentos (percussão, metais)
3. Compreender por que sinos não têm "nota" definida

### Desenvolvimento

#### Parte 1 — Harmônico vs. Inarmônico (30 min)

1. Carregue preset "Órgão" → ouça, observe
2. Carregue preset "Sino" → ouça, compare
3. **Ponto-chave:** No "Sino", os ratios são 1, 2.76, 5.4, 8.93, 13.34
   - "Estes números não são inteiros — o que isso significa?"
   - Mostre no painel de decomposição: as ondas não se repetem sincronicamente
4. Mude a F₀ do sino entre 200 Hz e 800 Hz
   - "Por que é difícil identificar a 'nota' de um sino?"

#### Parte 2 — Construindo Timbres Inarmônicos (30 min)

1. Limpe todos os parciais
2. Adicione P1 (1×), P2 (1.41×), P3 (2.0×), P4 (2.83×)
   - Razões baseadas em √2 → "Série metálica"
3. Compare com P1 (1×), P2 (2×), P3 (3×), P4 (4×)
   - Mesma quantidade de parciais, razões diferentes
4. **Discussão:** "Qual soa mais 'musical'? Por quê?"

#### Parte 3 — Exercício (30 min)

- **Tarefa:** Criar dois timbres contrastantes:
  1. Um timbre "vocal" (harmônico, 5+ parciais)
  2. Um timbre "percussivo" (inarmônico, razões fracionárias)
- Documentar os parâmetros usados

### Repertório de Escuta

- **Jonathan Harvey** — *Mortuos Plango, Vivos Voco* (análise espectral de sino)
- **Jean-Claude Risset** — *Mutations* (síntese aditiva com parciais inarmônicos)
- **Kaija Saariaho** — *Noa Noa* (espectro harmônico/inarmônico em flauta + eletrônica)

---

## 4. Roteiro 3 — Síntese Subtrativa

**Duração:** 1h30
**Modo:** Síntese Subtrativa

### Objetivos

1. Compreender o princípio da síntese subtrativa
2. Identificar auditivamente os efeitos de diferentes tipos de filtro
3. Relacionar frequência de corte e ressonância com qualidade tímbrica

### Desenvolvimento

#### Parte 1 — O Princípio (20 min)

1. Mude para modo **Subtrativo**
2. O preset "Dente-de-serra" carrega automaticamente
3. **Metáfora:** "É como um escultor: começamos com um bloco rico em material (todos os harmônicos) e removemos o que não queremos"
4. Observe no painel de decomposição: a onda completa (resultante) antes de qualquer filtro

#### Parte 2 — Tipos de Filtro (40 min)

**Passa-Baixa (LP):**
1. Comece com corte em 4000 Hz → abaixe lentamente até 200 Hz
2. "O que acontece com o brilho? Por quê?"
3. Observe no painel pós-filtro: a onda fica mais suave (menos harmônicos agudos)
4. Compare a decomposição antes/depois

**Passa-Alta (HP):**
1. Mude o filtro para HP, corte em 200 Hz → suba até 2000 Hz
2. "O que acontece com o corpo do som?"
3. O som fica "fino", "nasal"

**Passa-Banda (BP):**
1. Mude para BP, experimente diferentes posições de corte
2. "Simula o que acontece quando vocalizamos vogais"
3. Compare: corte em 300 Hz (som de "u") vs. 2000 Hz (som de "i")

**Ressonância Q:**
1. Com LP em 1000 Hz, aumente Q de 1 para 15
2. "Ouvem o pico? Isso é ressonância"
3. Discuta: o filtro não apenas remove, ele pode enfatizar

#### Parte 3 — Exercício (30 min)

- **Tarefa:** Usando modo subtrativo, simular três sons:
  1. Um som "abafado" (LP com corte baixo)
  2. Um som "telefone" (BP estreito em ~1kHz)
  3. Um som com "wah-wah" (variar corte do LP manualmente)
- Observar as diferenças no painel de decomposição pós-filtro

---

## 5. Roteiro 4 — Fase e Percepção

**Duração:** 45 min
**Modo:** Síntese Aditiva

### Objetivos

1. Compreender o papel da fase na forma de onda
2. Demonstrar a (quase) insensibilidade auditiva à fase
3. Relacionar teorema de Ohm acústico com o Explorer

### Desenvolvimento

1. Crie 3 harmônicos: P1 (1×, amp 1.0), P2 (2×, amp 0.5), P3 (3×, amp 0.33)
2. Todas as fases em 0° → observe forma de onda e ouça
3. Mude a fase de P2 para 90° → "A forma de onda mudou. O som mudou?"
4. Mude para 180° → forma de onda completamente diferente. "E o som?"
5. **Ponto-chave:** O espectro (amplitudes) não muda — apenas a forma de onda
6. Varie a fase de P3 entre 0° e 360° observando o painel de decomposição
7. **Discussão:** "O ouvido faz análise de Fourier — decompõe em frequências, não em forma de onda"

### Nota Didática

> A insensibilidade à fase é uma simplificação útil. Na prática, diferenças de fase podem ser percebidas em certas condições (transientes, sons complexos). Para o nível introdutório, a demonstração é válida.

---

## 6. Roteiro 5 — Envelope e Dinâmica Espectral

**Duração:** 45 min
**Modo:** Ambos

### Objetivos

1. Compreender o papel do envelope temporal no timbre
2. Relacionar ADSR com classes de instrumentos

### Desenvolvimento

1. Carregue preset "Órgão" — envelope padrão (A=50ms, D=150ms, S=70%, R=300ms)
2. Mude para A=5ms, D=1500ms, S=10%, R=2000ms → "Reconhecem? É um piano/sino"
3. Mude para A=500ms, D=100ms, S=90%, R=100ms → "E agora? É um som de cordas/pad"
4. **Exercício:** Carregar preset "Sino" e ajustar envelope para soar como:
   - Um sino de igreja (R longo)
   - Um xilofone (D curto, S baixo)
   - Um pad sintético (A longo, S alto)

---

## 7. Exercícios Propostos

### Nível Básico

1. **Identificação Auditiva:** Ouça os 6 presets com olhos fechados. Ordene do mais "suave" ao mais "áspero". Justifique usando conceitos de parciais.

2. **Construção Manual:** Sem usar presets, construa uma aproximação de onda dente-de-serra com 8 harmônicos. Capture a tela do painel de decomposição.

3. **Filtro Exploratório:** No modo subtrativo, descreva com suas palavras o efeito de cada tipo de filtro sobre o timbre.

### Nível Intermediário

4. **Análise Comparativa:** Compare os presets "Sino" e "Metálico". Ambos são inarmônicos. Quais as diferenças nos ratios? Como isso afeta o timbre?

5. **Síntese Dirigida:** Crie um timbre que soe como um clarinete (dica: predominância de harmônicos ímpares, F₀ por volta de 250 Hz, filtro LP suave).

6. **Fase vs. Espectro:** Crie um timbre com 4 harmônicos. Grave (ou descreva) o som com todas as fases em 0°. Depois mude as fases aleatoriamente. Discuta se houve mudança perceptível.

### Nível Avançado

7. **Ressíntese Conceitual:** Escolha um instrumento acústico. Pesquise seu espectro na literatura. Tente recriá-lo no Explorer ajustando parciais e envelope. Documente o processo.

8. **Modelagem Subtrativa:** Usando modo subtrativo, simule a articulação de três vogais (a, i, u) posicionando o filtro passa-banda em frequências formânticas apropriadas.

9. **Projeto Criativo:** Crie uma sequência de 4 timbres contrastantes que poderiam ser usados numa composição eletroacústica. Para cada um, documente os parâmetros e justifique as escolhas estéticas.

---

## 8. Critérios de Avaliação

### Exercícios Práticos (Rubrica)

| Critério | Insuficiente (0-4) | Satisfatório (5-7) | Excelente (8-10) |
|---|---|---|---|
| **Domínio técnico** | Não consegue usar os controles | Usa controles básicos | Usa todos os parâmetros com fluência |
| **Compreensão conceitual** | Não relaciona parâmetros com resultado sonoro | Relaciona parcialmente | Explica com precisão a relação causa-efeito |
| **Documentação** | Sem registro | Registro incompleto | Parâmetros documentados, capturas de tela, reflexão |
| **Criatividade** | Apenas reproduz presets | Modifica presets | Cria timbres originais com justificativa |

### Projeto Final (sugestão de peso)

- Criação de 3 timbres originais com documentação: **40%**
- Memorial descritivo do processo: **30%**
- Apresentação oral com demonstração ao vivo: **30%**

---

## 9. Repertório Complementar

### Síntese Aditiva

| Obra | Compositor | Ano | Relevância |
|---|---|---|---|
| *Mutations* | Jean-Claude Risset | 1969 | Pioneiro da síntese aditiva computacional |
| *Stria* | John Chowning | 1977 | Uso de razões áureas nos parciais |
| *Mortuos Plango, Vivos Voco* | Jonathan Harvey | 1980 | Análise/ressíntese espectral de sino |
| *Désintégrations* | Tristan Murail | 1982 | Espectralismo e síntese |
| *Partiels* | Gérard Grisey | 1975 | Composição baseada em espectro |

### Síntese Subtrativa

| Obra | Compositor/Artista | Ano | Relevância |
|---|---|---|---|
| *Switched-On Bach* | Wendy Carlos | 1968 | Moog — subtrativa clássica |
| *Oxygène* | Jean-Michel Jarre | 1976 | Síntese analógica subtrativa |
| *Kontakte* | Karlheinz Stockhausen | 1960 | Filtragem como composição |

### Compositores Brasileiros

| Obra | Compositor | Relevância |
|---|---|---|
| *Abertura* | Jorge Antunes | Pioneiro da música eletroacústica brasileira |
| Obras eletroacústicas | Rodolfo Caesar | Processamento espectral |
| Obras mistas | Silvio Ferraz | Integração acústico/eletrônico |
| Obras com live electronics | Mikhail Malt | Síntese e processamento em tempo real |

---

## 10. Referências Bibliográficas

### Acústica e Psicoacústica

- HENRIQUE, L. L. *Acústica Musical*. Lisboa: Fundação Calouste Gulbenkian. — Referência principal da disciplina.
- ROEDERER, J. G. *Introdução à Física e Psicofísica da Música*. São Paulo: EDUSP.
- ROADS, C. *The Computer Music Tutorial*. Cambridge: MIT Press, 1996.

### Síntese Sonora

- DODGE, C.; JERSE, T. A. *Computer Music: Synthesis, Composition, and Performance*. 2nd ed. Cengage, 1997.
- RUSS, M. *Sound Synthesis and Sampling*. 3rd ed. Focal Press, 2008.
- SMITH, J. O. *Spectral Audio Signal Processing*. Disponível online: https://ccrma.stanford.edu/~jos/sasp/

### Composição Espectral

- FINEBERG, J. "Spectral Music." *Contemporary Music Review*, v. 19, n. 2, 2000.
- MURAIL, T. "Target Practice." *Contemporary Music Review*, v. 24, n. 2-3, 2005.

---

<p align="center"><em>Documento elaborado para as disciplinas do NICS/UNICAMP — Prof. Ivan Simurra, 2026.</em></p>
