Varthaman 💬

AI-Powered Real-Time Messaging & Social Communication Platform

Varthaman is a modern web-based communication platform designed to provide users with a simple and responsive environment for connecting with people, managing profiles, sending friend requests, and exchanging direct messages.

The application combines a responsive messaging interface with a Node.js/Express backend and flexible database architecture supporting both local SQLite development and PostgreSQL/Supabase production deployments.

⸻

check out website is live here https://preetham078.github.io/varthaman/

🚀 Features

👤 User Accounts

* Create a personal account
* Username-based identity
* Secure password storage using password hashing
* Display name and customizable bio
* Login and logout functionality

💬 Direct Messaging

* Send direct messages to other users
* View conversations by username
* Persistent message history
* Inbox containing previous conversations
* Message timestamps

🤝 Friend System

* Search users by username
* Send friend requests
* View incoming friend requests
* Accept friend requests
* Manage connections between users

👨‍💻 User Profiles

* View profile information
* Display name
* Username
* Bio
* Account creation date
* Friend statistics
* Chat statistics
* Message statistics
* Edit profile information
* Share profile
* Logout functionality

📱 Responsive Interface

The frontend is designed to work across desktop and mobile screen sizes.

The interface includes:

* Mobile navigation
* Responsive chat layout
* Chat sidebar
* Profile panel
* Friend-request interface
* User search
* Mobile-friendly messaging controls

🗄️ Flexible Database Architecture

Varthaman supports two database modes:

Development

* SQLite
* Local data.sqlite database
* Easy setup without an external database

Production

* PostgreSQL
* Supabase-compatible
* Shared database for multiple users and devices

The database automatically initializes the required tables when the server starts.

⸻

🏗️ Architecture

                    ┌──────────────────────┐
                    │      User Device     │
                    │ Desktop / Mobile     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Frontend UI       │
                    │ HTML + CSS + JS      │
                    └──────────┬───────────┘
                               │
                         REST API
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Node.js + Express    │
                    │      Backend         │
                    └──────────┬───────────┘
                               │
                    ┌──────────┴──────────┐
                    │                     │
                    ▼                     ▼
             ┌─────────────┐       ┌─────────────┐
             │   SQLite    │       │ PostgreSQL  │
             │ Development │       │  / Supabase │
             └─────────────┘       └─────────────┘

⸻

🛠️ Technology Stack

Frontend

* HTML5
* CSS3
* JavaScript
* Responsive Web Design
* Google Fonts / Inter

Backend

* Node.js
* Express.js
* REST APIs

Database

* SQLite
* PostgreSQL
* Supabase

AI

* OpenAI API integration

Deployment

* GitHub Pages
* Google Cloud
* Cloud Build
* Docker
* Render

⸻

📁 Project Structure

varthaman/
│
├── .github/
│   └── workflows/
│       ├── gcloud-run-deploy.yml
│       └── pages.yml
│
├── public/
│   ├── index.html
│   ├── app.js
│   ├── styles.css
│   └── config.js
│
├── scripts/
│   ├── create_artifact_repo.sh
│   ├── create_cloud_build_trigger.sh
│   ├── create_github_secret.sh
│   └── create_service_account.sh
│
├── db.js
├── server.js
│
├── Dockerfile
├── app.yaml
├── cloudbuild.yaml
├── render.yaml
│
├── .env.example
├── .gitignore
├── .dockerignore
│
├── package.json
├── package-lock.json
│
├── CLOUD_BUILD_TRIGGER.md
├── DEPLOY_TO_GCLOUD.md
└── README.md

⸻

🔄 Application Flow

User
 │
 ▼
Create Account / Login
 │
 ▼
Profile Created
 │
 ├───────────────┐
 │               │
 ▼               ▼
Search Users   View Profile
 │
 ▼
Send Friend Request
 │
 ▼
Request Accepted
 │
 ▼
Start Conversation
 │
 ▼
Send / Receive Messages
 │
 ▼
Messages Stored in Database

⸻

🔌 API Endpoints

Authentication

Method	Endpoint	Description
POST	/api/accounts	Create a new account
POST	/api/login	Authenticate a user

Profile

Method	Endpoint	Description
GET	/api/profile	Get current user’s profile
PATCH	/api/profile	Update profile

Users

Method	Endpoint	Description
GET	/api/accounts/search	Search users by username

Friend Requests

Method	Endpoint	Description
GET	/api/friend-requests	Get friend requests
POST	/api/friend-requests	Send a friend request
POST	/api/friend-requests/:username/accept	Accept a friend request

Messaging

Method	Endpoint	Description
GET	/api/inbox	Get conversations
GET	/api/messages/:username	Get conversation
POST	/api/messages	Send a message

Health Check

