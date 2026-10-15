# Project Manager Backend

This repository contains the REST backend for Project Manager, an application for organizing software projects and the work assigned to them.

The backend provides authentication and project-management APIs for the [Project Manager Frontend](https://github.com/Shifinn/project-manager-frontend). It handles projects, modules, sub-modules, work items, bugs, user assignments, project roles, and the lookup data used by the frontend.

The frontend is maintained in a separate repository. This repository contains only the backend API.

## What the API provides

### Authentication

- Checks username and password credentials.
- Returns the user data used by the frontend to establish a session.

### Projects

- Lists all projects and projects available to a user.
- Creates, updates, and deletes projects.
- Retrieves project details.
- Retrieves the project data used by the Gantt chart.
- Manages user roles within a project.

### Project structure

- Creates and updates modules.
- Lists modules and module details.
- Creates, updates, and deletes sub-modules.
- Lists sub-modules for a project.

### Work items

- Creates, updates, and deletes work items.
- Retrieves work items for a sub-module.
- Retrieves work-item details.
- Provides a user's todo list.
- Manages users assigned to work items.
- Provides work-name data for project development views.

### Bugs

- Creates and updates bug work items.
- Lists bugs for a project.
- Retrieves bug details.
- Stores the affected work and defect-cause information associated with a bug.

### Lookup data

- Lists usernames.
- Lists users assigned to a project.
- Provides project and work names.
- Provides trackers, activities, priorities, and states.
- Provides defect causes.

## Architecture

- `api/index.go` contains the Gin router, request types, handlers, CORS configuration, database connection, and Vercel entry point.
- PostgreSQL provides the application data and database functions used by the handlers.
- The backend uses the `pgx` PostgreSQL driver through Go's `database/sql` package.
- Vercel routes requests matching `/api` to `api/index.go`.
- CORS currently allows the deployed frontend at `https://project-manager-frontend-olive.vercel.app` and local Angular development at `http://localhost:4200`.


## Related repository

[Project Manager Frontend](https://github.com/Shifinn/project-manager-frontend) is the Angular application that consumes this API. It provides the login page, My Work dashboard, project directory, backlog, bugs view, and Gantt chart.

## Tech stack

- Go 1.24.4
- Gin 1.10
- PostgreSQL
- pgx PostgreSQL driver
- `godotenv` for local environment loading
- `gin-contrib/cors`
- Vercel Serverless Functions
