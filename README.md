# Nitro Starter

A minimal starter project built with [Nitro](https://nitro.build) - a powerful server toolkit for building fast and portable web applications.

## Table of Contents

- [About Nitro](#about-nitro)
- [Local Development](#local-development)
- [Build & Preview](#build--preview)
- [GitHub Pages Deployment](#github-pages-deployment)
  - [How it Works](#how-it-works)
  - [GitHub Pages Preset](#github-pages-preset)
  - [Setup Requirements](#setup-requirements)
- [Learn More](#learn-more)

## About Nitro

Nitro is a next-generation server framework that provides:

- **Universal Deployment**: Build once, deploy anywhere with preset support for multiple platforms (Node.js, Cloudflare Workers, Vercel, Netlify, AWS, and more)
- **File-based Routing**: Automatic API routes based on your file structure in `server/routes/`
- **Auto-imports**: No need to manually import utilities - Nitro handles it automatically
- **Built on h3**: Powered by the minimal and performant h3 HTTP framework
- **Hot Module Replacement**: Instant updates during development without full reloads
- **TypeScript Support**: First-class TypeScript support out of the box

## Local Development

To start the development server locally:

```bash
npm run dev
```

This will:

- Start the Nitro development server with hot module replacement
- Make your application available at **http://localhost:3000/**
- Watch for file changes and automatically reload
- Provide detailed error messages and stack traces

You can edit `server/routes/index.ts` to modify the homepage or add new routes by creating files in the `server/routes/` directory.

## Build & Preview

Preview the production build locally:

```bash
npm run preview
```

Build the application for production:

```bash
npm run build
```

## GitHub Pages Deployment

This project is configured for automatic deployment to GitHub Pages via GitHub Actions.

### How it Works

1. **Trigger**: The deployment workflow runs automatically on every push to the `main` branch (or can be triggered manually via workflow_dispatch)

2. **Build Process** (`.github/workflows/deploy.yml`):
   - Checks out the repository
   - Sets up Node.js with the LTS version
   - Installs dependencies using `npx nypm install`
   - Builds the project with `npm run build` using the **`github_pages` preset**
   - The `NITRO_PRESET=github_pages` environment variable tells Nitro to generate static files optimized for GitHub Pages
   - Uploads the `.output/public` directory as a Pages artifact

3. **Deploy Process**:
   - Deploys the artifact to GitHub Pages
   - Requires `pages: write` and `id-token: write` permissions
   - Uses the `github-pages` environment

### GitHub Pages Preset

The `github_pages` preset is crucial for this deployment:

- Generates static HTML files in `.output/public`
- Configures the base URL to work with GitHub Pages subdirectory structure
- Optimizes assets for static hosting
- Creates a `404.html` for client-side routing fallback

### Setup Requirements

To enable GitHub Pages deployment for your repository:

1. Go to your repository **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. The workflow will automatically deploy on the next push to `main`

## Learn More

- 📖 [Nitro Documentation](https://nitro.build/guide)
- 🚀 [Nitro Quick Start](https://nitro.build/guide#quick-start)
- 🔧 [Nitro Deployment Presets](https://nitro.build/deploy)
- 🌐 [h3 Framework](https://h3.unjs.io/)
