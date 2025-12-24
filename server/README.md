# TeamFlow 🚀  
**Backend for a modern team collaboration platform**

TeamFlow is a full-stack collaboration platform designed to help teams communicate, manage tasks, and work together efficiently.  
This repository contains the **backend service**, with a strong focus on **database design**, **domain modeling**, and **clean REST API architecture** inspired by real-world SaaS products.

---

## ✨ Backend Capabilities

### 👤 User Domain
- User data model prepared for secure authentication
- UUID-based primary keys
- Unique email constraint
- Timestamped records (`createdAt`, `updatedAt`)

---

### 👥 Teams
- Team creation support
- Public and private teams
- Team metadata:
  - Name
  - Description
  - Avatar
  - Banner
- Creation and update timestamps

---

### 🔐 Team Membership & Roles
- Many-to-many relationship between users and teams
- Role-based access using enums:
  - `ADMIN`
  - `MANAGER`
  - `MEMBER`
- Unique membership per user per team
- Join timestamps for auditing and history

---

### 💬 Messaging System
- Team-scoped messaging model
- Supported message types:
  - `TEXT`
  - `IMAGE`
  - `VIDEO`
  - `FILE`
- Enum-based message classification
- Sender and team relationships
- Message timestamps for ordering and history

---

### 📋 Task Management
- Team-based task model
- Optional task assignment
- Task creator tracking
- Task status managed via enum:
  - `PENDING`
  - `IN_PROGRESS`
  - `COMPLETED`
  - `CANCELLED`
- Optional deadlines
- Full task lifecycle timestamps

---

### 🔔 Notifications
- User-specific notifications
- Read/unread state tracking
- Notification types handled via enum:
  - Task assigned
  - Task updated
  - Task due
  - Message
  - Team invite
  - System
- Reference-based notifications for contextual navigation

---

## 🧩 Database Models

The backend currently defines the following Prisma models:

- `User`
- `Team`
- `TeamMember`
- `Message`
- `Task`
- `Notification`

### Design principles:
- UUID primary keys
- Strong relational integrity
- Enum-based domain constraints
- Explicit relations between entities
- Audit-friendly timestamps across all models

---

## 🛠️ Tech Stack (Backend)

### Core
- **Node.js**
- **Express.js**
- **PostgreSQL**
- **Prisma ORM**
- **REST APIs**

### Database
- PostgreSQL with Prisma migrations
- Strong schema validation
- Relational modeling with Prisma

### Tooling
- Prisma Migrate
- Prisma Studio
- dotenv for environment configuration

---

## 🗂️ Backend Project Structure

backend/
├── src/
│ ├── app.js # Express app configuration
│ ├── routes/ # REST route definitions
│ ├── controllers/ # Request handlers
│ ├── middlewares/ # Middleware (auth, validation, etc.)
│ └── lib/
│ └── prisma.js # Prisma client instance
│
├── prisma/
│ └── schema.prisma # Database schema
│
├── server.js # Application entry point
├── .env # Environment variables
└── package.json


---

## ⚙️ Getting Started (Backend)

```bash
1️⃣ Install dependencies
npm install

2️⃣ Configure environment variables

Create a .env file:

DATABASE_URL="postgresql://username:password@localhost:5432/teamflow_db"
PORT=5000

3️⃣ Run database migrations
npx prisma migrate dev

4️⃣ Start the server
npm run dev
```