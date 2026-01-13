# Cookin' Up

Aplicação web desenvolvida com Vue 3 e TypeScript para seleção de ingredientes e sugestão de receitas. O projeto permite
que os usuários selecionem ingredientes disponíveis em sua cozinha por categorias e, com base nessa seleção, recebam
sugestões de receitas que podem ser preparadas com os ingredientes escolhidos.

> 📚 **Projeto desenvolvido durante o curso de Vue 3 da [Alura](https://www.alura.com.br/)**

## 🚀 Tecnologias Utilizadas

- **Vue 3** - Framework JavaScript progressivo
- **TypeScript** - Superset JavaScript com tipagem estática
- **Vite** - Build tool e dev server
- **Playwright** - Framework para testes end-to-end

## 📋 Funcionalidades Implementadas

- Visualização de lista de ingredientes organizados por categorias
- Seleção e deseleção interativa de ingredientes
- Sistema de busca de receitas baseado nos ingredientes selecionados
- Exibição de receitas disponíveis com os ingredientes escolhidos
- Navegação entre páginas (Seleção de Ingredientes ↔ Exibição de Receitas)
- Preservação do estado da seleção ao navegar entre páginas (KeepAlive)
- Renderização condicional com `v-if`, `v-else` e `v-else-if`
- Listagem dinâmica de ingredientes e receitas com `v-for`
- Sistema de eventos customizados entre componentes (emit/props)
- Requisições HTTP assíncronas para buscar dados de APIs externas
- Filtragem inteligente de receitas através de operações de listas
- Componentização seguindo boas práticas do Vue
- Interface responsiva com design moderno
- Gestão de estado local com data properties

## 🏗️ Estrutura de Componentes

### Componentes Principais

- **App.vue** - Componente raiz da aplicação
- **Banner.vue** - Cabeçalho com logo e apresentação do app
- **ConteudoPrincipal.vue** - Gerencia o estado dos ingredientes e navegação entre páginas
- **SelecionarIngredientes.vue** - Exibe categorias de ingredientes disponíveis para seleção
- **MostrarReceitas.vue** - Lista receitas filtradas baseadas nos ingredientes selecionados
- **SuaLista.vue** - Exibe os ingredientes atualmente selecionados pelo usuário
- **CardCategoria.vue** - Card individual de cada categoria de ingredientes
- **CardReceita.vue** - Card individual para exibição de uma receita
- **IngredienteSelecionavel.vue** - Componente de ingrediente com estado de seleção
- **Tag.vue** - Componente reutilizável para exibir tags de ingredientes
- **BotaoPrincipal.vue** - Botão estilizado reutilizável para ações principais
- **Rodape.vue** - Rodapé da aplicação

### Interfaces

- **ICategoria.ts** - Interface TypeScript para definir a estrutura de uma categoria
    - `nome: string` - Nome da categoria
    - `ingredientes: string[]` - Array de ingredientes da categoria
    - `imagem: string` - Caminho da imagem do ícone

- **IReceita.ts** - Interface TypeScript para definir a estrutura de uma receita
    - `nome: string` - Nome da receita
    - `ingredientes: string[]` - Lista de ingredientes necessários
    - `imagem: string` - Caminho da imagem da receita

### Serviços HTTP

- **http/index.ts** - Serviço para realizar requisições HTTP
    - `obterDadosURL<T>(url: string)` - Função genérica para buscar dados de uma URL
    - `obterCategorias()` - Busca categorias de ingredientes de uma API externa
    - `obterReceitas()` - Busca receitas disponíveis de uma API externa

### Operações e Utilitários

- **operacoes/listas.ts** - Funções auxiliares para manipulação de listas
    - `itensDeLista1EstaoEmLista2(lista1, lista2)` - Verifica se todos os itens da lista1 estão presentes na lista2

## 🔄 Fluxo de Dados

O aplicativo utiliza um fluxo unidirecional de dados seguindo as práticas do Vue:

1. **ConteudoPrincipal** mantém o estado central dos ingredientes selecionados e controla a navegação entre páginas
2. Eventos customizados (`adicionarIngrediente`, `removerIngrediente`, `buscarReceitas`, `editarReceitas`) são emitidos
   dos componentes filhos
3. Props são passadas para componentes filhos para exibição de dados
4. Sistema de re-emissão de eventos através da hierarquia de componentes
5. **KeepAlive** preserva o estado do componente `SelecionarIngredientes` ao navegar entre páginas
6. Filtragem de receitas é realizada verificando se todos os ingredientes da receita estão na lista selecionada

## 📝 Histórico de Desenvolvimento

O projeto foi desenvolvido seguindo uma evolução incremental:

1. **Configuração Inicial** - Instalação do Vue e estrutura base do projeto
2. **Componentização** - Criação dos componentes seguindo boas práticas
3. **Diretivas Vue** - Implementação de `v-for` com atributo `key` usando `v-bind`
4. **Renderização Condicional** - Uso de `v-if` e `v-else` para exibir lista vazia
5. **Integração com API** - Requisições HTTP para buscar categorias dinâmicas de uma API externa
6. **Personalização** - Customização de conteúdos e estilos dos componentes
7. **Interatividade** - Implementação de ingredientes selecionáveis com sistema de eventos
8. **Comunicação entre Componentes** - Sistema de emissão e re-emissão de eventos customizados
9. **Botões e Rodapé** - Adição de componentes de interface (BotaoPrincipal e Rodapé)
10. **Navegação entre Páginas** - Implementação de navegação com KeepAlive para preservar estado
11. **Sistema de Receitas** - Criação de componentes para exibir receitas (MostrarReceitas e CardReceita)
12. **Lógica de Filtragem** - Implementação de funções para verificar ingredientes e filtrar receitas
13. **Refatoração** - Otimização do código HTTP com função genérica e tipagem aprimorada

## 🛠️ Configuração do Ambiente

### IDE Recomendada

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (
desabilite o
Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

### Suporte de Tipos para Arquivos `.vue`

O TypeScript não lida nativamente com informações de tipo em imports `.vue`. Por isso, utilizamos `vue-tsc` no lugar do
`tsc` para verificação de tipos. No editor,
o [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin)
torna o serviço de linguagem TypeScript ciente dos tipos `.vue`.

Para melhor performance, você pode habilitar
o [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) do Volar:

1. Desabilite a extensão TypeScript integrada:
    1) Execute `Extensions: Show Built-in Extensions` na paleta de comandos do VSCode
    2) Encontre `TypeScript and JavaScript Language Features`, clique com o botão direito e selecione
       `Disable (Workspace)`
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

