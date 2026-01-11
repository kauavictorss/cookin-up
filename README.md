# Cookin' Up

Aplicação web desenvolvida com Vue 3 e TypeScript para seleção de ingredientes e sugestão de receitas. O projeto permite que os usuários visualizem e gerenciem uma lista de ingredientes disponíveis em sua cozinha, selecionando-os por categorias de forma interativa.

## 🚀 Tecnologias Utilizadas

- **Vue 3** - Framework JavaScript progressivo
- **TypeScript** - Superset JavaScript com tipagem estática
- **Vite** - Build tool e dev server
- **Playwright** - Framework para testes end-to-end

## 📋 Funcionalidades Implementadas

- Visualização de lista de ingredientes por categorias
- Seleção e deseleção interativa de ingredientes
- Renderização condicional com `v-if` e `v-else`
- Listagem dinâmica de ingredientes com `v-for`
- Sistema de eventos customizados entre componentes (emit/props)
- Requisições HTTP para buscar categorias de uma API externa
- Componentização seguindo boas práticas do Vue
- Interface responsiva com design moderno
- Gestão de estado local com data properties

## 🏗️ Estrutura de Componentes

### Componentes Principais

- **App.vue** - Componente raiz da aplicação
- **Banner.vue** - Cabeçalho com logo e apresentação do app
- **ConteudoPrincipal.vue** - Gerencia o estado dos ingredientes selecionados
- **SelecionarIngredientes.vue** - Exibe categorias de ingredientes disponíveis
- **SuaLista.vue** - Mostra os ingredientes selecionados pelo usuário
- **CardCategoria.vue** - Card individual de cada categoria de ingredientes
- **IngredienteSelecionavel.vue** - Componente de ingrediente com estado de seleção
- **Tag.vue** - Componente reutilizável para exibir tags de ingredientes

### Interfaces

- **ICategoria.ts** - Interface TypeScript para definir a estrutura de uma categoria
  - `nome: string` - Nome da categoria
  - `ingredientes: string[]` - Array de ingredientes da categoria
  - `imagem: string` - Caminho da imagem do ícone

### Serviços HTTP

- **http/index.ts** - Serviço para realizar requisições HTTP
  - `obterCategorias()` - Busca categorias de ingredientes de uma API externa

## 🔄 Fluxo de Dados

O aplicativo utiliza um fluxo unidirecional de dados seguindo as práticas do Vue:

1. **ConteudoPrincipal** mantém o estado central dos ingredientes selecionados
2. Eventos customizados (`adicionarIngrediente` e `removerIngrediente`) são emitidos dos componentes filhos
3. Props são passadas para componentes filhos para exibição de dados
4. Sistema de re-emissão de eventos através da hierarquia de componentes

## 📝 Histórico de Desenvolvimento

O projeto foi desenvolvido seguindo uma evolução incremental:

1. **Configuração Inicial** - Instalação do Vue e estrutura base do projeto
2. **Componentização** - Criação dos componentes seguindo boas práticas
3. **Diretivas Vue** - Implementação de `v-for` com atributo `key` usando `v-bind`
4. **Renderização Condicional** - Uso de `v-if` e `v-else` para exibir lista vazia
5. **Integração com API** - Requisições HTTP para buscar categorias dinâmicas
6. **Personalização** - Customização de conteúdos e estilos dos componentes
7. **Interatividade** - Implementação de ingredientes selecionáveis com sistema de eventos
8. **Comunicação entre Componentes** - Sistema de emissão e re-emissão de eventos customizados

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

## 🚦 Como Executar o Projeto

### Instalação

```sh
npm install
```

### Executar em Modo de Desenvolvimento

```sh
npm run dev
```

### Build para Produção

```sh
npm run build
```

### Executar Testes End-to-End com [Playwright](https://playwright.dev)

```sh
# Instalar navegadores (primeira execução)
npx playwright install

# Build do projeto para testes em CI
npm run build

# Executar os testes end-to-end
npm run test:e2e

# Executar testes apenas no Chromium
npm run test:e2e -- --project=chromium

# Executar testes de um arquivo específico
npm run test:e2e -- tests/example.spec.ts

# Executar testes em modo debug
npm run test:e2e -- --debug
```

## 🎨 Conceitos Vue Aplicados

Este projeto demonstra a aplicação prática de diversos conceitos fundamentais do Vue 3:

- **Composição de Componentes** - Estrutura modular e reutilizável
- **Props** - Passagem de dados de pai para filho
- **Custom Events** - Comunicação de filho para pai através de eventos
- **Event Re-emission** - Re-emissão de eventos através da hierarquia
- **Diretivas** - `v-for`, `v-if`, `v-else`, `v-bind`
- **Data Binding** - Vinculação reativa de dados
- **Lifecycle Hooks** - Uso de `created` para chamadas assíncronas
- **Computed Properties** - Uso de `:class` com objetos dinâmicos
- **TypeScript Integration** - Tipagem forte com interfaces e PropTypes
- **Async/Await** - Requisições assíncronas com fetch API

## 📁 Estrutura do Projeto

```
cookin-up/
├── public/              # Arquivos estáticos
├── src/
│   ├── assets/         # Imagens e recursos
│   ├── components/     # Componentes Vue
│   │   ├── Banner.vue
│   │   ├── CardCategoria.vue
│   │   ├── ConteudoPrincipal.vue
│   │   ├── IngredienteSelecionavel.vue
│   │   ├── SelecionarIngredientes.vue
│   │   ├── SuaLista.vue
│   │   └── Tag.vue
│   ├── http/          # Serviços de API
│   │   └── index.ts
│   ├── interfaces/    # Interfaces TypeScript
│   │   └── ICategoria.ts
│   ├── App.vue        # Componente raiz
│   └── main.ts        # Entry point
├── e2e/               # Testes end-to-end
└── package.json       # Dependências do projeto
```
