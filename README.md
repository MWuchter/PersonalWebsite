# Personal Website

This is a minimal front-end template built with Vue 3 and Vite to serve as a starter for a personal website showcasing your projects.

## Quick Start

1. Install dependencies

```powershell
npm install
```

2. Start dev server

```powershell
npm run dev
```

3. Build for production

```powershell
npm run build
npm run preview
```

## Deployment

### Deploy to Render.com

This project is configured for automatic deployment on Render.com as a static site.

**Steps:**

1. Push your code to a GitHub repository
2. Go to [Render.com](https://render.com) and sign in
3. Click "New +" and select "Static Site"
4. Connect your GitHub repository
5. Render will automatically detect the `render.yaml` configuration
6. Click "Create Static Site"

The site will automatically build and deploy. Render will run:
- Build Command: `npm install && npm run build`
- Publish Directory: `./dist`

Your site will be live at the URL provided by Render, typically: `https://your-site-name.onrender.com`

**Manual Configuration (if needed):**

If the render.yaml is not detected, you can manually configure:
- Build Command: `npm install && npm run build`
- Publish Directory: `dist`
