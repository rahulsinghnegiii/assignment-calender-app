# Calendar Application Development Plan

## Project Overview
A React-based calendar application with Redux state management and MongoDB backend, featuring a weekly view with drag-and-drop event management, similar to Google Calendar.

## Technical Stack
- **Frontend**: React.js + Vite with Tailwind CSS
- **State Management**: Redux
- **Backend**: Node.js with Express
- **Database**: MongoDB
- **Additional Libraries**: 
  - react-big-calendar or fullcalendar (for calendar component)
  - react-dnd or react-beautiful-dnd (for drag-and-drop)
  - mongoose (for MongoDB object modeling)
  - axios (for API requests)
  - react-hook-form (for form handling)

## Phase 1: Project Setup (Day 1, Morning)

### 1.1 Initialize Project Structure
- [ ] Create a new React application using Vite
  ```bash
  npm create vite@latest calendar-app -- --template react
  cd calendar-app
  npm install
  ```
- [ ] Setup Tailwind CSS
  ```bash
  npm install -D tailwindcss postcss autoprefixer
  npx tailwindcss init -p
  ```
- [ ] Configure Tailwind CSS (tailwind.config.js)
  ```javascript
  /** @type {import('tailwindcss').Config} */
  export default {
    content: [
      "./index.html",
      "./src/**/*.{js,ts,jsx,tsx}",
    ],
    theme: {
      extend: {},
    },
    plugins: [],
  }
  ```
- [ ] Add Tailwind directives to CSS (src/index.css)
  ```css
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
  ```
- [ ] Set up folder structure
  ```
  src/
  ├── components/
  │   ├── Calendar/
  │   ├── EventModal/
  │   └── common/
  ├── pages/
  ├── redux/
  │   ├── actions/
  │   ├── reducers/
  │   └── store.js
  ├── services/
  │   └── api.js
  ├── utils/
  ├── App.jsx
  ├── main.jsx
  └── index.css
  ```
- [ ] Install necessary dependencies
  ```bash
  npm install redux react-redux @reduxjs/toolkit axios
  npm install react-big-calendar date-fns
  npm install react-hook-form
  npm install react-beautiful-dnd
  ```

### 1.2 Backend Setup
- [ ] Create a new directory for the backend
  ```bash
  mkdir backend
  cd backend
  npm init -y
  ```
- [ ] Install backend dependencies
  ```bash
  npm install express mongoose cors body-parser dotenv
  npm install --save-dev nodemon
  ```
- [ ] Create basic server structure
  ```
  backend/
  ├── config/
  │   └── db.js
  ├── controllers/
  │   └── eventController.js
  ├── models/
  │   └── Event.js
  ├── routes/
  │   └── eventRoutes.js
  ├── .env
  └── server.js
  ```
- [ ] Set up MongoDB connection
- [ ] Define Event schema with fields for title, category, date, start time, end time

## Phase 2: Core Backend Implementation (Day 1, Afternoon)

### 2.1 API Development
- [ ] Create RESTful API endpoints for events:
  - GET /api/events - Retrieve all events
  - POST /api/events - Create a new event
  - PUT /api/events/:id - Update an existing event
  - DELETE /api/events/:id - Delete an event (optional)
- [ ] Implement controllers for each endpoint
- [ ] Add validation for event data
- [ ] Test API endpoints using Postman or Thunder Client

### 2.2 Database Integration
- [ ] Finalize MongoDB schema
- [ ] Implement CRUD operations
- [ ] Set up error handling for database operations

## Phase 3: Frontend Base & Redux Setup (Day 1, Evening)

### 3.1 Redux Configuration
- [ ] Set up Redux store using Redux Toolkit
- [ ] Create event-related slices for:
  - fetchEvents
  - createEvent
  - updateEvent
  - deleteEvent (optional)
- [ ] Implement reducers and actions using createSlice
- [ ] Create selectors for accessing event data

### 3.2 Basic UI Components
- [ ] Create layout components (Header, Sidebar, etc.) with Tailwind CSS
- [ ] Implement responsive design using Tailwind utility classes
- [ ] Set up routing (if needed)

## Phase 4: Calendar Implementation (Day 2, Morning)

### 4.1 Calendar View
- [ ] Create weekly calendar grid component
- [ ] Implement time slots (hourly divisions)
- [ ] Add day headers (Monday through Sunday)
- [ ] Display current week and navigation controls
- [ ] Style the calendar view with Tailwind CSS to match the design

### 4.2 Event Rendering
- [ ] Display events on calendar based on their time slots
- [ ] Style events according to their category using Tailwind's color classes
- [ ] Implement visual indicators for event duration
- [ ] Handle event overlapping

## Phase 5: Event Interaction (Day 2, Afternoon)

### 5.1 Event Creation
- [ ] Implement click handler on calendar to open modal
- [ ] Create event form with fields for:
  - Title input
  - Category dropdown (exercise, eating, work, relax, family, social)
  - Date picker
  - Start time picker
  - End time picker
- [ ] Style form components with Tailwind CSS
- [ ] Connect form submission to Redux action and API
- [ ] Add form validation

### 5.2 Drag and Drop
- [ ] Implement drag-and-drop functionality for events
- [ ] Update event time/date when moved to a different slot
- [ ] Connect drag-end events to Redux and API updates
- [ ] Add visual feedback during drag operations

## Phase 6: Testing & Refinement (Day 2, Evening)

### 6.1 Testing
- [ ] Test all features:
  - Event creation and display
  - Event editing
  - Drag-and-drop functionality
  - Weekly navigation
- [ ] Cross-browser testing
- [ ] Bug fixes

### 6.2 Final Polishing
- [ ] Improve UI/UX using Tailwind's utility classes
- [ ] Add loading states and indicators
- [ ] Implement error handling and user feedback
- [ ] Add responsive design adjustments
- [ ] Optimize performance
- [ ] Configure build process with Vite

## Phase 7: Documentation & Submission

### 7.1 Documentation
- [ ] Create README.md with:
  - Project description
  - Setup instructions
  - Technologies used
  - Features implemented
  - Screenshots
  
### 7.2 Submission
- [ ] Final code review
- [ ] Package the application
- [ ] Submit the assignment

## Technical Considerations

### State Management
- Store all event data in Redux
- Use Redux Toolkit for simpler Redux configuration
- Handle optimistic updates for drag-and-drop operations
- Maintain clean separation of concerns

### Backend Architecture
- Implement proper error handling
- Validate incoming requests
- Ensure efficient database queries

### Performance
- Consider lazy loading or pagination for large datasets
- Optimize re-renders in React components
- Use React.memo and useCallback where appropriate
- Leverage Vite's fast HMR during development 