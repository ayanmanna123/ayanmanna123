# Project Setup Guide

This guide outlines the process of setting up a modern React application using **Vite 8**, **Tailwind CSS v4**, and **Shadcn UI**.

## 1. Project Initialization

Create a new Vite project with the React template:

```bash
npm create vite@latest
```

## 2. Tailwind CSS v4 Installation

Install Tailwind CSS and its Vite plugin:

```bash
npm install tailwindcss @tailwindcss/vite
```

### Import Tailwind

Import Tailwind CSS in your CSS entry point (e.g., `src/index.css`):

```css
@import "tailwindcss";
```

## 3. Path Aliases & Node Types

Setting up the `@` alias for easier imports and installing Node types for configuration support.

### Install Node Types

Install `@types/node` to provide TypeScript/IDE support for Node modules like `path`:

```bash
npm install -D @types/node
```

### VS Code Support (jsconfig.json)

Create a `jsconfig.json` file in the root directory to enable autocomplete for the `@` alias:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

### Vite Configuration

Update `vite.config.js` to resolve the `@` path and register the Tailwind plugin:

```javascript
import path from "path";
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import tailwindcss from "@tailwindcss/vite";

export default defineConfig({
  plugins: [react(), tailwindcss()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
  server: {
    open: true,
    port: 5173,
  },
})
```

## 4. Shadcn UI Installation

Initialize Shadcn UI in your project:

```bash
npx shadcn@latest init
```

> [!NOTE]
> Since this project uses Tailwind v4, Shadcn's init process might detect it automatically. Follow the CLI prompts carefully.

## Summary of Tech Stack

- **Vite 8**: Next-generation frontend tooling.
- **React 19**: The latest version of React.
- **Tailwind CSS v4**: High-performance CSS framework.
- **Shadcn UI**: Beautifully designed, accessible components.
- **Node Types**: Added via `@types/node` for robust configuration support.
