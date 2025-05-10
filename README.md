
# 🌐 Pack Calculator Frontend

This is the frontend for the Pack Calculator app, built with **Vue 3** and **Vite**.  
It allows users to input the number of items and available pack sizes, then displays the optimal pack breakdown returned by the API.

---

## 🚀 Features

- Built with Vue 3 + Vite
- Connects to a Go-based backend API
- Responsive and simple UI
- Axios for HTTP requests
- Docker-ready

---

## ⚙️ Setup & Development

### 1. Install dependencies

```bash
npm install
```

### 2. Run locally

```bash
npm run dev
```

It will be available at:  
`http://localhost:5173`

Make sure the API is running at `http://localhost:8080`

---

## 🐳 Docker Build

This project is Dockerized and ready to run in production mode.

### 1. Build and run

```bash
docker build -t pack-calculator-frontend .
docker run -p 80:80 pack-calculator-frontend
```

It will serve the built frontend at `http://localhost`

---

## 📁 Project Structure

```
src/
├── components/       # Vue components (e.g., CalculatorForm.vue)
├── assets/           # Static images or styles
├── App.vue           # Root component
├── main.js           # App entry
```

---

## 🌐 Connect to API

Make sure your Axios requests target the correct backend address.  
In development:
```js
http://localhost:8080/calculate
```

In production (Docker):
```js
http://api:8080/calculate
```

```
VITE_API_URL=http://localhost:8080
```

---

## 🧑‍💻 Author 
Made by **Abdelrahman Tarek** using Vue 3 and Vite
---