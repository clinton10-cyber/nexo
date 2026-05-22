# Nexarion Zone 🛒

A full-stack e-commerce store built with Flask + SQLAlchemy.  
Dark luxury aesthetic. Admin panel. WhatsApp/Phone/Email ordering. Auto user accounts.

---

## 🚀 Deploy to Render (5 minutes)

### Option A — render.yaml (easiest)
1. Push this folder to a GitHub repo
2. Go to [render.com](https://render.com) → New → Blueprint
3. Connect your repo → Render reads `render.yaml` automatically
4. Click **Apply** — done!

### Option B — Manual
1. Go to Render → New → Web Service
2. Connect your GitHub repo
3. Set:
   - **Environment:** Python
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `gunicorn app:app --workers 2 --bind 0.0.0.0:$PORT`
4. Add a **Disk** under Advanced:
   - Mount Path: `/data`
   - Size: 1 GB
5. Add Environment Variables:
   | Key | Value |
   |-----|-------|
   | `SECRET_KEY` | *(auto-generate)* |
   | `ADMIN_PASSWORD` | your-strong-password |
   | `DATABASE_URL` | `sqlite:////data/nexarion.db` |
   | `RENDER` | `true` |

### Option C — PostgreSQL (production scale)
1. Create a Render PostgreSQL database
2. Copy the **Internal Database URL**
3. Set `DATABASE_URL` to that URL (starts with `postgresql://`)
4. Remove the Disk (not needed with Postgres)

---

## 🔧 Local Development

```bash
# Install dependencies
pip install -r requirements.txt

# Run dev server
python app.py
# Visit: http://localhost:5000
```

---

## 🔑 Admin Panel

- URL: `yoursite.com` → click **Admin** in navbar
- Default password: **nexarion2024**
- Change via `ADMIN_PASSWORD` env var on Render

### Admin features:
- ✅ Add / Edit / Delete products
- ✅ Edit site name, tagline, phone, WhatsApp, address, email, theme colour
- ✅ View all user carts in real time
- ✅ Store stats (users, products, potential revenue)

---

## 👤 Customer Features

- Auto account on first visit (name prompt)
- Browse products with search & category filter
- Add to cart, adjust quantities
- Order via **WhatsApp**, **Phone call**, or **Email**
- View product details

---

## 📁 Project Structure

```
nexarion-zone/
├── app.py              ← Flask backend (all routes + models)
├── requirements.txt    ← Python dependencies
├── render.yaml         ← Render deployment config
├── README.md           ← This file
└── templates/
    └── index.html      ← Full frontend SPA (vanilla JS)
```

---

## 🌍 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `SECRET_KEY` | auto | Flask session secret |
| `ADMIN_PASSWORD` | `nexarion2024` | Admin login password |
| `DATABASE_URL` | `sqlite:///nexarion.db` | Database connection string |
| `RENDER` | — | Set to `true` on Render for secure cookies |
| `FLASK_DEBUG` | `0` | Set to `1` for debug mode |
| `ALLOWED_ORIGINS` | `*` | Comma-separated CORS origins |

---

## 📞 Contact Buttons Setup

Update via Admin → Settings:
- **WhatsApp:** full number with country code, no spaces (e.g. `+2348012345678`)
- **Phone:** display format (e.g. `+234 801 234 5678`)
- **Email:** your Gmail or any email address
