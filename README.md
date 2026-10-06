# iNotebook - Your Notes on the Cloud

iNotebook is a full-stack secure cloud storage web application designed for creating, organizing, and accessing personal markdown or rich-text style notes. Built using the **MERN** (MongoDB, Express, React, Node.js) stack, the platform provides secure user accounts with segmented cloud storage spaces, token-based session persistence, and instant database modifications.

---

## 🚀 Key Features

- **Full CRUD Management:** Easily add, view, update, and remove personal notes from any authorized browser interface.
- **Secure Authentication Framework:** Uses custom middleware handlers enforcing JSON Web Tokens (JWT) for secure user sessions, signup, and login workflows.
- **Isolated User Storage Spaces:** Multi-tenant database design where users strictly access and modify their own securely nested note documents.
- **React Context API Architecture:** Global data-state pipeline utilizing Context and Custom State hooks to manage notes fluidly across complex component hierarchies without prop drilling.
- **Clean Component Interface:** A responsive client UI constructed using functional React views, modular form handling blocks, flash alerts, and conditional route bindings.

---

## 🛠️ Tech Stack & Dependencies

### Backend Core
- **Runtime & Framework:** Node.js, Express.js
- **Database Indexing:** MongoDB, Mongoose (ODM)
- **Security & Validation:** JSON Web Tokens (JWT), BcryptJS (Password hashing), Express-Validator (Request schema sanitization)

### Client UI
- **Development Tooling:** React (Vite-optimized rendering pipeline)
- **State Management:** React Context API (`noteContext`, `NoteState`)
- **Routing & Presentation:** React Router DOM, Custom Alert & Navigation fragments

---

## 📁 Project Architecture & Directory Structure

Based on your repository snapshot, here is the official folder breakdown:

```text
Inotebook-main/
├── backend/                # API Engine & Database Layer
│   ├── middleware/         # System pipeline interceptors
│   │   └── fetchuser.py    # JWT extraction, signature check, and user payload parsing
│   ├── models/             # Strict Mongoose data models
│   │   ├── Note.js         # Document schema specifying note title, description, tags, and date
│   │   └── User.js         # Identity schema defining name, email, credentials, and timestamps
│   ├── routes/             # Endpoints matching paths to controller execution
│   │   ├── auth.js         # Registration logic, login evaluation, and context identification
│   │   └── notes.js        # Note resource modifications (Fetch, Add, Put, Delete)
│   ├── db.js               # Central MongoDB handshake and client setup handler
│   └── index.js            # Node bootstrapper setting up middlewares and port bindings
├── client/                 # Interactive React Frontend Dashboard
│   ├── public/             # Browser presentation icons, manifest assets, and root HTML frame
│   ├── src/                # Core client functional files
│   │   ├── assets/         # Visual styling iconography and vector illustrations
│   │   ├── components/     # UI presentation fragments
│   │   │   ├── About.jsx   # Informational landing card
│   │   │   ├── AddNote.jsx # Modular interface housing title/description insert states
│   │   │   ├── Alert.jsx   # Floating notification banners for operational updates
│   │   │   ├── Home.jsx    # Core dashboard grouping form inputs and active lists
│   │   │   ├── Login.jsx   # Credential input layout with JWT session binding hooks
│   │   │   ├── Navbar.jsx  # Context-aware path manager changing states for active users
│   │   │   ├── Noteitem.jsx# Single note renderer with update and purge execution tools
│   │   │   ├── Notes.jsx   # Iterative matrix loop generating note structures from Context
│   │   │   └── Signup.jsx  # New registration wrapper processing profile data induction
│   │   ├── context/        # React global state containers
│   │   │   └── notes/      # Custom state tracking blueprints
│   │   │       ├── noteContext.js # Instantiated context gateway linking views to values
│   │   │       └── NoteState.jsx  # Fetch calls orchestrating frontend state syncing with APIs
│   │   ├── App.css         # Baseline template formatting definitions
│   │   ├── App.jsx         # Global page wrapper binding global routers, contexts, and views
│   │   └── main.jsx        # Root compiler injection linking React to the Document Object Model
│   ├── eslint.config.js    # Client code formatting verification presets
│   └── vite.config.js      # Optimization asset conductor configuration for client runtimes
├── package-lock.json       # Structural lock mapping downstream environment builds
└── package.json            # Root dependency matrix definitions
```

---

## ⚙️ Installation & Local Setup

Follow these sequential steps to fire up the system configuration on your machine:

### 1. Separate Setup Configuration
Ensure you have **Node.js** and a **MongoDB cluster connection string** ready.

### 2. Extract & Set Up Your Server Layer
```bash
cd Inotebook-main/backend
npm install
```

Configure your environment metrics inside an application `.env` variable block within the `backend/` directory:
```env
JWT_SECRET=your_custom_secure_signature_phrase
MONGO_URI=mongodb://localhost:27107/inotebook
```

Launch the data pipeline API:
```bash
npm start   # Runs 'node index.js' or configured nodemon watch rules
```

### 3. Build & Fire the User Workspace Client
Open a fresh shell partition and travel to the application workspace core:
```bash
cd Inotebook-main/client
npm install
npm run dev
```

Once tracking logs announce operational states, navigate your local desktop target browser to `http://localhost:5173` (or the dynamic Vite port logged in your console environment).

---

## 🛣️ API Endpoints Blueprint

### Identity & Authentication Mappings (`/api/auth`)
- `POST /createuser` - Validates input parameters and logs new registration profiles.
- `POST /login` - Evaluates credentials and returns secure JSON Web Tokens.
- `POST /getuser` - Intercepts access parameters using `fetchuser` middleware to output credential profiles.

### Notes Management Mappings (`/api/notes`)
- `GET /fetchallnotes` - Locates and returns all notes bound to the active user profile context.
- `POST /addnote` - Creates a new note object linked to the request user account parameters.
- `PUT /updatenote/:id` - Locates target item tracking parameters and overwrites modified property objects.
- `DELETE /deletenote/:id` - Validates tracking item ownership and strips targeted notes completely from storage records.
