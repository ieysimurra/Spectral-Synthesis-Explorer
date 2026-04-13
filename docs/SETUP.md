# 🚀 Setup Rápido — GitHub + GitHub Pages

Este guia mostra como publicar o Síntese Espectral Explorer no GitHub Pages em 5 minutos.

---

## Passo 1 — Criar o Repositório

1. Acesse [github.com/new](https://github.com/new)
2. Nome do repositório: `sintese-espectral-explorer`
3. Descrição: `Aplicativo interativo para exploração de síntese aditiva e subtrativa — NICS/UNICAMP`
4. Marque **Public**
5. **NÃO** inicialize com README (já temos o nosso)
6. Clique em **Create repository**

## Passo 2 — Enviar os Arquivos

No terminal, na pasta do projeto:

```bash
cd sintese-espectral-explorer

git init
git add .
git commit -m "feat: versão inicial do Síntese Espectral Explorer"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/sintese-espectral-explorer.git
git push -u origin main
```

## Passo 3 — Ativar GitHub Pages

1. No repositório, vá em **Settings** (engrenagem)
2. No menu lateral, clique em **Pages**
3. Em **Source**, selecione **GitHub Actions**
4. O workflow `deploy.yml` já está configurado — ele será executado automaticamente

## Passo 4 — Acessar o Site

Após 1–2 minutos, o site estará disponível em:

```
https://SEU-USUARIO.github.io/sintese-espectral-explorer/
```

Você pode verificar o status do deploy na aba **Actions** do repositório.

## Passo 5 — Personalizar o README

Abra o `README.md` e substitua todas as ocorrências de `SEU-USUARIO` pelo seu nome de usuário do GitHub.

---

## Estrutura de Arquivos

```
sintese-espectral-explorer/
├── index.html                    ← A aplicação (GitHub Pages serve este)
├── README.md                     ← Documentação principal
├── LICENSE                       ← Licença MIT
├── CHANGELOG.md                  ← Histórico de versões
├── .gitignore
├── .github/
│   └── workflows/
│       └── deploy.yml            ← CI/CD automático
└── docs/
    ├── GUIA_PEDAGOGICO.md        ← Roteiros de aula
    ├── TECHNICAL.md              ← Documentação técnica
    ├── CONTRIBUTING.md           ← Guia para contribuidores
    ├── SETUP.md                  ← Este arquivo
    └── images/
        └── logo.svg              ← Logo do projeto
```

## Atualizando o Site

Qualquer push na branch `main` atualiza o site automaticamente:

```bash
# Faça suas edições no index.html
git add .
git commit -m "feat: adicionado novo preset"
git push
```

O GitHub Actions publicará a nova versão em ~1 minuto.

---

## Uso Offline / Em Sala de Aula

Se a internet não estiver disponível no estúdio:

1. Baixe o `index.html` para um pendrive
2. Abra diretamente no navegador do computador
3. Tudo funciona offline (exceto as fontes do Google Fonts, que usarão fallback do sistema)

---

*Dúvidas? Abra uma issue no repositório.*
