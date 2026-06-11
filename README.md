# 🏠 ProRoof Kenya – Roofing Quotation PWA

A complete Progressive Web App for roofing service quotation management.

**Developer:** Daniel Ochieng Oketch  
**Live App:** https://roofing-pwa.vercel.app  
**API:** https://roofing-pwa.onrender.com/api/health

---

## Tech Stack

**Backend:** Node.js · Express · MongoDB (Mongoose)  
**Frontend:** React 18 · React Router v6 · jsPDF · IndexedDB  
**Storage:** MongoDB Atlas (database) · Cloudinary (images)  
**Hosting:** Vercel (frontend) · Render (backend)

---

## Project Structure

```
roofing-pwa/
├── backend/          # Node.js + Express + MongoDB API
└── frontend/         # React PWA
```

---

## ⚡ Quick Start (Local Development)

### Prerequisites

- Node.js 18+
- MongoDB (local or Atlas)
- Cloudinary account (free at cloudinary.com)

### 1. Clone and install

```bash
git clone https://github.com/YOUR_USERNAME/roofing-pwa.git
cd roofing-pwa
npm install && npm run install:all
```

### 2. Configure backend environment

```bash
cd backend
cp .env.example .env
```

Edit `.env` with your values:

```env
PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb://localhost:27017/roofing_pwa
JWT_SECRET=your-long-random-secret-here
JWT_EXPIRES_IN=7d
FRONTEND_URL=http://localhost:3000

# Cloudinary — get from cloudinary.com dashboard
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

### 3. Seed the database

```bash
npm run seed --prefix backend
```

This creates:

- 47 Kenyan counties
- Common roofing units (m², lm, pcs, sht, etc.)
- Admin user → `admin@proroofkenya.co.ke` / `admin1234`

> ⚠️ Change the admin password immediately after first login.

### 4. Start both apps

```bash
npm run dev
```

- **Website** → http://localhost:3000
- **API** → http://localhost:5000/api/health

---

## 🌍 Production Environment Variables

### Render (Backend)

| Key                     | Value                                |
| ----------------------- | ------------------------------------ |
| `MONGODB_URI`           | Your MongoDB Atlas connection string |
| `JWT_SECRET`            | Long random secret string            |
| `JWT_EXPIRES_IN`        | `7d`                                 |
| `NODE_ENV`              | `production`                         |
| `FRONTEND_URL`          | `https://roofing-pwa.vercel.app`     |
| `CLOUDINARY_CLOUD_NAME` | From Cloudinary dashboard            |
| `CLOUDINARY_API_KEY`    | From Cloudinary dashboard            |
| `CLOUDINARY_API_SECRET` | From Cloudinary dashboard            |

### Vercel (Frontend)

| Key                 | Value                                  |
| ------------------- | -------------------------------------- |
| `REACT_APP_API_URL` | `https://roofing-pwa.onrender.com/api` |

---

## 🔑 Features

### Public Website

- **Home** – hero, features, stats, CTA
- **About** – company story, values, why choose us
- **Projects** – portfolio grid (populated from dashboard)
- **Contact** – real contact details with Call, Email and WhatsApp buttons

### Staff Dashboard (login required)

| Page       | Description                                             |
| ---------- | ------------------------------------------------------- |
| Dashboard  | Summary stats + recent quotations                       |
| Quotations | Create, edit, view, print, share via PDF/WhatsApp/Email |
| Clients    | Client database with county                             |
| Units      | Measurement units (name + symbol shown on PDF)          |
| Counties   | Kenyan counties for dropdowns                           |
| Projects   | Portfolio with Cloudinary photo upload                  |
| Account    | Business details, logo, users, password                 |

### Quotation PDF

- Auto-generated in browser using jsPDF (no server needed)
- Business details + logo top-right
- Client details top-left
- Itemised table with description, qty, unit symbol, unit price, total
- Whitespace and indentation preserved exactly as typed
- Subtotal in KES
- Notes, signature blocks, footer
- Download as PDF, share via WhatsApp or Email

### Offline Mode (PWA)

- Installable on mobile (Add to Home Screen)
- All data cached in IndexedDB
- Works fully offline
- Auto-syncs when back online via Background Sync API
- Sync status indicator in dashboard topbar

---

## 📱 Installing on Mobile

1. Open https://roofing-pwa.vercel.app in Chrome (Android) or Safari (iOS)
2. Tap browser menu → **Add to Home Screen**
3. App installs and works offline

---

## 🗂 API Endpoints

| Method  | Path                       | Description                       |
| ------- | -------------------------- | --------------------------------- |
| GET     | `/api/health`              | Health check                      |
| POST    | `/api/auth/login`          | Login → JWT                       |
| GET     | `/api/auth/me`             | Current user                      |
| GET/PUT | `/api/business`            | Business settings                 |
| POST    | `/api/business/logo`       | Upload logo (Cloudinary)          |
| CRUD    | `/api/clients`             | Client management                 |
| CRUD    | `/api/quotations`          | Quotation management              |
| CRUD    | `/api/units`               | Unit management                   |
| CRUD    | `/api/counties`            | County management                 |
| CRUD    | `/api/projects`            | Project management                |
| POST    | `/api/projects/:id/images` | Upload project photo (Cloudinary) |
| GET     | `/api/sync/pull`           | Pull changed data for offline     |
| POST    | `/api/sync/push`           | Push offline data to server       |

---

## 🚀 Deployment

See **DEPLOYMENT.md** for the full step-by-step guide covering:

- MongoDB Atlas setup
- GitHub repository
- Render (backend) deployment
- Vercel (frontend) deployment
- Custom domain + HTTPS
- CI/CD with GitHub Actions

### Quick deploy after changes

```bash
git add .
git commit -m "Describe your change"
git push
# Vercel and Render auto-deploy in ~2 minutes
```

---

## 💰 Hosting Cost

| Service       | Plan                    | Cost            |
| ------------- | ----------------------- | --------------- |
| GitHub        | Free                    | KES 0           |
| Vercel        | Hobby (100GB/month)     | KES 0           |
| Render        | Free (sleeps when idle) | KES 0           |
| MongoDB Atlas | M0 (512MB)              | KES 0           |
| Cloudinary    | Free (25GB storage)     | KES 0           |
| **Total**     |                         | **KES 0/month** |

---

## 📞 https://www.linkedin.com/in/ochieng-daniel

_Built by Daniel Ochieng Oketch · KES currency · 47 Kenyan counties_

---