### Testes End-to-End com [Playwright](https://playwright.dev)

> ⚠️ **Nota:** Os testes end-to-end serão implementados em breve.

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
- **Diretivas** - `v-for`, `v-if`, `v-else`, `v-else-if`, `v-bind`
- **Data Binding** - Vinculação reativa de dados
- **Lifecycle Hooks** - Uso de `created` para chamadas assíncronas
- **Computed Properties** - Uso de `:class` com objetos dinâmicos
- **TypeScript Integration** - Tipagem forte com interfaces e PropTypes
- **Async/Await** - Requisições assíncronas com fetch API
- **KeepAlive** - Preservação de estado de componentes ao navegar
- **Conditional Rendering** - Renderização de componentes baseada em estado
- **Array Methods** - Uso de `filter` e `every` para operações em arrays
- **Type Safety** - Uso de generics para funções tipadas
- **Component Naming** - Propriedade `name` para identificação de componentes

## 📁 Estrutura do Projeto

```
cookin-up/
├── public/              # Arquivos estáticos
│   └── imagens/        # Imagens de categorias e receitas
├── src/
│   ├── assets/         # Imagens e recursos estáticos
│   │   ├── images/     # Imagens da aplicação
│   │   └── main.css    # Estilos globais
│   ├── components/     # Componentes Vue
│   │   ├── Banner.vue
│   │   ├── BotaoPrincipal.vue
│   │   ├── CardCategoria.vue
│   │   ├── CardReceita.vue
│   │   ├── ConteudoPrincipal.vue
│   │   ├── IngredienteSelecionavel.vue
│   │   ├── MostrarReceitas.vue
│   │   ├── Rodape.vue
│   │   ├── SelecionarIngredientes.vue
│   │   ├── SuaLista.vue
│   │   └── Tag.vue
│   ├── http/          # Serviços de API
│   │   └── index.ts
│   ├── interfaces/    # Interfaces TypeScript
│   │   ├── ICategoria.ts
│   │   └── IReceita.ts
│   ├── operacoes/     # Funções utilitárias
│   │   └── listas.ts
│   ├── App.vue        # Componente raiz
│   └── main.ts        # Entry point
├── e2e/               # Testes end-to-end
└── package.json       # Dependências do projeto
```

## 🎯 Funcionalidades Principais

### Seleção de Ingredientes

Usuários podem navegar por diferentes categorias de ingredientes (Laticínios, Frutas, Verduras, etc.) e selecionar
aqueles que possuem em casa. Os ingredientes selecionados aparecem em uma lista no topo da página.

### Busca de Receitas

Ao clicar em "Buscar receitas!", o sistema filtra e exibe apenas as receitas que podem ser preparadas com os
ingredientes selecionados. A verificação garante que todos os ingredientes necessários para a receita estejam
disponíveis.

### Navegação Fluida

A aplicação utiliza o componente `KeepAlive` do Vue para preservar o estado da seleção ao navegar entre as páginas de
seleção de ingredientes e visualização de receitas, proporcionando uma experiência de usuário fluida.

### Feedback Visual

Caso nenhuma receita seja encontrada com os ingredientes selecionados, uma mensagem amigável é exibida juntamente com
uma ilustração, incentivando o usuário a tentar uma nova combinação.

## 📖 Sobre o Curso

Este projeto foi desenvolvido como parte do curso **" Vue 3: entendendo componentes, diretivas e reatividade no
framework"** da [Alura](https://www.alura.com.br/), que aborda desde os fundamentos do Vue 3 até conceitos avançados
como componentização, TypeScript, requisições HTTP e gerenciamento de estado.

## 📄 Licença

Este projeto é fictício e foi desenvolvido exclusivamente para fins educacionais.
