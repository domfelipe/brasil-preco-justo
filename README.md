# 🇧🇷 Brasil Preço Justo

> Dashboard interativo de monitoramento de inflação, cesta básica e poder de compra no Brasil.

![Version](https://img.shields.io/badge/version-1.0.0-purple)
![License](https://img.shields.io/badge/license-MIT-blue)
![Status](https://img.shields.io/badge/status-stable-green)

## ✨ Funcionalidades

- **📊 KPIs em tempo real**: IPCA acumulado 12M, Dólar, Selic e Cesta Básica SP
- **📈 Gráficos interativos**: Evolução histórica de IPCA, IGP-M e Dólar (24 meses)
- **🛒 Cesta Básica**: Cards dos 8 itens essenciais com variação de preço
- **🧮 Calculadora de Poder de Compra**: Simule quanto da sua renda é consumida pela cesta
- **💸 Simulador de Perda**: Visualize como a inflação erode seu salário ao longo dos anos
- **🎨 Design premium**: Dark theme fintech com glassmorphism e animações refinadas

## 🚀 Deploy

Este projeto utiliza **GitHub Actions** para deploy automático no GitHub Pages.

### Passo a passo:

1. Crie um novo repositório no GitHub
2. Faça upload destes arquivos para a branch `main`
3. Acesse **Settings → Pages** e selecione a fonte "GitHub Actions"
4. O workflow será executado automaticamente. Acesse a aba **Actions** para acompanhar
5. Seu site estará disponível em `https://seuusuario.github.io/nome-do-repo`

### Deploy manual (alternativo):

```bash
git init
git add .
git commit -m "Primeiro commit - Brasil Preço Justo v1.0"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/nome-do-repo.git
git push -u origin main
```

## 🏗️ Arquitetura

```
brasil-preco-justo/
├── index.html              # Aplicação SPA completa
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions para deploy
├── docs/
│   ├── PLANEJAMENTO.md     # Documento de planejamento
│   ├── REDTEAM.md          # Validação de segurança
│   └── QA.md               # Checklist de qualidade
└── README.md               # Este arquivo
```

## 🔌 APIs Utilizadas

| Fonte | Endpoint | Dado |
|-------|----------|------|
| ANP | `gov.br/anp/.../serie-historica-de-precos-de-combustiveis` | Gasolina, alcool e diesel |
| IBGE SIDRA | `servicodados.ibge.gov.br/api/v3/agregados/7061` | Variacao de aluguel residencial |
| Banco Central | `api.bcb.gov.br/dados/serie/bcdata.sgs.433` | IPCA mensal |
| Banco Central | `api.bcb.gov.br/dados/serie/bcdata.sgs.189` | IGP-M |
| Banco Central | `api.bcb.gov.br/dados/serie/bcdata.sgs.432` | Selic |
| AwesomeAPI | `economia.awesomeapi.com.br/json/last/USD-BRL` | Dólar comercial |

> ⚠️ **Fallback**: Quando APIs estão indisponíveis (CORS, timeout, manutenção), o sistema utiliza dados mockados realistas para manter a experiência funcional. Um indicador visual mostra se os dados são "em tempo real" ou "de demonstração".

## 🛡️ Segurança (RED TEAM)

Consulte [docs/REDTEAM.md](docs/REDTEAM.md) para o relatório completo de validação de segurança.

Pontos principais:
- ✅ Zero dados pessoais coletados
- ✅ Cálculos 100% client-side
- ✅ Sem cookies de rastreamento
- ✅ Sanitização de inputs
- ✅ CSP-ready (Content Security Policy)
- ✅ HTTPS-only via GitHub Pages

## 🧪 QA / Testes

Consulte [docs/QA.md](docs/QA.md) para o checklist completo de qualidade.

| Categoria | Status |
|-----------|--------|
| Responsividade | ✅ Mobile, Tablet, Desktop |
| Performance | ✅ Lighthouse > 90 |
| Acessibilidade | ✅ Contraste WCAG AA, navegação por teclado |
| Cross-browser | ✅ Chrome, Firefox, Safari, Edge |
| Offline | ⚠️ Parcial (dados mock funcionam) |

## 📄 Licença

MIT License — livre para uso, modificação e distribuição.

---

**Feito com 💜 para a população brasileira.**
