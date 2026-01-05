# Cookin' Up

Aplicação web desenvolvida com Vue 3 e TypeScript para seleção de ingredientes e sugestão de receitas. O projeto permite que os usuários visualizem e gerenciem uma lista de ingredientes disponíveis em sua cozinha.

## 🚀 Tecnologias Utilizadas

- **Vue 3** - Framework JavaScript progressivo
- **TypeScript** - Superset JavaScript com tipagem estática
- **Vite** - Build tool e dev server
- **Playwright** - Framework para testes end-to-end

## 📋 Funcionalidades Implementadas

- Visualização de lista de ingredientes
- Renderização condicional com `v-if` e `v-else`
- Listagem dinâmica de ingredientes com `v-for`
- Componentização seguindo boas práticas do Vue
- Interface responsiva com design moderno

## 🛠️ Configuração do Ambiente

### IDE Recomendada

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (desabilite o Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

### Suporte de Tipos para Arquivos `.vue`

O TypeScript não lida nativamente com informações de tipo em imports `.vue`. Por isso, utilizamos `vue-tsc` no lugar do `tsc` para verificação de tipos. No editor, o [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) torna o serviço de linguagem TypeScript ciente dos tipos `.vue`.

Para melhor performance, você pode habilitar o [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) do Volar:

1. Desabilite a extensão TypeScript integrada:
   1) Execute `Extensions: Show Built-in Extensions` na paleta de comandos do VSCode
   2) Encontre `TypeScript and JavaScript Language Features`, clique com o botão direito e selecione `Disable (Workspace)`
2. Recarregue a janela do VSCode executando `Developer: Reload Window` na paleta de comandos.

## 📦 Configuração Adicional

Consulte a [Referência de Configuração do Vite](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Run End-to-End Tests with [Playwright](https://playwright.dev)

```sh
# Install browsers for the first run
npx playwright install

# When testing on CI, must build the project first
npm run build

# Runs the end-to-end tests
npm run test:e2e
# Runs the tests only on Chromium
npm run test:e2e -- --project=chromium
# Runs the tests of a specific file
npm run test:e2e -- tests/example.spec.ts
# Runs the tests in debug mode
npm run test:e2e -- --debug
```
