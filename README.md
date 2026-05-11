# Task Management Web Application

A modern, full-stack task management application built with Node.js, Express, React, and MongoDB. Features user authentication, real-time updates via WebSockets, and a responsive design for web and mobile devices.

[Live Demo](https://heet-113.github.io/Task-Management-App-Frontend/)

## 🎯 Key Features

- **User Authentication & Authorization**
  - Secure registration and login
  - JWT-based authentication
  - Password hashing with bcryptjs

- **CRUD Operations for Tasks**
  - Create new tasks
  - Read/view task details
  - Update task information (title, description, priority, due date, status)
  - Delete tasks
  - Filter tasks by status

- **Real-Time Updates**
  - WebSocket integration with Socket.io
  - Real-time task creation, updates, and deletions
  - Automatic UI synchronization across clients

- **Responsive Design**
  - Mobile-first approach
  - Responsive grid layout
  - Touch-friendly interface
  - Works seamlessly on desktop, tablet, and mobile devices

- **Task Management Features**
  - Priority levels (Low, Medium, High)
  - Task status tracking (To Do, In Progress, Completed)
  - Due date management
  - Task descriptions
  - Task statistics dashboard

## 🛠 Tech Stack

### Backend
- **Node.js** - JavaScript runtime
- **Express** - Web framework
- **MongoDB** - NoSQL database
- **Persistence** - JSON file storage (file-based, no external DB)
- **Socket.io** - Real-time communication
- **JWT** - Authentication
- **bcryptjs** - Password hashing

### Frontend
- **React** - UI library
- **React Router** - Client-side routing
- **Axios** - HTTP client
- **Socket.io-client** - WebSocket client
- **CSS3** - Styling with media queries for responsiveness

## 📋 Project Structure

```
Task-Management-App/
├── backend/
│   ├── models/
│   │   ├── User.js
│   │   └── Task.js
│   ├── controllers/
│   │   ├── authController.js
│   │   └── taskController.js
│   ├── routes/
│   │   ├── auth.js
│   │   └── tasks.js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── errorHandler.js
│   ├── config/
│   │   └── database.js
│   ├── server.js
│   ├── package.json
│   ├── .env.example
│   └── .gitignore
│
└── frontend/
    ├── public/
    │   └── index.html
    ├── src/
    │   ├── components/
    │   │   ├── Navigation.js
    │   │   ├── Navigation.css
    │   │   ├── PrivateRoute.js
    │   │   ├── TaskItem.js
    │   │   ├── TaskItem.css
    │   │   ├── TaskForm.js
    │   │   └── TaskForm.css
    │   ├── pages/
    │   │   ├── Login.js
    │   │   ├── Register.js
    │   │   ├── Dashboard.js
    │   │   └── AuthPages.css
    │   │   └── Dashboard.css
    │   ├── context/
    │   │   ├── AuthContext.js
    │   │   └── TaskContext.js
    │   ├── utils/
    │   │   ├── api.js
    │   │   └── socket.js
    │   ├── App.js
    │   ├── App.css
    │   ├── index.js
    │   └── index.css
    ├── package.json
    ├── .gitignore
    └── public/index.html
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- MongoDB (local or MongoDB Atlas)

### Backend Setup

1. **Navigate to backend directory:**
   ```bash
   cd backend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Create `.env` file:**
   ```bash
   cp .env.example .env
   ```

4. **Update `.env` with your configuration:**
   ```
   MONGODB_URI=mongodb://localhost:27017/task-management
   JWT_SECRET=your_secret_key_here
   PORT=5000
   NODE_ENV=development
   CLIENT_URL=http://localhost:3000
   ```

5. **Start MongoDB:**
   - If using local MongoDB:
     ```bash
     mongod
     ```
   - Or update `MONGODB_URI` to use MongoDB Atlas

6. **Start the backend server:**
   ```bash
   npm run dev
   ```

   Server will run at `http://localhost:5000`

### Frontend Setup

1. **Navigate to frontend directory:**
   ```bash
   cd frontend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Create `.env.local` (optional, if backend is on different URL):**
   ```
   REACT_APP_API_URL=http://localhost:5000/api
   REACT_APP_SOCKET_URL=http://localhost:5000
   ```

4. **Start the development server:**
   ```bash
   npm start
   ```

   Application will open at `http://localhost:3000`

## 🔑 API Endpoints

### Authentication Routes (`/api/auth`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|----------------|
| POST | `/register` | Register new user | No |
| POST | `/login` | Login user | No |
| GET | `/me` | Get current user | Yes |

### Task Routes (`/api/tasks`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|----------------|
| GET | `/` | Get all user's tasks | Yes |
| GET | `/:id` | Get specific task | Yes |
| POST | `/` | Create new task | Yes |
| PUT | `/:id` | Update task | Yes |
| DELETE | `/:id` | Delete task | Yes |

## 📱 Responsive Breakpoints

- **Mobile (< 768px)** - Optimized for smartphones
- **Tablet (768px - 1024px)** - Optimized for tablets
- **Desktop (> 1024px)** - Full desktop experience

## 🔐 Authentication Flow

1. User registers with username, email, and password
2. Password is hashed using bcryptjs
3. User logs in with email and password
4. Server generates JWT token
5. Token is stored in localStorage and sent with subsequent requests
6. Protected routes verify token validity

## 🔄 Real-Time Updates via WebSocket

- When a task is created, updated, or deleted, Socket.io broadcasts the event
- All connected clients of that user receive real-time updates
- No page refresh needed for changes to appear

## 🛡️ Security Features

- Password hashing with bcryptjs (10 salt rounds)
- JWT-based authentication with 7-day expiration
- Protected API routes requiring valid JWT token
- CORS configuration for secure cross-origin requests
- User can only access/modify their own tasks

## 🚢 Deployment

### Backend Deployment (Heroku/Railway)

1. Create account on hosting platform
2. Connect GitHub repository
3. Set environment variables in platform dashboard
4. Deploy from main branch

### Frontend Deployment (Vercel/Netlify)

1. Build the frontend:
   ```bash
   npm run build
   ```

2. Deploy the `build/` folder to:
   - Vercel (recommended for React apps)
   - Netlify
   - Any static hosting service

3. Update API URLs in `.env.local` to point to deployed backend

## 📝 Sample Credentials for Testing

After running the application:

1. Click "Register" to create a new account
2. Fill in username, email, and password
3. Click "Sign Up"
4. Log in with your credentials
5. Create and manage tasks

## 🐛 Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running
- Verify `MONGODB_URI` in `.env`
- Check if using MongoDB Atlas - ensure IP is whitelisted

### CORS Error
- Verify `CLIENT_URL` matches your frontend URL
- Check backend is running on correct port

### WebSocket Connection Issues
- Ensure Socket.io is properly initialized
- Check if backend and frontend are on same/accessible URLs

## 📚 Additional Resources

- [Express.js Documentation](https://expressjs.com/)
- [React Documentation](https://react.dev/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [Socket.io Documentation](https://socket.io/docs/)
- [JWT Documentation](https://jwt.io/)

## 📄 License

This project is open source and available under the MIT License.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

**Happy task managing! 🎉**
