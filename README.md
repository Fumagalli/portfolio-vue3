# Ângelo Fumagalli - Portfolio - VUE 3

Portfolio profissional desenvolvido com tecnologias modernas de frontend, apresentando experiência, projetos e habilidades técnicas.

## 🚀 Tecnologias Utilizadas

### Core

- **[Vue 3](https://vuejs.org/)** - Framework progressivo para construção de interfaces
- **[TypeScript](https://www.typescriptlang.org/)** - Superset JavaScript com tipagem estática
- **[Vite](https://vitejs.dev/)** - Build tool e dev server de última geração

### UI/Styling

- **[Tailwind CSS](https://tailwindcss.com/)** - Framework CSS utility-first
- **[Lucide Vue Next](https://lucide.dev/)** - Biblioteca de ícones para Vue 3
- **[class-variance-authority](https://cva.style/)** - Variantes de componentes type-safe
- **[clsx](https://github.com/lukeed/clsx)** - Construção condicional de className
- **[tailwind-merge](https://github.com/dcastil/tailwind-merge)** - Merge de classes Tailwind

### State Management & Routing

- **[Pinia](https://pinia.vuejs.org/)** - Store oficial para Vue 3
- **[Vue Router](https://router.vuejs.org/)** - Roteamento oficial para Vue 3

### Internacionalização

- **[vue-i18n](https://vue-i18n.intlify.dev/)** - Plugin de internacionalização para Vue 3

### Testes

- **[Vitest](https://vitest.dev/)** - Framework de testes unitários
- **[Vue Test Utils](https://test-utils.vuejs.org/)** - Utilitários oficiais para testes

### Qualidade de Código

- **[ESLint](https://eslint.org/)** - Linter JavaScript/TypeScript
- **[Prettier](https://prettier.io/)** - Formatador de código

## 📁 Estrutura do Projeto

```bash
portfolio-vue3/
├── public/              # Arquivos estáticos
├── src/
│   ├── assets/          # Assets da aplicação
│   │   ├── i18n/        # Configuração de internacionalização
│   │   │   ├── index.ts
│   │   │   └── locales/ # Arquivos de tradução (pt.json, en.json)
│   │   └── styles/      # Estilos globais
│   │       └── main.css # Design system e variáveis CSS
│   ├── components/      # Componentes Vue
│   │   ├── ui/          # Componentes base reutilizáveis
│   │   │   ├── Button.vue
│   │   │   ├── Card.vue
│   │   │   └── Badge.vue
│   │   ├── Hero.vue
│   │   ├── Navigation.vue
│   │   ├── About.vue
│   │   ├── Projects.vue
│   │   ├── Experience.vue
│   │   ├── Testimonials.vue
│   │   ├── Contact.vue
│   │   └── Footer.vue
│   ├── composables/     # Composables reutilizáveis
│   │   └── useIntersectionObserver.ts
│   ├── router/          # Configuração de rotas
│   │   └── index.ts
│   ├── stores/          # Pinia stores
│   │   └── counter.ts
│   ├── utils/           # Funções utilitárias
│   │   └── cn.ts
│   ├── views/           # Páginas da aplicação
│   │   ├── HomePage.vue
│   │   └── NotFound.vue
│   ├── App.vue          # Componente raiz
│   └── main.ts          # Entry point
├── index.html           # Template HTML
├── tailwind.config.js   # Configuração do Tailwind CSS
├── tsconfig.json        # Configuração TypeScript
├── vite.config.ts       # Configuração Vite
├── vitest.config.ts     # Configuração Vitest
└── package.json
```

## 🎨 Padrões e Convenções

### Componentes

- Composition API com `<script setup>`
- Props tipadas com TypeScript
- Uso de `defineProps` e `defineEmits`
- Nomenclatura PascalCase para componentes

### Estilização

- Design system baseado em CSS variables (HSL)
- Classes utilitárias do Tailwind CSS
- Componentes temáticos com suporte a dark mode
- Uso de `cn()` helper para merge condicional de classes

### Internacionalização

- Suporte para PT-BR e EN
- Arquivos JSON separados por idioma em `src/assets/i18n/locales/`
- Uso de `useI18n()` composable para textos
- `t()` para strings simples e `tm()` para objetos/arrays

### TypeScript

- Strict mode habilitado
- Tipos explícitos para props e composables
- Interfaces para estruturas de dados
- Type safety em todo o código

### Composables

- Lógica reutilizável extraída em composables
- Nomenclatura com prefixo `use`
- Return de refs e funções reativas

## 🛠️ Como Executar

### Pré-requisitos

- Node.js 18+ instalado
- npm, yarn ou pnpm

### Instalação

```bash
# Clone o repositório
git clone https://github.com/Fumagalli/portfolio-vue3.git

# Entre no diretório
cd portfolio-vue3

# Instale as dependências
npm install
# ou
yarn install
# ou
pnpm install
```

### Desenvolvimento

```bash
# Inicie o servidor de desenvolvimento
npm run dev
# ou
yarn dev
# ou
pnpm dev
```

O projeto estará disponível em `http://localhost:5173`

### Build para Produção

```bash
# Gere a build de produção
npm run build
# ou
yarn build
# ou
pnpm build

# Preview da build
npm run preview
# ou
yarn preview
# ou
pnpm preview
```

### Testes

```bash
# Execute os testes unitários
npm run test:unit
# ou
yarn test:unit
# ou
pnpm test:unit
```

### Type Check

```bash
# Execute a verificação de tipos
npm run type-check
# ou
yarn type-check
# ou
pnpm type-check
```

### Linting

```bash
# Execute o ESLint
npm run lint
# ou
yarn lint
# ou
pnpm lint
```

## 🌍 Idiomas Disponíveis

O portfolio suporta dois idiomas:

- **Português (PT-BR)** - Idioma padrão
- **Inglês (EN)**

Alternar idioma através do seletor de idioma na interface.

## 📝 Configuração

### Variáveis de Ambiente

Não há variáveis de ambiente obrigatórias. Todas as configurações estão em arquivos TypeScript.

### Design System

As cores e estilos do design system estão definidos em `src/assets/styles/main.css` usando CSS custom properties.

### Tailwind Config

Configurações adicionais do Tailwind em `tailwind.config.js`, incluindo:

- Cores customizadas baseadas em HSL
- Animações personalizadas
- Extensões de tema
- Content paths para Vue files

## 🎯 Features

- ✅ Sistema completo de internacionalização (PT/EN)
- ✅ Design system robusto com variáveis CSS
- ✅ Componentes UI reutilizáveis (Button, Card, Badge)
- ✅ Intersection Observer para animações ao scroll
- ✅ Navegação fixa com detecção de scroll
- ✅ Layout totalmente responsivo
- ✅ TypeScript strict mode
- ✅ Testes unitários com Vitest
- ✅ Code splitting e lazy loading

## 📄 Licença

Todos os direitos reservados © 2025 Ângelo Fumagalli
