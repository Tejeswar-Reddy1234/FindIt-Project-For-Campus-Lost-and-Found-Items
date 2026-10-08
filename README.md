FindIt – Campus Lost & Found Platform
FindIt is a campus-based Lost & Found platform developed to help students, security staff, and administrators report, discover, match, claim, and return lost items in an organized way.
Features
- Student registration and login
- JWT-based authentication
- Role-based access for Students, Security, and Admins
- Report lost and found items
- Search and filter reported items
- View item details and status
- Rule-based smart matching between lost and found items
- Ownership claim submission
- Security claim verification
- Found item collection management
- Handover and return management
- In-app messaging
- Notifications for important activities
- Admin dashboard and user management
Smart Matching
FindIt includes a rule-based smart matching system that compares lost and found items using six attributes:
Attribute	Weight
Category	25
Location	25
Description / Name	20
Colour	10
Brand	10
Date Proximity	10
Total	100


The system generates a match score and provides reasons for the match, such as matching category, location, colour, brand, or similar descriptions.
The current matching system is a deterministic rule-based heuristic and does not use machine learning or an external AI model.

How It Works
User interacts with the React frontend, which communicates with the Node.js and Express backend through REST APIs.
User
  ↓
React Frontend
  ↓
fetchApi()
  ↓
Node.js + Express REST API
  ↓
Route Handler
  ↓
Business Logic
  ↓
In-Memory Data Store
  ↓
JSON Response
  ↓
React UI

Lost & Found Flow
Report Item
    ↓
Smart Matching
    ↓
Possible Match
    ↓
Ownership Claim
    ↓
Security Verification
    ↓
Claim Approved
    ↓
Handover
    ↓
Returned

Authentication Flow
Login
  ↓
SignIn.jsx
  ↓
POST /api/auth/login
  ↓
authRoutes.js
  ↓
Password Verification
  ↓
JWT Token
  ↓
Token Stored in localStorage
  ↓
Bearer Token Sent with Requests
  ↓
Protected API Access

Technology Stack
Frontend
- React 18
- Vite
- React Router
- Tailwind CSS
- JavaScript
Backend
- Node.js
- Express.js
- REST APIs
- JSON
Authentication & Security
- JWT
- bcryptjs
- Role-based authorization
Data Storage
The current runtime implementation uses JavaScript in-memory stores for users, items, claims, messages, notifications, and matches.
MongoDB/Mongoose integration is prepared for future persistent database integration.
Project Structure
FindIt/
│
├── client/
│   └── src/
│       ├── components/
│       ├── context/
│       │   └── AuthContext.jsx
│       ├── pages/
│       │   ├── SignIn.jsx
│       │   ├── SignUp.jsx
│       │   ├── PostItem.jsx
│       │   ├── BrowseItems.jsx
│       │   ├── ItemDetails.jsx
│       │   ├── SmartMatches.jsx
│       │   ├── SecurityDesk.jsx
│       │   ├── AdminDashboard.jsx
│       │   └── ...
│       ├── services/
│       │   └── api.js
│       └── App.jsx
│
├── server/
│   ├── middleware/
│   │   └── auth.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── itemRoutes.js
│   │   ├── claimRoutes.js
│   │   ├── handoverRoutes.js
│   │   ├── securityRoutes.js
│   │   ├── messageRoutes.js
│   │   ├── notificationRoutes.js
│   │   ├── adminRoutes.js
│   │   └── metaRoutes.js
│   ├── utils/
│   │   ├── memoryStore.js
│   │   └── smartMatcher.js
│   └── server.js
│
└── README.md

Main API Modules
API	Purpose
/api/auth	Registration and login
/api/items	Lost/found item management
/api/claims	Ownership claims and verification
/api/handover	Handover management
/api/security	Security Desk operations
/api/messages	Conversations and messages
/api/notifications	In-app notifications
/api/admin	Admin operations
/api/meta	Categories and locations


User Roles
Student
- Register and login
- Report lost/found items
- Browse and search items
- View smart matches
- Submit claims
- Send messages
- View notifications
Security
- Review claims
- Collect found items
- Manage item custody
- Complete handovers
- Perform Security Desk operations
Admin
- View dashboard statistics
- Manage users
- Manage user roles
- Access administrative functions
Installation
Clone the Repository
git clone <YOUR_REPOSITORY_URL>
cd FindIt

Install Frontend Dependencies
cd client
npm install

Install Backend Dependencies
Open another terminal:
cd server
npm install

Start Backend
npm run dev

Start Frontend
cd client
npm run dev

Environment Variables
Create the required environment configuration.
JWT_SECRET=your_secret_key
PORT=5000

For the frontend, if required:
VITE_API_URL=http://localhost:5000

Do not commit real passwords, tokens, API keys, or other sensitive credentials to the repository.
Future Improvements
- MongoDB persistent database integration
- Real-time messaging using WebSockets
- Email, SMS, and push notifications
- Improved image upload and storage
- Machine-learning-based matching
- Stronger input validation
- Rate limiting and additional security controls
- Improved access control for messages and claims
Project Goal
FindIt aims to provide a centralized campus platform that simplifies the complete lost-and-found process:
Report → Discover → Match → Claim → Verify → Handover → Return
Team
CSE Panthers
Woxsen University
School of Technology
B.Tech Computer Science & Engineering
License
This project was developed as an academic project for educational purposes.
