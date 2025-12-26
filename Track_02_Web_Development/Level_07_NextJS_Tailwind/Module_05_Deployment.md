# Module 05: Deployment

## Level 2.7: Next.js & Tailwind

---

## 🎯 Module Objectives

By the end of this module, you will be able to:

- Deploy to Vercel (recommended)
- Deploy to alternative platforms
- Configure environment variables
- Set up custom domains

---

## Lesson 1: Preparing for Deployment

### Pre-deployment Checklist

```
□ Build succeeds locally (npm run build)
□ All tests pass
□ Environment variables documented
□ Images optimized
□ No console errors in production mode
□ SEO metadata configured
□ Error pages customized (404, 500)
□ Performance acceptable
```

### Build Locally First

```bash
# Build production version
npm run build

# Test production build locally
npm start
```

Fix any build errors before deploying.

---

## Lesson 2: Deploy to Vercel

### Why Vercel?

- Created by Next.js team
- Zero configuration
- Automatic CI/CD
- Free tier available
- Edge network
- Analytics

### Method 1: GitHub Integration

```bash
# 1. Push your code to GitHub
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/username/my-app.git
git push -u origin main
```

Then:

1. Go to [vercel.com](https://vercel.com)
2. Sign up with GitHub
3. Click "Import Project"
4. Select your repository
5. Click "Deploy"

### Method 2: Vercel CLI

```bash
# Install Vercel CLI
npm i -g vercel

# Login
vercel login

# Deploy
vercel

# Follow the prompts
```

### Automatic Deployments

- Every push to `main` → Production deploy
- Every push to other branches → Preview deploy
- Each PR gets its own preview URL

---

## Lesson 3: Environment Variables

### Local Development

```bash
# .env.local (DO NOT commit this file)
DATABASE_URL=mongodb://localhost:27017/myapp
API_KEY=your-secret-key
NEXT_PUBLIC_API_URL=http://localhost:3000/api
```

### Naming Convention

```
NEXT_PUBLIC_*  → Available in browser (be careful!)
Other          → Server-only (secure)
```

### In Vercel Dashboard

1. Go to your project
2. Settings → Environment Variables
3. Add each variable
4. Choose environments (Production, Preview, Development)

### Using Environment Variables

```jsx
// Server-side (API routes, Server Components)
const dbUrl = process.env.DATABASE_URL;

// Client-side (only NEXT_PUBLIC_ prefix)
const apiUrl = process.env.NEXT_PUBLIC_API_URL;
```

---

## Lesson 4: Alternative Platforms

### Netlify

```bash
# Install Netlify CLI
npm i -g netlify-cli

# Login
netlify login

# Deploy
netlify deploy --prod
```

Create `netlify.toml`:

```toml
[build]
  command = "npm run build"
  publish = ".next"

[[plugins]]
  package = "@netlify/plugin-nextjs"
```

### Railway

1. Go to [railway.app](https://railway.app)
2. Connect GitHub
3. Select repository
4. Railway auto-detects Next.js

### Docker

```dockerfile
# Dockerfile
FROM node:18-alpine AS base

FROM base AS deps
WORKDIR /app
COPY package*.json ./
RUN npm ci

FROM base AS builder
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .
RUN npm run build

FROM base AS runner
WORKDIR /app
ENV NODE_ENV production

COPY --from=builder /app/public ./public
COPY --from=builder /app/.next/standalone ./
COPY --from=builder /app/.next/static ./.next/static

EXPOSE 3000
CMD ["node", "server.js"]
```

```bash
docker build -t my-app .
docker run -p 3000:3000 my-app
```

---

## Lesson 5: Custom Domain

### In Vercel

1. Go to project Settings → Domains
2. Add your domain (e.g., `myapp.com`)
3. Add DNS records at your registrar:
   - A record: `76.76.21.21`
   - CNAME for www: `cname.vercel-dns.com`
4. Wait for SSL certificate (automatic)

### With Subdomain

- `app.yourdomain.com` → Your Next.js app
- CNAME record pointing to `cname.vercel-dns.com`

---

## Lesson 6: Optimization

### Image Optimization

```jsx
import Image from 'next/image';

export default function Hero() {
  return (
    <Image
      src="/hero.jpg"
      alt="Hero image"
      width={1200}
      height={600}
      priority  // Load immediately
      placeholder="blur"  // Show blur while loading
      blurDataURL="..."   // Base64 blur image
    />
  );
}
```

### Font Optimization

```jsx
// app/layout.js
import { Inter } from 'next/font/google';

const inter = Inter({ subsets: ['latin'] });

export default function RootLayout({ children }) {
  return (
    <html lang="en" className={inter.className}>
      <body>{children}</body>
    </html>
  );
}
```

### Bundle Analysis

```bash
# Install analyzer
npm install @next/bundle-analyzer

# next.config.js
const withBundleAnalyzer = require('@next/bundle-analyzer')({
  enabled: process.env.ANALYZE === 'true',
});

module.exports = withBundleAnalyzer({
  // your config
});

# Run analysis
ANALYZE=true npm run build
```

---

## Lesson 7: Monitoring & Analytics

### Vercel Analytics

```jsx
// app/layout.js
import { Analytics } from '@vercel/analytics/react';

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        {children}
        <Analytics />
      </body>
    </html>
  );
}
```

### Vercel Speed Insights

```jsx
import { SpeedInsights } from '@vercel/speed-insights/next';

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        {children}
        <SpeedInsights />
      </body>
    </html>
  );
}
```

### Error Monitoring

Consider services like:

- Sentry
- LogRocket
- Bugsnag

```bash
npm install @sentry/nextjs
npx @sentry/wizard@latest -i nextjs
```

---

## 🧪 Self-Check Exercises

### Exercise 1: Local Build

Run `npm run build` and fix any errors.

### Exercise 2: Deploy to Vercel

Deploy your Next.js app to Vercel via GitHub.

### Exercise 3: Environment Variables

Set up environment variables in Vercel.

### Exercise 4: Custom Domain

Configure a custom domain (or subdomain).

### Exercise 5: Analytics

Add Vercel Analytics to your app.

---

## 📝 Module Summary

| Topic | Key Points |
|-------|------------|
| **Vercel** | Best for Next.js, zero config |
| **Env Vars** | `NEXT_PUBLIC_` for client |
| **Domains** | Add in Vercel, configure DNS |
| **Optimization** | Images, fonts, bundles |
| **Monitoring** | Analytics, Speed Insights |

**Deployment Commands:**

```bash
npm run build     # Build locally
vercel            # Deploy to Vercel
vercel --prod     # Deploy to production
```

---

## 🎯 Next Steps

**Coming Next**: Module 06 - Project: E-commerce Store

*You will build a complete full-stack application!*

---

<div align="center">

**Your app is live!** 🌐

*From localhost to the world.*

</div>
