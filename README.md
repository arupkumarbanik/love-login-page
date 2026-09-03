# 💖 Love Login Page — Romantic Wedding OTP Verification

An interactive, romantic **Pink Wedding-Themed OTP Verification & Login Page** built with **React 19**, **TypeScript**, **Vite**, and **Tailwind CSS v4**.

Designed with glassmorphic cards, smooth micro-interactions, canvas-driven rose petal showers, and playful wedding-themed success/failure states.

[![Author](https://img.shields.io/badge/Author-Arup%20Kumar%20Banik-ff4d79?style=flat&logo=github)](https://github.com/arupkumarbanik)
[![Repository](https://img.shields.io/badge/Repository-love--login--page-rose?style=flat&logo=github)](https://github.com/arupkumarbanik/love-login-page)
[![React](https://img.shields.io/badge/React-19.0-61dafb?style=flat&logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178c6?style=flat&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-4.1-38bdf8?style=flat&logo=tailwindcss)](https://tailwindcss.com/)
[![Vite](https://img.shields.io/badge/Vite-6.2-646cff?style=flat&logo=vite)](https://vitejs.dev/)

---

## ✨ Features

- 💌 **Romantic Glassmorphism Design**: Frosted glass card with subtle rose-tinted borders, multi-layered depth, and elegant typography (*Playfair Display*, *Cormorant Garamond*, *Great Vibes*, and *Plus Jakarta Sans*).
- 🔢 **6-Digit Smart OTP Input**:
  - Auto-focus and auto-advance between inputs
  - Backspace & arrow key navigation
  - Full clipboard paste handling (auto-fills all 6 boxes)
  - Numeric filter enforcement
  - Individual digit vertical rolling animation
- 🌸 **Canvas Particle Engine**:
  - Ambient floating hearts, warm orbs, and twinkling sparkles
  - High-performance celebratory rose petal drop and champagne gold confetti shower on verification success
  - Fully responsive with automatic window resize handling
- 🎉 **Cinematic Success State**:
  - Radiant heart entrance with rhythmic romantic pulse
  - Smooth SVG checkmark stroke draw animation
  - Champagne gold twinkling sparkles around the title
  - Wedding Passcode confirmation card with glowing borders
  - Interactive "Test Another Code" button with hover sheen
- 💔 **Playful Unsuccessful State**:
  - Animated broken heart separation and settle effect with soft crack glow
  - Lighthearted, wedding-appropriate copy (*"Check your heart, feel the love, and try again"* ❤️)
  - Staggered individual OTP box error shake
  - Pulsing demo hint card
  - One-click "Try Again" reset that restores focus
- 📱 **Mobile-First & Accessible**:
  - Zero unwanted horizontal page scroll or viewport shifts
  - Fully responsive on all screen sizes
  - Hardware-accelerated CSS animations (`transform`, `opacity`, `filter`)
  - `prefers-reduced-motion` support

---

## 🛠️ Tech Stack

- **Framework**: [React 19](https://react.dev/)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **Icons**: [Lucide React](https://lucide.dev/)
- **Bundler & Dev Server**: [Vite 6](https://vitejs.dev/)

---

## 🚀 Quick Start (Local Development)

### Prerequisites
Make sure you have **Node.js** (v18 or higher) and **npm** / **bun** installed.

### 1. Clone the repository
```bash
git clone https://github.com/arupkumarbanik/love-login-page.git
cd love-login-page
```

### 2. Install dependencies
```bash
npm install
```

### 3. Start development server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) (or the port shown in terminal) in your browser.

### 4. Build for production
```bash
npm run build
```
The compiled, optimized static files will be placed into the `dist/` directory.

---

## 🧪 Demo Passcode

To test the different states:
- **Valid Code**: Enter `123456` to trigger the **Success Celebration** with rose petals and confetti.
- **Invalid Code**: Enter any other 6-digit combination (e.g. `000000`) to see the **Broken Heart** animation and playful retry message.

---

## 🌐 Deployment Guide

You can easily deploy this static SPA to your preferred platform:

### Option 1: Deploy to Vercel (Recommended)
1. Fork or push this repository to your GitHub account: `https://github.com/arupkumarbanik/love-login-page`
2. Go to [Vercel](https://vercel.com) and click **"Add New Project"**.
3. Import `love-login-page`.
4. Vercel automatically detects Vite:
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
5. Click **Deploy**. Your app will be live with a free SSL certificate!

---

### Option 2: Deploy to Netlify
1. Log into [Netlify](https://www.netlify.com/).
2. Click **"Add new site"** > **"Import an existing project"** > select **GitHub**.
3. Choose `love-login-page`.
4. Set build settings:
   - **Build command**: `npm run build`
   - **Publish directory**: `dist`
5. Click **Deploy Site**.

---

### Option 3: Deploy to GitHub Pages

1. In `vite.config.ts`, set the base path to your repository name if needed:
   ```typescript
   export default defineConfig({
     base: '/love-login-page/',
     plugins: [react(), tailwindcss()],
   });
   ```
2. Install `gh-pages` helper (optional) or use **GitHub Actions**:
   Create `.github/workflows/deploy.yml`:
   ```yaml
   name: Deploy to GitHub Pages

   on:
     push:
       branches: [main]

   permissions:
     contents: read
     pages: write
     id-token: write

   concurrency:
     group: 'pages'
     cancel-in-progress: true

   jobs:
     deploy:
       environment:
         name: github-pages
         url: ${{ steps.deployment.outputs.page_url }}
       runs-on: ubuntu-latest
       steps:
         - name: Checkout
           uses: actions/checkout@v4
         - name: Set up Node.js
           uses: actions/setup-node@v4
           with:
             node-version: 20
             cache: 'npm'
         - name: Install dependencies
           run: npm install
         - name: Build
           run: npm run build
         - name: Setup Pages
           uses: actions/configure-pages@v4
         - name: Upload artifact
           uses: actions/upload-pages-artifact@v3
           with:
             path: './dist'
         - name: Deploy to GitHub Pages
           id: deployment
           uses: actions/deploy-pages@v4
   ```
3. In your repo settings on GitHub, navigate to **Settings** > **Pages** > select **GitHub Actions** as the source.

---

### Option 4: Deploy with Docker / Cloud Run / Render
A standard production build produces a static directory (`dist/`). You can serve it using Nginx or any static file server:

```dockerfile
# Build stage
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Serve stage
FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

---

## 📤 How to Push to Your GitHub Repository

If you haven't pushed this code to your GitHub repo yet, run these commands from your local project terminal:

```bash
# 1. Initialize git (if not already initialized)
git init

# 2. Add all files to staging
git add .

# 3. Commit your changes
git commit -m "feat: initial release of love-login-page with romantic OTP verification"

# 4. Set the default branch to main
git branch -M main

# 5. Link to your GitHub repository
git remote add origin https://github.com/arupkumarbanik/love-login-page.git

# 6. Push to GitHub
git push -u origin main
```

*(If the remote repository already exists with an initial README or license, run `git pull origin main --rebase` before pushing).*

---

## 📂 Project Structure

```text
love-login-page/
├── index.html                  # HTML5 entry with Google Fonts
├── package.json                # Project dependencies and npm scripts
├── vite.config.ts              # Vite configuration with Tailwind CSS v4 plugin
├── tsconfig.json               # TypeScript configuration
├── public/                     # Static assets and icons
└── src/
    ├── main.tsx                # Application root entry
    ├── App.tsx                 # Main layout & OTP state coordinator
    ├── index.css               # Tailwind CSS imports, custom keyframes & glassmorphism
    ├── types.ts                # TypeScript interfaces and status types
    ├── components/
    │   ├── OtpInput.tsx        # 6-digit input boxes with rolling transition & auto-advance
    │   ├── ParticleBackground.tsx # Canvas particle engine (floating hearts, rose petals, confetti)
    │   ├── SuccessView.tsx     # Cinematic verification celebration view
    │   ├── BrokenHeartView.tsx # Playful failure view with heart split animation
    │   ├── WeddingIcon.tsx     # Intertwined gold rings & diamond motif
    │   └── Toast.tsx           # Romantic floating status notification
    └── utils/
        └── otpValidator.ts     # OTP verification logic & validation helpers
```

---

## 👤 Author

**Arup Kumar Banik**
- GitHub: [@arupkumarbanik](https://github.com/arupkumarbanik)
- Repository: [love-login-page](https://github.com/arupkumarbanik/love-login-page)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
Feel free to use and customize this for your romantic events, weddings, or themed applications!
