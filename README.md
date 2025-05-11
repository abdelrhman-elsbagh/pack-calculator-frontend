# 🌐 Pack Calculator Frontend

This is the frontend for the Pack Calculator app, built with **Vue 3** and **Vite**.  
It allows users to input the number of items and available pack sizes, then displays the optimal pack breakdown returned by the API.

---

## 🚀 Features

- Built with Vue 3 + Vite
- Connects to a Go-based backend API
- Responsive and simple UI
- Axios for HTTP requests
- Docker-ready for production deployment

---

## ⚙️ Setup & Development

### 1. Install dependencies

```bash
npm install
```

### 2. Run locally (for development)

```bash
npm run dev
```

The app will be available at:  
`http://localhost:5173`

Make sure the backend API is running at:  
`http://localhost:8080`

---

## 🐳 Docker (Production Mode)

Before building, make sure your `.env.production` file exists and contains the correct backend URL:

```env
VITE_API_URL=http://54.91.1.171:8080
```

### Build and run:

```bash
docker rm -f pack-frontend
docker build -t pack-frontend --build-arg BUILD_ENV=production .
docker run -d -p 80:80 --name pack-frontend pack-frontend
```

The app will be live at:  
🔗 `http://54.91.1.171/`

---

## 📁 Project Structure

```
src/
├── components/       # Vue components (e.g., CalculatorForm.vue)
├── views/            # Optional views (e.g., DocsView.vue)
├── App.vue           # Root component
├── main.js           # App entry point

public/
├── openapi.yaml      # OpenAPI spec
├── docs/
│   ├── index.html    # Redoc viewer
│   └── redoc.standalone.js
```

---

## 🌐 Connect to API

Make sure Axios connects to the correct backend endpoint.

### In production:
```js
VITE_API_URL=http://54.91.1.171:8080
```

---

## 📘 API Documentation

API docs are available at:  
[`http://54.91.1.171/docs/index.html`](http://54.91.1.171/docs/index.html)

---

## 🧑‍💻 Author

Made by **Abdelrahman Tarek** using Vue 3 and Vite.