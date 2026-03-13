# ChatterBox — Realtime Chat App

A fullstack realtime chat app built with the MERN stack and Socket.io.

Users can sign up, log in, send text/image messages in real-time, see who's online, update their profile pic, and switch between 32 UI themes.

## Tech Stack

**Frontend:** React, Vite, TailwindCSS, DaisyUI, Zustand, Axios, Socket.io-client

**Backend:** Node.js, Express, MongoDB (Mongoose), Socket.io, JWT, bcrypt, Cloudinary

## Features

- JWT auth with HTTP-only cookies
- Realtime messaging with Socket.io
- Online/offline user tracking
- Image uploads via Cloudinary
- Profile picture update
- 32 switchable DaisyUI themes
- Responsive UI

## How it works

- Users authenticate via JWT stored in cookies. Passwords are hashed with bcrypt.
- Messages are stored in MongoDB. When you send a message, it's saved to the DB and also pushed to the receiver in real-time through Socket.io.
- Online status is tracked by mapping `userId → socketId` on the server. When someone connects or disconnects, the updated list is broadcasted to all clients.
- Images (profile pics + chat attachments) are converted to base64 on the client, sent to the backend, uploaded to Cloudinary, and the URL is stored in the DB.

## Setup

1. Clone the repo
2. Create `backend/.env`:
```
MONGO_URI=your_mongodb_uri
PORT=5001
JWT_SECRET=your_secret
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_key
CLOUDINARY_API_SECRET=your_secret
NODE_ENV=development
```
3. Install deps and run:
```bash
npm install --prefix backend
npm install --prefix frontend

# run backend
npm run dev --prefix backend

# run frontend
npm run dev --prefix frontend
```

Backend runs on `localhost:5001`, frontend on `localhost:5173`.

## Build for production

```bash
npm run build
npm start
```

This builds the React app and serves it from Express.

## Acknowledgements

Built as a code-along from a YouTube tutorial to learn fullstack development with MERN + Socket.io.
