## Project Overview
Name: R3alm Hub
Purpose: A professional dashboard for managing R3alm Ecosystem applications with full CRUD functionality, user authentication, and responsive design.

## Technical Requirements ### Tech Stack
Frontend: React 18 + TypeScript + Vite
Styling: Tailwind CSS with dark theme (cyan/blue gradients, NO purple/indigo)
Icons: Lucide React
Routing: React Router
State Management: React Context or Zustand
Database: Local JSON storage (localStorage or lowdb)
Accessibility: WCAG 2.1 compliant
### Core Features to Implement #### 1. Authentication System
Login screen with centered form (email/password fields)
Two demo login buttons:
Demo User: demo@r3alm.io / demo123456
Admin User: admin@r3alm.io / admin123456
Error handling with Tailwind-styled alerts
Role-based access control (admin vs user permissions)
#### 2. Navigation Structure
Left-side collapsible menu (NOT top navigation) with:

Dashboard (shows all application cards)
Add Application (admin only)
Settings (user preferences)
Logout
Mobile: Hamburger icon with slide-in animation
Desktop: Fixed sidebar with cyan highlights for active items
#### 3. Dashboard Features
Display cards for all 21 applications from R3almEcosystemApplications.csv
Each card shows: name, description, status, version, last_updated
Search bar and status filter functionality
Responsive grid layout using Tailwind
Clickable cards navigate to dedicated app pages
Edit button on cards (admin only)
#### 4. Application Detail Pages
Route: /apps/[app-name]
Documentation tabs/cards for: README.md, HISTORY.md, ROADMAP.md, API_DOCUMENTATION.md, USER_MANUAL.md, CONTRIBUTING.md, CODE_OF_CONDUCT.md, CHANGELOG.md, SECURITY.md, AUTHORS.md, FAQ.md
Back button to dashboard
Copy-to-clipboard functionality for documentation
#### 5. Admin Features
Add new application form with validation
Edit existing application cards via modal/form
All changes persist to local database
#### 6. Settings Page
Theme preferences (dark/light toggle)
Notification settings
Real-time preference saving
### Database Schema
Initialize local database with:


interface User {
  id: string;
  email: string;
  role: 'user' | 'admin';
  created_at: string;
}

interface Application {
  id: string;
  name: string;
  description: string;
  status: 'Active' | 'In Development' | 'Planned';
  version: string;
  last_updated: string;
}

interface Preference {
  user_id: string;
  theme: 'dark' | 'light';
  notifications_enabled: boolean;
}

interface Documentation {
  app_id: string;
  type: 'README' | 'HISTORY' | 'ROADMAP' | 'API_DOCUMENTATION' | 'USER_MANUAL' | 'CONTRIBUTING' | 'CODE_OF_CONDUCT' | 'CHANGELOG' | 'SECURITY' | 'AUTHORS' | 'FAQ';
  content: string;
}
### API Simulation
Implement mock endpoints:

GET /api/applications - Fetch all applications
POST /api/applications - Create new application
PUT /api/applications/:id - Update application
Include proper validation and error responses (400, 401, 403)
### UI/UX Requirements
Color Scheme: Dark theme with cyan (#06b6d4) and blue (#3b82f6) gradients
Responsive Design: Mobile-first approach, test on all viewport sizes
Animations: Smooth transitions, hover effects, loading states
Accessibility: Proper ARIA labels, keyboard navigation, color contrast
Form Validation: Real-time validation with clear error messages
### Project Structure

r3alm-hub/
├── src/
│   ├── components/
│   │   ├── Login.tsx
│   │   ├── Dashboard.tsx
│   │   ├── AppDetails.tsx
│   │   ├── AddAppForm.tsx
│   │   ├── Navigation.tsx
│   │   └── Settings.tsx
│   ├── contexts/
│   │   └── AuthContext.tsx
│   ├── lib/
│   │   ├── database.ts
│   │   └── types.ts
│   ├── pages/
│   │   ├── Home.tsx
│   │   ├── Dashboard.tsx
│   │   ├── AppPage.tsx
│   │   ├── AddApp.tsx
│   │   └── Settings.tsx
│   ├── App.tsx
│   └── main.tsx
├── public/
│   └── demo-data.json
├── vite.config.ts
└── package.json
### Success Criteria
Application loads without errors and displays login screen
Demo logins work and redirect to dashboard
All 21 application cards display correctly with data from CSV
Navigation menu is fully functional and responsive
Admin users can add/edit applications
Documentation pages load with proper tab/card navigation
Settings save preferences in real-time
All UI components are accessible and mobile-friendly
Dark theme with cyan/blue gradients is consistently applied
Search and filter functionality works correctly
### Important Notes
Use the provided R3almEcosystemApplications.csv to populate the 21 application cards
Generate mock content for documentation files, using CONTRIBUTING.md and CHANGELOG.md as templates
Ensure all code is well-commented and extensible for future R3alm applications
Test thoroughly on both mobile and desktop viewports
Implement proper input sanitization using sanitize-html
Build this application step-by-step, ensuring each feature is fully functional before moving to the next. Focus on creating a professional, polished user experience that represents the R3alm brand effectively.