📸 Simple Social — Media Sharing Platform

A full-stack media sharing application built with FastAPI, Streamlit, JWT authentication, and ImageKit for scalable media storage and delivery.

Users can register, authenticate, upload images/videos, and view a personalized feed — all backed by an async database and modern API design.

🚀 Features
🔐 Authentication & Authorization

JWT-based authentication using FastAPI Users

Secure login, signup, password reset, and email verification

Protected routes with current active user dependency

Authorization checks (users can delete only their own posts)

📤 Media Upload (ImageKit Integration)

Upload images & videos via API

Files stored on ImageKit CDN (no local media storage)

Automatic media type detection (image vs video)

Optimized delivery through ImageKit URLs

Supports large files without blocking the server

📰 Feed System

Chronological feed ordered by creation time

Displays:

Media (image / video)

Caption

Author email

Creation date

Ownership awareness (is_owner)

Real-time delete support for post owners

🎨 Frontend (Streamlit)

Clean, responsive UI

JWT-aware session handling

Media rendering based on file type:

st.image() for images

st.video() for videos

ImageKit on-the-fly transformations

Caption overlays

Uniform sizing

Sidebar navigation (Feed / Upload / Logout)

🗄️ Database & Backend

Async SQLAlchemy with SQLite (easy to swap to Postgres)

Proper relational models:

User

Post (linked via user_id)

Automatic DB initialization on app startup

Clean separation of concerns (auth, media, feed)

🧱 Tech Stack
Layer	Technology
Backend API	FastAPI
Auth	FastAPI Users (JWT)
Media CDN	ImageKit
Database	SQLite + SQLAlchemy (Async)
Frontend	Streamlit
HTTP Client	Requests
Runtime	Python 3.13
📁 Project Structure
app/
├── app.py            # Main FastAPI app
├── db.py             # Database models & session
├── images.py         # ImageKit client setup
├── users.py          # Auth & user logic
├── schemas.py        # Pydantic schemas
frontend/
├── streamlit_app.py  # Streamlit UI

🔑 Environment Variables

Create a .env file:

IMAGEKIT_PUBLIC_KEY=your_public_key
IMAGEKIT_PRIVATE_KEY=your_private_key
IMAGEKIT_URL=https://ik.imagekit.io/your_id

SECRET=jwt_secret_key

▶️ Running the App
Backend
uvicorn app.app:app --reload

Frontend
streamlit run frontend/streamlit_app.py

🧠 Design Highlights

No media stored on server → scalable by default

Async everywhere → non-blocking uploads & queries

JWT-protected API → secure by design

CDN-backed delivery → fast media loading

Clear ownership model → safe deletes

Extensible architecture → ready for likes, comments, follows

📌 Future Enhancements

Likes & comments

Pagination / infinite scroll

Post reactions

User profiles

Cloud database (PostgreSQL)

Caching & rate limiting

👨‍💻 Author

Built with ❤️ by Adarsh Rai
