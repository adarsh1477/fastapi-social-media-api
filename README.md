# 📸 Simple Social — Media Sharing Platform

_A full-stack social media application built with FastAPI, Streamlit, JWT authentication, ImageKit CDN integration, and an async database architecture._

---

## 👥 Project Info
**Personal Full-Stack Project**  
**Developer:** Adarsh Rai

---

## 📋 Table of Contents
- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Architecture](#architecture)
- [Key Technologies](#key-technologies)
- [Core Features](#core-features)
- [API Endpoints](#api-endpoints)
- [How it Works](#how-it-works)
- [Security](#security)
- [Results](#results)
- [Future Enhancements](#future-enhancements)

---

## 📝 Overview
Simple Social is a cloud-ready media sharing platform that allows authenticated users to upload images and videos, view a personalized feed, and manage their own posts.  
The system uses **ImageKit** for scalable media storage and delivery, **JWT-based authentication**, and a **fully async backend** for high performance.

---

## 🎯 Problem Statement
Traditional social media prototypes often:
- Store media locally (poor scalability)
- Lack proper authentication and authorization
- Block servers during large uploads
- Mix frontend and backend responsibilities

Simple Social solves these problems using a **CDN-first architecture**, **JWT auth**, and **async microservice-style APIs**.

---

## 🏛️ Architecture
1. User authenticates via JWT (FastAPI Users).
2. Media is uploaded via FastAPI and streamed to ImageKit.
3. Media metadata is stored in the database.
4. Feed data is served via protected APIs.
5. Streamlit frontend consumes APIs and renders media dynamically.

_**(Attach architecture diagram here)**_

---

## 🛠️ Key Technologies
- **FastAPI** — Async backend & REST APIs  
- **FastAPI Users** — JWT authentication & user management  
- **ImageKit** — Media CDN, storage & transformations  
- **Streamlit** — Frontend UI  
- **SQLAlchemy (Async)** — Database ORM  
- **SQLite** — Development database (Postgres-ready)  
- **JWT** — Secure API access  

---

## ✨ Core Features

### 🔐 Authentication & Authorization
- JWT-based login & registration
- Password reset & email verification
- Protected routes with `current_active_user`
- Ownership-based access control (delete only your posts)

---

### 📤 Media Upload (ImageKit Integration)
- Supports **images & videos**
- No local media storage
- Automatic file-type detection
- CDN-optimized delivery via ImageKit URLs
- Handles large files efficiently

---

### 📰 Feed System
- Chronological feed (latest first)
- Displays:
  - Media (image / video)
  - Caption
  - Author email
  - Timestamp
- Ownership flag (`is_owner`)
- Secure delete functionality

---

### 🎨 Frontend (Streamlit)
- Clean, responsive UI
- JWT-aware session handling
- Media rendering by type:
  - `st.image()` for images
  - `st.video()` for videos
- ImageKit transformations:
  - Caption overlays
  - Uniform sizing
- Sidebar navigation (Feed / Upload / Logout)

---

## 🌐 API Endpoints

| Method | Endpoint | Purpose |
|------|---------|--------|
| POST | `/auth/jwt/login` | Login & obtain JWT |
| POST | `/auth/register` | User registration |
| GET | `/users/me` | Get current user |
| POST | `/upload` | Upload image/video |
| GET | `/feed` | Fetch feed posts |
| DELETE | `/post/{post_id}` | Delete user’s post |

---

## 🔎 How it Works

**1️⃣ Authentication**  
User logs in → receives JWT → stored in frontend session.

**2️⃣ Upload Media**  
Frontend sends multipart upload → FastAPI streams file → ImageKit stores media.

**3️⃣ Save Metadata**  
Post metadata (URL, caption, user_id) saved to DB.

**4️⃣ Feed Retrieval**  
Backend joins posts + users → returns enriched feed.

**5️⃣ Media Rendering**  
Frontend renders media using correct component (`image` / `video`).

---

## 🔐 Security
- JWT-based protected endpoints
- Role-aware user access
- Ownership checks for destructive actions
- No public write access to media storage
- Tokens never exposed in URLs

---

## 📊 Results
- Handles image & video uploads reliably
- Zero server-side media storage
- Fast media loading via CDN
- Clean separation of frontend & backend
- Fully async, non-blocking API design

---

## 🚀 Future Enhancements
- Likes & comments
- Pagination / infinite scroll
- User profiles
- Cloud database (PostgreSQL)
- Rate limiting & caching
- Media compression presets
- Follow / unfollow system

---

## 👨‍💻 Author
Built with ❤️ by **Adarsh Rai**
