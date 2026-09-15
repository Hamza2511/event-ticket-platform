# Event Ticket Platform

A full-stack event ticketing application where organizers can create and manage events, attendees can browse and purchase tickets, and staff can validate tickets at the door via QR code scanning.

## Tech Stack

**Backend**
- Java 21 / Spring Boot 3
- Spring Data JPA + Hibernate
- PostgreSQL
- Spring Security with OAuth2 / JWT (Keycloak)
- Maven

**Frontend**
- React 19 + TypeScript
- Vite
- Tailwind CSS
- OIDC authentication (react-oidc-context)

**Infrastructure**
- Docker & Docker Compose (PostgreSQL, Keycloak, Adminer)

## Features

- Organizer dashboard to create and manage events and ticket types
- Attendee-facing event browsing and ticket purchase flow
- QR-code based ticket generation and validation
- Role-based access control (organizers / attendees / staff) via Keycloak
- RESTful API secured with JWT

## Getting Started

### Prerequisites
- Java 21 (JDK)
- Node.js and npm
- Docker Desktop

### 1. Start the infrastructure
```bash
cd backend
docker compose up -d
```
This starts PostgreSQL, Keycloak, and Adminer.

### 2. Configure Keycloak
- Open `http://localhost:9090` and log in (`admin` / `admin`)
- Create a realm named `event-ticket-platform`
- Create a client `event-ticket-platform-app` (public, standard flow) with redirect URI `http://localhost:5173/callback`
- Create a test user with a password

### 3. Run the backend
Open the `backend` folder in IntelliJ (or any Java IDE) and run `TicketsApplication`.
The API will be available at `http://localhost:8080`.

### 4. Run the frontend
```bash
cd frontend
npm install --legacy-peer-deps
npm run dev
```
The app will be available at `http://localhost:5173`.

## Project Structure

| Directory | Contents |
|---|---|
| `backend/` | Spring Boot REST API, domain model, security config |
| `frontend/` | React + TypeScript client application |
| `docs/` | Architecture and design notes |

## About This Project

This project was built as a hands-on exercise in designing and implementing a secure, full-stack event ticketing platform, covering domain modeling, REST API design, JWT-based authentication with Keycloak, and a React frontend consuming the API. I followed a guided project structure to learn the patterns and then set up, configured, debugged, and deployed the full stack independently (Docker networking, Keycloak realm/client setup, database configuration, and frontend-backend integration).