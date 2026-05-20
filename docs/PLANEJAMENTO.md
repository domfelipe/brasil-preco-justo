# 📋 Documento de Planejamento — Brasil Preço Justo

## 1. Visão do Produto

**Brasil Preço Justo** é um dashboard fintech que democratiza o acesso à informação econômica no Brasil. Resolve a dor da população de não conseguir visualizar, de forma simples e intuitiva, como a inflação e os preços da cesta básica impactam seu poder de compra real.

### Público-alvo
- Classe média e trabalhadora (renda entre 1-10 salários mínimos)
- Estudantes de economia e ciências sociais
- Jornalistas e pesquisadores
- Qualquer cidadão preocupado com o poder aquisitivo

## 2. Requisitos Funcionais

### RF-001: Dashboard de KPIs
- Exibir IPCA acumulado 12 meses
- Exibir cotação do Dólar comercial
- Exibir taxa Selic meta
- Exibir valor da cesta básica em São Paulo

### RF-002: Gráfico Histórico
- Linha temporal de 24 meses
- Alternância entre IPCA, IGP-M e Dólar
- Tooltips interativos
- Animação de carregamento

### RF-003: Cesta Básica
- 8 itens essenciais com preço médio
- Indicador de variação percentual (12 meses)
- Alerta visual quando variação > 20%

### RF-004: Calculadora de Poder de Compra
- Input de salário mensal
- Seleção de dependentes (1-4+)
- Seleção de ano de referência (2020-2024)
- Cálculo de % da renda consumida pela cesta
- Cálculo de poder de compra vs ano selecionado
- Cálculo de salário necessário para manter poder aquisitivo

### RF-005: Simulador de Perda Salarial
- Visualização gráfica (barras) de salário nominal vs real
- Projeção de 5 anos com inflação acumulada
- Atualização dinâmica baseada na calculadora

## 3. Requisitos Não-Funcionais

### RNF-001: Performance
- First Contentful Paint < 1.5s
- Time to Interactive < 3s
- Bundle size < 100KB (excluindo CDN)

### RNF-002: Design
- Dark theme premium (preto, cinza escuro, roxo/violeta)
- Glassmorphism nos cards
- Animações sutis (fade-in, hover, contadores)
- Totalmente responsivo (mobile-first)

### RNF-003: Confiabilidade
- Fallback para dados mockados quando APIs falharem
- Indicador visual de status da API
- Dados sempre atualizados quando online

### RNF-004: Segurança
- Zero persistência de dados pessoais
- Sanitização de inputs
- HTTPS-only
- Sem cookies de rastreamento

## 4. Arquitetura Técnica

### Stack
- **Frontend**: HTML5, Tailwind CSS (CDN), Vanilla JS
- **Gráficos**: Chart.js (CDN)
- **Ícones**: SVG inline (sem dependência externa)
- **Fonte**: Inter (Google Fonts)
- **Deploy**: GitHub Pages via GitHub Actions

### Estrutura de Dados
```javascript
// IPCA/IGP-M/Dólar
{ data: "MM/YYYY", valor: float }

// Itens da cesta
{ nome: string, preco: float, variacao: float, icone: string }

// Configurações
{ cestaBasicaAtual, cestaBasicaAnterior, salarioMinimo, ... }
```

### APIs
1. Banco Central (IPCA, IGP-M, Selic) — JSON via CORS
2. AwesomeAPI (Dólar) — JSON via CORS
3. Fallback: dados mockados realistas

## 5. Fluxo de Dados

```
Usuário → Carrega página → JS tenta fetch APIs
    ├── Sucesso → Exibe dados reais + badge "Live"
    └── Falha → Exibe dados mock + badge "Demo"

Usuário → Interage com calculadora → Cálculo client-side
    └── Resultado exibido instantaneamente (zero latência)
```

## 6. Roadmap

### v1.0 (Atual)
- Dashboard com KPIs e gráficos
- Calculadora de poder de compra
- Simulador de perda salarial
- Deploy GitHub Pages

### v1.1 (Futuro)
- Geolocalização para cesta básica regional
- Alertas por e-mail/SMS quando inflação subir
- Modo offline completo (Service Worker)
- Comparador entre cidades

### v1.2 (Futuro)
- Backend Node.js para cache de APIs
- Autenticação para salvar simulações
- API própria REST
- App PWA instalável

## 7. Métricas de Sucesso

- Tempo médio na página > 2 minutos
- Taxa de interação com calculadora > 40%
- Score Lighthouse > 90 em todas as categorias
- 0 vulnerabilidades críticas no RED TEAM
