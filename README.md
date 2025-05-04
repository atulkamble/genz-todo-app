**Gen-Z-style GitHub Actions project** setup with all the ✨vibes✨ — Dockerized app, auto-builds, deploy-ready, and lit CI/CD via GitHub Actions. Let’s go! 🔥

---

## 📁 Project: `genz-todo-app`

> A super chill full-stack TODO app for Gen-Z devs. ReactJS + Node.js + MongoDB 🍃 + Docker + GitHub Actions = 💯

---

### 🔧 Tech Stack

* ⚛️ ReactJS (Frontend)
* 🐢 Node.js + Express (Backend)
* 🍃 MongoDB (DB)
* 🐳 Docker
* 🛠️ GitHub Actions

---

## 💡 Folder Structure

```bash
genz-todo-app/
├── .github/
│   └── workflows/
│       └── ci-cd.yml
├── backend/
│   ├── Dockerfile
│   └── index.js
├── frontend/
│   ├── Dockerfile
│   └── App.js
├── docker-compose.yml
└── README.md
```

---

### 🔥 `ci-cd.yml` – GitHub Actions Workflow

📁 `.github/workflows/ci-cd.yml`

```yaml
name: CI/CD 🚀

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: 📥 Checkout repo
        uses: actions/checkout@v3

      - name: 🐳 Set up Docker
        uses: docker/setup-buildx-action@v2

      - name: 🔨 Build Backend Image
        run: docker build -t backend:latest ./backend

      - name: 🔨 Build Frontend Image
        run: docker build -t frontend:latest ./frontend

      - name: ✅ Verify Images
        run: docker images
```

---

### 🐳 Dockerfile (Backend)

📁 `backend/Dockerfile`

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 5000
CMD ["node", "index.js"]
```

---

### 🐳 Dockerfile (Frontend)

📁 `frontend/Dockerfile`

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install && npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

---

### 🧱 docker-compose.yml

```yaml
version: "3.9"

services:
  backend:
    build: ./backend
    ports:
      - "5000:5000"

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
```

---

### 🧠 Example Node Backend (`index.js`)

```js
const express = require("express");
const app = express();
app.get("/", (req, res) => res.send("👋 Hello from Gen-Z Backend!"));
app.listen(5000, () => console.log("🟢 Server on http://localhost:5000"));
```

---

### ⚛️ React Frontend Snippet (`App.js`)

```jsx
function App() {
  return (
    <div style={{ textAlign: "center", marginTop: "2rem" }}>
      <h1>✅ TODOs for Gen-Z</h1>
      <p>React + Docker + GitHub Actions = 💖</p>
    </div>
  );
}
export default App;
```

---
