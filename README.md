### This project is built with:

- Vite
- TypeScript
- React
- shadcn-ui
- Tailwind CSS


## How to deploy it in github pages
This guide explains how to deploy a Vite + React project to GitHub Pages and update it later.

### 1. Clone your repository:

```bash
git clone https://github.com/<username>/<repo-name>.git
cd <repo-name>
```
### 2. Edit vite.config.ts

Set the base path to your repository name:

```bash
export default defineConfig({
  base: "/<repo-name>/",
  server: {
    host: "::",
    port: 8080,
    hmr: {
      overlay: false,
    },
  },
  plugins: [react(), componentTagger()].filter(Boolean),
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
});
```
### 3. Install gh-pages

In your terminal install gh-pages
```bash
npm install --save-dev gh-pages
```
### 4. Update package.json
If not already present, add:
```bash
"scripts": {
  "predeploy": "npm run build",
  "deploy": "gh-pages -d dist"
}
```
### 5. Deploy
In your terminal, run
```bash
npm run deploy
```
### 6. Enable GitHub Pages
Go to: Repository → Settings → Pages

Set:
```bash
Source: Deploy from branch
Branch: gh-pages
Folder: / (root)
```

## Updating the site
Whenever you make changes:
```bash
git add .
git commit -m "update"
git push
npm run deploy
```
