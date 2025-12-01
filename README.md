# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) (or [oxc](https://oxc.rs) when used in [rolldown-vite](https://vite.dev/guide/rolldown)) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.


## SETUP STEPS
### Prerequisites

- Node.js (v18 or higher)
- MongoDB (local or cloud instance)
- Google AI API key (for Gemini integration)

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd heal-sym
   ```

2. **Install backend dependencies**
   ```bash
   cd backend
   npm install
   ```

3. **Install frontend dependencies**
   ```bash
   cd ../frontend-old
   npm install
   ```

4. **Environment Setup**

   Create a `.env` file in the `backend` directory:
   ```env
   PORT=5000
   MONGO_URI=mongodb://localhost:27017/healthcare-symptom-checker
   GOOGLE_API_KEY=your_gemini_api_key_here
   MODEL=gemini-2.5-flash
   FRONTEND_ORIGIN=http://localhost:5173
   ```

   Create a `.env` file in the `frontend-old` directory:
   ```env
   VITE_API_BASE=http://localhost:5000
   ```

### Running the Application

1. **Start MongoDB** (if running locally)
   ```bash
   mongod
   ```

2. **Start the backend server**
   ```bash
   cd backend
   npm run dev
   ```

3. **Start the frontend development server** (in a new terminal)
   ```bash
   cd frontend-old
   npm run dev
   ```

4. **Access the application**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:5000
   - Health Check: http://localhost:5000/api/health

## 📁 Project Structure

```
heal-sym/
├── backend/
│   ├── controller/
│   │   └── symptomController.js    # Request handlers for symptom analysis
│   ├── model/
│   │   └── Query.js               # MongoDB schema for user queries
│   ├── route/
│   │   └── symptom.js             # API routes for symptom endpoints
│   ├── service/
│   │   └── llmService.js          # Google Gemini AI integration
│   ├── server.js                  # Main server file
│   └── package.json
├── frontend-old/
│   ├── src/
│   │   ├── components/
│   │   │   ├── SymptomChecker.jsx # Main symptom analysis component
│   │   │   ├── home.jsx           # Landing page
│   │   │   ├── About.jsx          # About page
│   │   │   ├── Contact.jsx        # Contact page
│   │   │   └── Privacy.jsx        # Privacy policy
│   │   ├── styles/
│   │   │   ├── symptomChecker.css # Symptom checker specific styles
│   │   │   ├── home.css           # Home page styles
│   │   │   └── pageBase.css       # Base styles
│   │   ├── App.jsx                # Main app component with routing
│   │   └── main.jsx               # App entry point
│   └── package.json
└── README.md
```

## 🔧 API Endpoints

### Health Check
- `GET /api/health` - Server health status

### Symptom Analysis
- `POST /api/symptoms` - Analyze symptoms and get AI insights
  ```json
  {
    "text": "fever, headache, fatigue"
  }
  ```

### History Management
- `GET /api/symptoms/history/:sessionId` - Get user's query history


## TECHSTACK USED
### Frontend (React + Vite)
- **Framework**: React 19 with Vite for fast development
- **Styling**: TailwindCSS with custom CSS modules
- **Routing**: React Router for navigation
- **Icons**: Heroicons for consistent iconography
- **Animations**: Framer Motion for smooth transitions
- **Markdown**: React Markdown for rich text rendering

### Backend (Node.js + Express)
- **Runtime**: Node.js with ES modules
- **Framework**: Express.js for REST API
- **AI Integration**: Google Generative AI (Gemini)
- **Security**: CORS, rate limiting, input validation
- **Environment**: dotenv for configuration management

### Database
- **Database**: MongoDB with Mongoose ODM

 ## SCREEN RECORDING
 https://drive.google.com/file/d/1H1iOlj2hE3v5zxR-yFytUK20t-A8J9oA/view?usp=sharing
 
## Most Challenging Problem I Solved Recently
The most challenging problem I solved while building this Healthcare website was getting the layout to look clean and consistent on all screen sizes without using any frameworks. Small CSS changes would fix one section but break another, so I had to patiently adjust the design until everything aligned properly. I also struggled with making the JavaScript form interactions smooth, especially input validation and updating the UI without causing layout shifts. At one point, the navigation and sections were overlapping, so I had to reorganize my CSS structure and rewrite parts of the script. Through these issues, I learned how important responsive design, clean code structure, and careful testing are in front-end development. Overall, solving this challenge improved both my confidence and my understanding of how real websites behave.
⭐ Bonus Features Implemented
Interactive Dashboard

Developed a dashboard showing:

Number of appointments

Quick patient stats

Navigation cards for faster access
