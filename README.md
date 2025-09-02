# DevConnect

- A modern developer networking application to discover, connect, and collaborate with fellow developers.
- Connect with other developers, create/edit/delete profiles, send/accept connection requests, and manage your professional network.
- Permanent delete-account functionality that safely removes a user and all associated references across the network.

---

## ✨ Features

### Core Platform

- **Seamless user lifecycle:** Sign up, sign in, and sign out with sessions secured by **httpOnly JWT cookie (1‑day expiry)**.
- **Full profile management:** Create, edit, and **permanently delete** profiles; delete-account cleans connections and pending requests to maintain DB consistency.

### Social & Networking

- **Connection flow:** Send, receive, accept, reject or cancel connection requests with clear incoming/outgoing states.
- **Connections feed:** Discover new developers in a fast, filtered home feed showing the latest profiles.

### Security & Compliance

- **Industry-standard auth:** Passwords hashed with **bcrypt**; authentication and authorization enforced with **JWT** tokens.
- **Cookie security & CORS:** `httpOnly` cookies and CORS configured to allow secure frontend-backend communication.

### UX & Performance

- **Responsive UI:** Built with utility-first styling for a clean mobile-first interface and accessible components.
- **Lightweight API layer:** Focus on fast Express endpoints and efficient Mongoose queries for quick discovery and profile updates.

### Developer-Focused

- **Extensible architecture:** Clear separation of controllers, routes, and models for quick feature additions (avatars, notifications, search).
- **API-first design:** Simple REST contract that’s easy to test (Postman) and integrate across platforms.

---

## 🧰 Tech Stack

This project combines pragmatic frontend tooling with a secure, scalable backend. Below is a concise description of each tech and why it was chosen.

### Frontend (Client)

- **React** — Component-driven UI for fast iteration and reusable views.
- **Redux (RTK)** — Predictable global state for auth, user data and request flows.
- **React Router** — Declarative, nested routing for protected routes and clean navigation.
- **Axios** — Promise-based HTTP client with `withCredentials` to send/receive cookies securely.
- **Tailwind CSS & DaisyUI** — Utility-first styling with accessible, themeable components for rapid UI development and consistent visuals.

> The frontend code is available in the `frontend/` folder of this repo. (README focuses on usage & API; implementation files live in the repository.)

### Backend (Server)

- **Node.js + Express** — Lightweight, performant server for REST APIs and middleware pipelines (auth, CORS, cookie parsing).
- **MongoDB + Mongoose** — Flexible document DB that maps naturally to user profiles, connections, and request relationships.

**Key backend libraries & why they matter**

- **bcrypt** — Securely hash and salt passwords before saving to the DB to prevent credential leaks.
- **cookie-parser** — Parse and manage httpOnly cookies containing JWT tokens (secure session handling).
- **cors** — Controlled cross-origin requests; configured with credentials to allow cookie-based auth from the frontend.
- **jsonwebtoken (JWT)** — Stateless authentication tokens stored in secure cookies for session management (1-day expiry).
- **mongoose** — Schema-driven ODM for data validation, relations (connections/requests) and concise DB queries.
- **validator** — Validate email formats and other user inputs at the model level for data integrity.

### Recommended tooling & deployment notes

- **Development:** nodemon, dotenv for environment variables, and Postman for API testing.
- **Hosting:** Deploy backend to platforms like Render/Heroku/AWS Elastic Beanstalk; use MongoDB Atlas for managed DB.
- **CI/CD:** Add GitHub Actions for linting, tests, and automated deploys.

---

## 🔒 Security & Best Practices

- Store JWT in `httpOnly` cookies to reduce XSS risk; set `sameSite` and secure flags in production.
- Always hash passwords (bcrypt) and enforce minimal password complexity on the client side.
- Use server-side validation (validator + Mongoose schemas) to prevent malformed or malicious data.
- On account deletion, cascade cleanup of references (connections, incoming/outgoing requests) to avoid orphaned data.

---

## Contributing

This project is **open source** — contributions, issues, and pull requests are welcome. Feel free to fork the repository, submit improvements, add features (avatars, notifications, search, tests), or help improve documentation and API examples.

Please follow standard contribution practices:
- Fork the repo and create a feature branch.
- Add tests and run linters where applicable.
- Open a descriptive PR referencing the issue or feature.

Thank you — your contributions make this project better for everyone.

---

## ⚙️ Environment Variables

```bash
PORT=5000
MONGO_URI=mongodb://localhost:27017/devconnect
JWT_SECRET=your_jwt_secret_here
JWT_EXPIRES_IN=1d
COOKIE_NAME=token
FRONTEND_URL=http://localhost:3000
```

---

## ✅ How to Run

1. Start the backend (see `backend/` folder):

```bash
cd backend
npm install
cp .env.example .env
# edit .env to set MONGO_URI and JWT_SECRET
npm run dev
```

2. Start the frontend (see `frontend/` folder):

```bash
cd frontend
npm install
npm run dev
```

Open `http://localhost:3000` to use the app.

---

## 🛠️ Extending DevConnect

- Add avatar uploads (Multer → Cloudinary / S3).
- Introduce real-time notifications with Socket.io for requests/acceptances.
- Add search & filters (skills, location) and pagination on the feed.
- Add unit/integration tests for auth flows and API contracts.

---
