# SauceDemo Automation - Playwright

[![Playwright CI](https://github.com/rfslusarz/saucedemo-automation-playwright/actions/workflows/playwright.yml/badge.svg)](https://github.com/rfslusarz/saucedemo-automation-playwright/actions/workflows/playwright.yml)
[![Relatório Allure](https://img.shields.io/badge/Allure-Relatório-yellow?style=flat-square)](https://rfslusarz.github.io/saucedemo-automation-playwright/)
[![Playwright](https://img.shields.io/badge/Playwright-1.40+-45ba4b?style=flat-square&logo=Playwright&logoColor=white)](https://playwright.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat-square&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI/CD-2088FF?style=flat-square&logo=github-actions&logoColor=white)](https://github.com/features/actions)
[![ESLint](https://img.shields.io/badge/ESLint-8.0+-4B32C3?style=flat-square&logo=eslint&logoColor=white)](https://eslint.org/)
[![Licença: ISC](https://img.shields.io/badge/Licença-ISC-yellow?style=flat-square)](https://opensource.org/licenses/ISC)

## Relatório Público (GitHub Pages)
- **URL:** [https://rfslusarz.github.io/saucedemo-automation-playwright/](https://rfslusarz.github.io/saucedemo-automation-playwright/)
- **Conteúdo:** Visão geral, suites, cenários, evidências, timeline e métricas de duração

## Demonstrações
- [Allure Report (GitHub Pages)](https://rfslusarz.github.io/saucedemo-automation-playwright/) - Relatório completo com suites, timeline e evidências
- [GitHub Actions](https://github.com/rfslusarz/saucedemo-automation-playwright/actions) - Pipeline CI/CD com execução automatizada

## Visão Geral do Projeto
- Automação E2E com Playwright cobrindo login, catálogo, carrinho e checkout
- Arquitetura em Page Object Model para manutenibilidade
- Custom Test Fixtures para injeção de dependência
- Relatórios Allure com evidências e métricas
- Pipeline CI/CD no GitHub Actions com execução headless
- Suporte multi-browser (Chromium, Firefox, WebKit)

## Tecnologias
- **Playwright** para automação E2E multi-browser
- **TypeScript** para tipagem estática e segurança
- **Page Object Model (POM)** para organização do código
- **Custom Fixtures** para injeção de dependência
- **Allure Reports** para relatórios detalhados
- **GitHub Actions** para CI/CD
- **ESLint + Prettier** para qualidade de código

## Estrutura do Projeto

```
.
├── .github/
│   └── workflows/
│       └── playwright.yml          # Pipeline CI/CD
├── fixtures/
│   ├── fixtures.ts                 # Custom fixtures
│   ├── test-data.ts                # Dados de teste
│   └── users.json                  # Credenciais
├── pages/
│   ├── LoginPage.ts
│   ├── InventoryPage.ts
│   ├── CartPage.ts
│   └── CheckoutPage.ts
├── tests/
│   ├── login.spec.ts
│   ├── checkout.e2e.spec.ts
│   ├── global-setup.ts
│   └── global-teardown.ts
├── utils/
├── playwright.config.ts
└── package.json
```

## Critérios de Qualidade e Objetivos dos Testes
- **Sucesso:** Usuário consegue autenticar, adicionar produtos, revisar resumo e finalizar compra
- **Falha:** Mensagens de erro apropriadas em credenciais inválidas, campos obrigatórios ausentes e fluxos não permitidos
- **Cobertura:** Happy paths e unhappy paths do login, carrinho e checkout
- **Objetivo:** Validar o fluxo crítico de compra com evidências (Allure), garantindo rápida detecção de regressões em CI

## Custom Fixtures
- **Local:** `fixtures/fixtures.ts`
- **Benefício:** Elimina código repetitivo de instanciação de Page Objects
- **Uso:** Injeção automática de dependências nos testes

**Exemplo:**
```typescript
// Com Fixtures (código limpo)
test('deve fazer login', async ({ loginPage }) => {
  await loginPage.navigate();
  await loginPage.login('usuario', 'senha');
});
```

## Pré-requisitos
- Node.js 18+
- npm

## Instalação

1. Clone o repositório
2. Instale as dependências:

```bash
npm install
```

3. Instale os navegadores do Playwright:

```bash
npx playwright install --with-deps
```

## Execução dos Testes

### Execução Local

- **Modo interativo (UI Mode):**
```bash
npm run test:ui
```

- **Modo headless:**
```bash
npm test
```

- **Modo headed:**
```bash
npm run test:headed
```

- **Modo debug:**
```bash
npm run test:debug
```

- **Testes específicos:**
```bash
npm run test:login
npm run test:checkout
```

### Navegadores Específicos

```bash
npx playwright test --project=chromium
npx playwright test --project=firefox
npx playwright test --project=webkit
```

## Relatórios Allure

```bash
# Gerar relatório
npm run allure:generate

# Abrir relatório
npm run allure:open

# Gerar e servir
npm run allure:serve
```

## Qualidade de Código

```bash
# Verificar linting
npm run lint

# Corrigir automaticamente
npm run lint:fix
```

## CI/CD (GitHub Actions)

O projeto está integrado com GitHub Actions para execução automatizada e publicação de relatórios.

### Pipeline Automatizado

**Gatilhos:**
- Push nas branches `main` ou `develop`
- Pull Requests para `main` ou `develop`

**Etapas do Pipeline:**
1. Checkout do código
2. Setup Node.js 18
3. Instalação de dependências
4. Instalação dos navegadores Playwright
5. Execução dos testes
6. Geração do relatório Allure
7. Deploy no GitHub Pages

**Badge de Status:**
- Verde: Todos os testes passaram
- Vermelho: Algum teste falhou
- Amarelo: Pipeline em execução

## Boas Práticas Implementadas

1. **Page Object Model (POM)** - Separação de responsabilidades
2. **Custom Test Fixtures** - Injeção de dependência
3. **TypeScript** - Tipagem estática e segurança
4. **ESLint + Prettier** - Qualidade e formatação de código
5. **Dados Centralizados** - Fixtures e test data separados
6. **Relatórios Detalhados** - Allure com screenshots e vídeos
7. **CI/CD Automatizado** - Execução e deploy automáticos
8. **Multi-browser** - Testes em Chromium, Firefox e WebKit
9. **Retry e Timeout** - Configurações para estabilidade
10. **Versionamento** - Controle com `.gitignore` e `package-lock.json`

## Licença

Este projeto está licenciado sob a **Licença ISC**.
