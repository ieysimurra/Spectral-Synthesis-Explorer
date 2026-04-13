# 🤝 Guia de Contribuição

Obrigado pelo interesse em contribuir com o Síntese Espectral Explorer!

## Como Contribuir

### Reportando Bugs

1. Verifique se o bug já não foi reportado em [Issues](../../issues)
2. Abra uma nova issue com:
   - Descrição clara do problema
   - Passos para reproduzir
   - Navegador e sistema operacional
   - Captura de tela (se aplicável)

### Sugerindo Melhorias

Abra uma issue com a tag `enhancement` descrevendo:
- O que a melhoria resolve
- Público-alvo (alunos de graduação, pós, etc.)
- Mockup ou exemplo (se possível)

### Enviando Código

1. Faça um fork do repositório
2. Crie uma branch: `git checkout -b minha-feature`
3. Faça suas alterações no `index.html`
4. Teste em pelo menos Chrome e Firefox
5. Commit: `git commit -m "feat: descrição da mudança"`
6. Push: `git push origin minha-feature`
7. Abra um Pull Request

## Convenções

### Commits

Usamos [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` nova funcionalidade
- `fix:` correção de bug
- `docs:` documentação
- `style:` formatação (sem mudança de lógica)
- `refactor:` refatoração
- `perf:` performance

### Código

- O projeto é **arquivo único** (`index.html`) — mantenha essa filosofia
- CSS organizado por componente com comentários delimitadores
- JavaScript com seções claras (STATE, AUDIO, VIZ, etc.)
- Sem dependências externas (exceto Google Fonts)
- Teste com áudio ativo e em diferentes tamanhos de tela

## Áreas Prioritárias

- Acessibilidade (ARIA labels, navegação por teclado)
- Novos presets baseados em instrumentos reais
- Tradução (i18n)
- Testes automatizados de interface
- Exportação de áudio/imagem

## Código de Conduta

Respeite todos os participantes. Contribuições construtivas e respeitosas são sempre bem-vindas.

---

*Dúvidas? Abra uma issue com a tag `question`.*
