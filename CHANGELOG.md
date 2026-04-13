# Changelog

Todas as mudanças relevantes deste projeto serão documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/).

## [1.0.0] — 2026-04-13

### Adicionado

- **Modo Síntese Aditiva** — construção de timbres pela soma de parciais senoidais
- **Modo Síntese Subtrativa** — filtragem de som rico com filtros LP, HP, BP e Notch
- **Visualização em tempo real** — forma de onda, espectro (escala log) e espectrograma
- **Painel de Decomposição de Ondas** — visualização estática individual de cada parcial
  - Onda resultante (soma) com fantasmas dos parciais individuais
  - Onda pós-filtro (modo subtrativo) com comparação antes/depois
- **Envelope ADSR** — controle de Attack, Decay, Sustain e Release
- **6 presets didáticos** — dente-de-serra, quadrada, triangular, sino, órgão, metálico
- **Controle de fase** individual por parcial (0°–360°)
- **Controle de ciclos visíveis** na decomposição (1–8)
- **Paleta de 20 cores** consistente entre sidebar, espectro e decomposição
- **Indicação harmônico/inarmônico** por código de cores (verde/rosa)
- **Atualização em tempo real** de todos os parâmetros durante reprodução
- **Interface responsiva** para desktop e tablets
- **Documentação completa** — README, guia pedagógico, documentação técnica
- **GitHub Pages** — deploy automático via GitHub Actions
