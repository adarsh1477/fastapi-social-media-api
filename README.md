📸 Simple Social — Media Sharing Platform

A full-stack media sharing application built with FastAPI, Streamlit, JWT authentication, and ImageKit for scalable media storage and delivery.

Users can register, authenticate, upload images/videos, and view a personalized feed — all backed by an async database and modern API design.

🚀 Features
🔐 Authentication & Authorization

JWT-based authentication using FastAPI Users

Secure login, signup, password reset, and email verification

Protected routes using current_active_user

Authorization checks (users can delete only their own posts)

📤 Media Upload (ImageKit Integration)

Upload images & videos via FastAPI

Files stored on ImageKit CDN (no local storage)

Automatic media-type detection (image vs video)

Optimized delivery using ImageKit URLs

Supports large uploads without blocking the server

📰 Feed System

Chronological feed ordered by creation date

Displays:

Media (image / video)

Caption

Author email

Timestamp

Ownership awareness (is_owner)

Secure delete support for post owners

🎨 Frontend (Streamlit)

Clean, responsive UI

JWT-aware session handling

Media rendering by file type:

st.image() for images

st.video() for videos

ImageKit on-the-fly transformations

Caption overlays

Uniform sizing & padding

Sidebar navigation (Feed / Upload / Logout)

🗄️ Database & Backend

Async SQLAlchemy with SQLite (easily swappable to Postgres)

Relational models:

User

Post (linked via user_id)

Automatic DB initialization on startup

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
├── app.py            # Main FastAPI application
├── db.py             # Database models & session
├── images.py         # ImageKit client setup
├── users.py          # Authentication logic
├── schemas.py        # Pydantic schemas

frontend/
├── streamlit_app.py  # Streamlit UI

🔑 Environment Variables

Create a .env file in the project root:

IMAGEKIT_PUBLIC_KEY=your_public_key
IMAGEKIT_PRIVATE_KEY=your_private_key
IMAGEKIT_URL=https://ik.imagekit.io/your_id

SECRET=your_jwt_secret

▶️ Running the App
Backend
uvicorn app.app:app --reload

Frontend
streamlit run frontend/streamlit_app.py

🧠 Design Highlights

No server-side media storage → CDN-first architecture

Fully async backend → high performance

JWT-protected API → secure access

Optimized media delivery via ImageKit

Ownership-aware operations → safe deletes

Extensible design → ready for future features

📌 Future Enhancements

Likes & comments

Pagination / infinite scroll

User profiles

Cloud database (PostgreSQL)

Rate limiting & caching

👨‍💻 Author

Built with ❤️ by Adarsh Rai