Method	Endpoint	Description
GET	/api/health	Check server status

The Express backend implements these REST endpoints for accounts, profiles, user search, friend requests, inboxes, and direct messages.

⸻

🗃️ Database Schema

Accounts

Stores user account information.

accounts
├── id
├── display_name
├── username
├── password_hash
├── bio
└── created_at

Direct Messages

Stores messages exchanged between users.

direct_messages
├── id
├── sender_id
├── receiver_id
├── content
└── created_at

Friend Requests

Stores connection requests between users.

friend_requests
├── id
├── requester_id
├── receiver_id
├── status
├── created_at
└── updated_at

The database layer automatically creates these tables and indexes when required.

⸻

⚙️ Installation

1. Clone the repository

git clone https://github.com/preetham078/varthaman.git
cd varthaman

2. Install dependencies

npm install

The project requires Node.js 20.17+ and uses Express, OpenAI, PostgreSQL, dotenv, and optional SQLite dependencies.

3. Configure environment variables

Create your environment file:

cp .env.example .env

Add the required configuration.

Example:

PORT=3000
HOST=0.0.0.0
OPENAI_API_KEY=your_openai_api_key
SUPABASE_DB_URL=your_postgresql_connection_string
ALLOWED_ORIGIN=*

Never commit your .env file or expose private API keys.

⸻

▶️ Run Locally

Start the application:

npm start

The server will run on:

http://localhost:3000

Then open the URL in your browser.

⸻

📱 Testing on Multiple Devices

If your computer and mobile devices are connected to the same Wi-Fi network, you can access the application using your computer’s local IP address:

http://YOUR_LOCAL_IP:3000

For example:

http://192.168.1.20:3000

Do not use localhost on another phone because localhost refers to that phone itself.

⸻

☁️ Production Deployment

Varthaman can be deployed using a separate frontend and backend architecture.

Recommended architecture:

GitHub Pages
     │
     │ Frontend
     ▼
Static Web Interface
     │
     │ REST API
     ▼
Node.js / Express Server
     │
     ▼
Supabase PostgreSQL

The repository already contains deployment configuration for Google Cloud, GitHub Pages, Docker, Cloud Build, and Render.

⸻

🔐 Security Considerations

The application includes password hashing rather than storing plain-text passwords.

For production deployment, additional security measures should be considered:

* HTTPS
* Secure authentication tokens/sessions
* Rate limiting
* Strong password requirements
* Input validation
* CSRF protection where applicable
* Restrictive CORS configuration
* Secure environment-variable management
* Database connection security
* API abuse protection

For production, change:

ALLOWED_ORIGIN=*

to your actual frontend domain.

⸻

🤖 AI Integration

The project includes OpenAI integration through the backend.

The OpenAI API key can be configured through:

OPENAI_API_KEY=your_api_key

If the API key is unavailable, the application can continue operating for messaging and data storage while AI functionality falls back accordingly.

⸻

🎨 Frontend

The frontend is implemented as a lightweight browser application using:

HTML
CSS
JavaScript

The main interface provides:

* Authentication
* Chat navigation
* User search
* Friend requests
* Profile management
* Messaging
* Mobile navigation

The current HTML interface identifies the application UI as WhatsChat.

⸻

🧪 Development

To modify the frontend:

public/index.html
public/styles.css
public/app.js
public/config.js

To modify backend APIs:

server.js

To modify database logic:

db.js

⸻

📌 Future Improvements

Possible improvements for future versions include:

* 🔒 JWT/session-based authentication
* 🔔 Real-time messaging using WebSockets
* 🟢 Online/offline status
* ✍️ Typing indicators
* 📎 File and image sharing
* 🎤 Voice messages
* 📞 Audio/video calling
* 🔔 Push notifications
* 👥 Group chats
* 🛡️ Advanced moderation
* 🤖 AI-powered chat assistant
* 🌐 Internationalization
* 📊 User analytics
* 🔍 Advanced user search
* 🌓 Dark/light themes

⸻

🌟 Project Vision

Varthaman aims to provide a lightweight and scalable communication platform where users can discover people, build connections, and communicate through a simple username-based messaging system.

The architecture is intentionally modular, allowing the project to evolve from a basic messaging application into a larger social communication platform.

⸻

👨‍💻 Developer

Preetham M

Computer Science Engineering
Alliance University, Bangalore

GitHub:
https://github.com/preetham078

Project:
https://github.com/preetham078/varthaman

⸻

📄 License

This project currently uses the license configuration specified in package.json.

⸻

⭐ Support

If you find this project useful, consider giving the repository a ⭐ on GitHub.

⸻

Built with ❤️ using Node.js, Express, JavaScript, PostgreSQL/SQLite and AI.
