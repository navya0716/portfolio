# Navya Sharma — Portfolio Website

A full-stack personal portfolio with a Node.js/Express backend and dark glassmorphism frontend.

---

## 📁 Project Structure

```
navya-portfolio/
├── backend/
│   ├── routes/
│   │   ├── contact.js      # POST /api/contact — contact form + email
│   │   ├── projects.js     # GET  /api/projects — project data
│   │   └── skills.js       # GET  /api/skills   — skills data
│   ├── utils/
│   │   └── mailer.js       # Nodemailer email utility
│   ├── server.js           # Express app entry point
│   ├── .env.example        # Environment variable template
│   └── package.json
└── frontend/
    └── index.html          # Single-page portfolio (served by Express)
```

---

## 🚀 Quick Start (Local)

### 1. Install dependencies
```bash
cd backend
npm install
```

### 2. Configure environment
```bash
cp .env.example .env
```
Edit `.env` with your details (see Configuration section below).

### 3. Start the server
```bash
# Development (auto-restart on changes)
npm run dev

# Production
npm start
```

### 4. Open in browser
```
http://localhost:5000
```

---

## ⚙️ Configuration (.env)

| Variable       | Description                                      | Example                      |
|----------------|--------------------------------------------------|------------------------------|
| `PORT`         | Server port                                      | `5000`                       |
| `NODE_ENV`     | `development` or `production`                    | `development`                |
| `EMAIL_USER`   | Your Gmail address                               | `navya@gmail.com`            |
| `EMAIL_PASS`   | Gmail **App Password** (not your login password) | `abcd efgh ijkl mnop`        |
| `EMAIL_TO`     | Where to receive contact messages                | `navya@gmail.com`            |
| `FRONTEND_URL` | Allowed CORS origin                              | `http://localhost:5000`      |

### 🔑 Getting a Gmail App Password
1. Go to [Google Account → Security](https://myaccount.google.com/security)
2. Enable **2-Step Verification**
3. Go to **App Passwords** → Select app: Mail → Select device: Other → name it "Portfolio"
4. Copy the 16-character password into `EMAIL_PASS`

> **Note:** In development mode (`NODE_ENV=development`), if email is not configured, contact form messages are logged to the console instead of emailed — so you can test the full flow without email setup.

---

## 🔗 API Endpoints

| Method | Endpoint           | Description                  |
|--------|--------------------|------------------------------|
| GET    | `/api/health`      | Server health check          |
| POST   | `/api/contact`     | Submit contact form          |
| GET    | `/api/projects`    | Get all projects             |
| GET    | `/api/projects/:id`| Get project by ID            |
| GET    | `/api/skills`      | Get all skill categories     |
| GET    | `/api/skills/:cat` | Get skills by category slug  |

### Contact API — Request Body
```json
{
  "name":    "John Doe",
  "email":   "john@example.com",
  "subject": "Project inquiry",
  "message": "Hi Navya, I'd love to work with you..."
}
```

---

## 🌐 Deployment

### Render / Railway / Fly.io
1. Push the `backend/` folder to GitHub
2. Set environment variables in the platform dashboard
3. Build command: `npm install`
4. Start command: `npm start`

### Vercel / Netlify (frontend only)
Deploy `frontend/index.html` as a static site and update the fetch URL in the HTML to point to your deployed backend.

---

## 🛡️ Security Features

- **Helmet.js** — sets secure HTTP headers
- **CORS** — restricted to `FRONTEND_URL` origin
- **Rate limiting** — 100 req/15min globally, 5 contact submissions/hour
- **Input validation** — express-validator on all contact fields
- **Body size limit** — 10kb max JSON payload

---

## ✏️ Customization

Open `frontend/index.html` and update:
- Your **email**, **phone**, **LinkedIn URL**, **GitHub URL**
- Hero **stats** (years of experience, project count)
- **Project descriptions** in `backend/routes/projects.js`
- **Skill levels** in `backend/routes/skills.js`

---

© 2026 Navya Sharma. All Rights Reserved.
