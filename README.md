# Svelte UI Components

A comprehensive collection of reusable UI components built with [Svelte](https://svelte.dev/) and TypeScript. This library provides modern, customizable, and accessible components for building beautiful web applications.

![Demo Page](https://github.com/user-attachments/assets/65fea74d-012b-4946-bf8a-440bce656666)

## ✨ Features

- 🎨 **25+ Components** - Comprehensive collection of UI components
- 🔧 **TypeScript Support** - Full type safety and IntelliSense
- 🎯 **CSS Variables** - Easy theming and customization
- 📱 **Responsive Design** - Mobile-first approach
- ♿ **Accessibility** - ARIA compliant components
- 🚀 **Zero Dependencies** - Lightweight and performant
- 📦 **Tree Shakable** - Import only what you need

## 📦 Installation

This library is published on npm and can be installed via any npm client:

```bash
npm install @juspay/svelte-ui-components
```

```bash
pnpm add @juspay/svelte-ui-components
```

```bash
yarn add @juspay/svelte-ui-components
```

## 🚀 Usage

The library contains a collection of components that can be imported and used in your Svelte project.

### 📋 Available Components

#### Core Components

- **Accordion** - Collapsible content sections
- **Badge** - Status indicators and labels
- **Banner** - Promotional messages and alerts
- **BrandLoader** - Branded splash screen/loading component
- **Button** - Interactive buttons with loading states
- **Carousel** - Image/content carousel with navigation
- **CheckListItem** - Enhanced checkbox with custom styling
- **GridItem** - Grid layout item with loading animation
- **Icon** - Customizable icon component
- **Img** - Enhanced image component
- **Input** - Form input with validation
- **InputButton** - Input field with attached button
- **ListItem** - Flexible list item component
- **Loader** - Loading indicators (circular, progress bar)
- **Modal** - Overlay dialogs with animations
- **Select** - Dropdown selection component
- **Status** - Status screen for empty/error states
- **Stepper** - Multi-step form navigation
- **Step** - Individual step component
- **Table** - Data table with sorting
- **Toast** - Notification messages
- **Toggle** - Switch/toggle component
- **Toolbar** - Action toolbar component

#### Animation Components

- **ModalAnimation** - Modal transition animations
- **OverlayAnimation** - Overlay transition effects

All components can be easily imported from the package:

### 📖 Basic Usage Example

```svelte
<script lang="ts">
  import { Button, defaultButtonProperties } from '@juspay/svelte-ui-components';
</script>

<Button properties={{ ...defaultButtonProperties, text: 'Click Me' }} />
```

### 🔧 Advanced Usage with TypeScript

```svelte
<script lang="ts">
  import {
    Button,
    Modal,
    Input,
    type ButtonProperties,
    type ModalProperties,
    type InputProperties,
    defaultButtonProperties,
    defaultModalProperties,
    defaultInputProperties
  } from '@juspay/svelte-ui-components';

  let showModal = false;
  let inputValue = '';

  const buttonProps: ButtonProperties = {
    ...defaultButtonProperties,
    text: 'Open Modal',
    type: 'button'
  };

  const modalProps: ModalProperties = {
    ...defaultModalProperties,
    size: 'medium',
    align: 'center'
  };

  const inputProps: InputProperties = {
    ...defaultInputProperties,
    placeholder: 'Enter your name...',
    required: true
  };

  function handleButtonClick() {
    showModal = true;
  }

  function handleModalClose() {
    showModal = false;
  }
</script>

<Button properties={buttonProps} on:click={handleButtonClick} />

{#if showModal}
  <Modal properties={modalProps} on:close={handleModalClose}>
    <h2>User Information</h2>
    <Input bind:value={inputValue} properties={inputProps} />
  </Modal>
{/if}
```

## 🎨 Customizing Components

Each component comes with extensive customization options through two approaches:

### 1. CSS Variables (Recommended)

All components expose CSS variables for styling properties, making theming consistent and easy:

```svelte
<style>
  :global(body) {
    /* Global theme variables */
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --success-color: #28a745;
    --danger-color: #dc3545;

    /* Component-specific variables */
    --button-background-color: var(--primary-color);
    --button-text-color: white;
    --button-border-radius: 8px;
    --button-padding: 12px 24px;

    --modal-background-color: white;
    --modal-max-width: 600px;
    --modal-border-radius: 12px;

    --input-border-color: #ced4da;
    --input-focus-border-color: var(--primary-color);
    --input-padding: 10px 12px;
  }
</style>
```

### 2. Properties/Props

Components accept properties for dynamic behavior and content:

```svelte
<script lang="ts">
  import {
    Button,
    type ButtonProperties,
    defaultButtonProperties
  } from '@juspay/svelte-ui-components';

  const buttonProperties: ButtonProperties = {
    ...defaultButtonProperties,
    text: 'Submit Form',
    type: 'submit',
    showLoader: false,
    enable: true,
    loaderType: 'Circular'
  };

  function handleSubmit() {
    // Show loading state
    buttonProperties.showLoader = true;

    // Simulate API call
    setTimeout(() => {
      buttonProperties.showLoader = false;
    }, 2000);
  }
</script>

<div class="form-container">
  <Button properties={buttonProperties} on:click={handleSubmit} />
</div>

<style>
  .form-container {
    --button-background-color: #28a745;
    --button-text-color: white;
    --button-border-radius: 6px;
    --button-padding: 14px 28px;
    --button-font-weight: 600;
  }
</style>
```

## 🛠️ Development & Contributing

### Prerequisites

- Node.js (v16 or higher)
- pnpm (recommended) or npm

### Getting Started

1. **Clone the repository**

   ```bash
   git clone https://github.com/swaroopvarma2359/svelte-ui-components.git
   cd svelte-ui-components
   ```

2. **Install dependencies**

   ```bash
   pnpm install
   # or
   npm install
   ```

3. **Start development server**
   ```bash
   pnpm run dev
   # or
   npm run dev
   ```
   This starts the development server at `http://localhost:5173` with a demo page showcasing the components.

### Available Scripts

| Command                 | Description                              |
| ----------------------- | ---------------------------------------- |
| `pnpm dev`              | Start development server with hot reload |
| `pnpm build`            | Build the library for production         |
| `pnpm preview`          | Preview the production build             |
| `pnpm package`          | Package the library for publishing       |
| `pnpm test`             | Run all tests (unit + integration)       |
| `pnpm test:unit`        | Run unit tests with Vitest               |
| `pnpm test:integration` | Run integration tests with Playwright    |
| `pnpm check`            | Type-check the project                   |
| `pnpm lint`             | Lint code with ESLint and Prettier       |
| `pnpm format`           | Format code with Prettier                |

### Testing

The project uses a comprehensive testing strategy:

- **Unit Tests**: Vitest for component logic testing
- **Integration Tests**: Playwright for end-to-end testing
- **Type Checking**: TypeScript and svelte-check for type safety

```bash
# Run all tests
pnpm test

# Run only unit tests
pnpm test:unit

# Run only integration tests
pnpm test:integration

# Type checking
pnpm check
```

### Building & Packaging

```bash
# Build the project
pnpm build

# Package for npm publishing
pnpm package

# The built library will be in the `dist/` directory
```

### Contributing Guidelines

1. **Fork the repository** and create your feature branch
2. **Make your changes** following the existing code style
3. **Add tests** for new components or functionality
4. **Run tests** to ensure everything works: `pnpm test`
5. **Lint your code**: `pnpm lint`
6. **Commit your changes** using conventional commits
7. **Push to your fork** and create a pull request

### Code Style

- Follow TypeScript best practices
- Use meaningful component and prop names
- Add JSDoc comments for complex functions
- Maintain consistent CSS variable naming
- Ensure accessibility standards (ARIA, keyboard navigation)

### Commit Convention

This project uses [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add new Toast component
fix: resolve Button loading state issue
docs: update README with new examples
style: format code with prettier
test: add unit tests for Modal component
```

## 📚 Project Structure

```
svelte-ui-components/
├── src/
│   ├── lib/                    # Component library
│   │   ├── Accordion/          # Accordion component
│   │   ├── Badge/              # Badge component
│   │   ├── Button/             # Button component
│   │   ├── Modal/              # Modal component
│   │   ├── ... (other components)
│   │   ├── types.ts            # Shared TypeScript types
│   │   ├── utils.ts            # Utility functions
│   │   └── index.ts            # Main export file
│   ├── routes/                 # Demo pages (SvelteKit)
│   └── app.html                # App template
├── tests/                      # Test files
├── scripts/                    # Build and deployment scripts
├── package.json                # Package configuration
├── vite.config.ts             # Vite configuration
├── svelte.config.js           # Svelte configuration
├── playwright.config.ts       # Playwright test configuration
└── README.md                  # This file
```

## 🔧 Technology Stack

- **[Svelte](https://svelte.dev/)** - Component framework
- **[SvelteKit](https://kit.svelte.dev/)** - Development and packaging
- **[TypeScript](https://www.typescriptlang.org/)** - Type safety
- **[Vite](https://vitejs.dev/)** - Build tool and dev server
- **[Vitest](https://vitest.dev/)** - Unit testing framework
- **[Playwright](https://playwright.dev/)** - End-to-end testing
- **[ESLint](https://eslint.org/)** - Code linting
- **[Prettier](https://prettier.io/)** - Code formatting
- **[Husky](https://typicode.github.io/husky/)** - Git hooks

## 📦 Publishing

This package is published to npm under the `@juspay` organization. The publishing process is automated with version management:

```bash
# Publish with version bump
node scripts/publish.js version=patch   # 1.0.0 -> 1.0.1
node scripts/publish.js version=minor   # 1.0.0 -> 1.1.0
node scripts/publish.js version=major   # 1.0.0 -> 2.0.0
```

The publish script handles:

- Version bumping in package.json
- Building the library
- Git tagging
- npm publishing with 2FA

## 🐛 Issues & Support

If you encounter any issues or have questions:

1. Check the [existing issues](https://github.com/swaroopvarma2359/svelte-ui-components/issues)
2. Create a new issue with detailed information
3. Include code examples and expected behavior
4. Mention your environment (Node.js version, browser, etc.)

## 📝 Changelog

See the [commit history](https://github.com/swaroopvarma2359/svelte-ui-components/commits) for detailed changes and updates.

## 🙏 Acknowledgments

- Built with ❤️ using [Svelte](https://svelte.dev/)
- Inspired by modern component libraries
- Thanks to all contributors and users

---

**Happy coding!** 🚀
