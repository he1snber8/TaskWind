# TaskWind

A web-based task management application allowing users to add, edit, and delete tasks within projects, featuring JWT authentication, project-specific categorization, priority-based sorting, and a responsive Angular UI styled with Tailwind CSS.

## Tech Stack

- Angular
- Tailwind CSS

## Requirements

- User authentication with JWT tokens (Hint: Use Angular's HttpClient to handle auth requests and store the JWT in localStorage.)
- Project-based task categorization (Hint: Bind dropdown selection to filter task list in the component.)
- Priority sorting of tasks (Hint: Use JavaScript array sort in the TaskService or component.)
- Optional: Implement due date filtering (Hint: Extend Task model with dueDate: string and filter by date.)

## Installation

1. Ensure you have Node.js (v14+) and npm installed.
2. Install Angular CLI globally:
   bash
   npm install -g @angular/cli
   
3. Clone the repository:
   bash
   git clone https://github.com/<your-username>/TaskWind.git
   cd TaskWind
   
4. Install dependencies:
   bash
   npm install
   
5. Configure environment variables in `src/environments/`:
   ts
   // src/environments/environment.ts
   export const environment = {
     production: false,
     apiUrl: 'https://your-api-base-url.com',
   };
   

## Usage

1. Start the development server:
   bash
   ng serve
   
2. Navigate to `http://localhost:4200` in your browser.
3. Register or log in to begin creating projects and managing tasks.

## Implementation Steps

1. **Initialize Angular Project**
   - Run `ng new TaskWind --routing --style=css`.
2. **Install and Configure Tailwind CSS**
   - Follow Tailwind docs to install: `npm install tailwindcss postcss autoprefixer`
   - Generate config: `npx tailwindcss init`
   - Update `tailwind.config.js` and include Tailwind directives in `styles.css`.
3. **Create Authentication Service**
   - Use `ng generate service services/auth`.
   - Implement login, register methods using `HttpClient`.
   - Store and retrieve JWT from `localStorage`.
4. **Set Up Route Guards**
   - Generate `AuthGuard` to protect routes requiring authentication.
5. **Define Models**
   - Create `User`, `Project`, and `Task` interfaces (`dueDate?: string`).
6. **Implement Project Management**
   - Generate `ProjectListComponent` and `ProjectFormComponent`.
   - CRUD operations via `ProjectService`.
7. **Implement Task Management**
   - Generate `TaskListComponent` and `TaskFormComponent`.
   - In `TaskService`, implement methods to add, edit, delete tasks.
   - Sort tasks by priority using `array.sort((a, b) => b.priority - a.priority)`.
   - Filter tasks by selected project via dropdown binding.
   - (Optional) Filter tasks by due date in component logic.
8. **HTTP Interceptor for JWT**
   - Create `TokenInterceptor` to attach JWT to outgoing requests.
9. **UI and Styling**
   - Use Tailwind CSS utility classes across components for responsive design.
10. **Testing and Debugging**
   - Use Angular’s development tools and browser console for testing endpoints and UI flows.

## API Endpoints

*(Assuming a RESTful backend; adjust URLs per your implementation.)*

- **POST** `/api/auth/register` — Register a new user.
- **POST** `/api/auth/login` — Authenticate user and return JWT.
- **GET** `/api/projects` — Fetch all projects for the authenticated user.
- **POST** `/api/projects` — Create a new project.
- **GET** `/api/projects/:projectId/tasks` — Fetch tasks for a specific project.
- **POST** `/api/projects/:projectId/tasks` — Add a new task to a project.
- **PUT** `/api/projects/:projectId/tasks/:taskId` — Update an existing task.
- **DELETE** `/api/projects/:projectId/tasks/:taskId` — Delete a task.