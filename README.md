# Bitasmbl-ChessConnect

Description

Develop a scalable real-time multiplayer chess platform featuring a React single-page application, an Express/Node.js backend secured with JWT authentication, live gameplay via Socket.IO, and Redis for in-memory state management and pub/sub across server instances. Containerized with Docker for consistent, production-ready deployments.

## Tech Stack

- React
- Node.js (Express)
- Socket.IO
- Redis

## Requirements

- Implement JWT authentication for all API endpoints
- Enforce chess rules on the server
- Use Redis pub/sub for synchronizing state across server instances
- Write unit tests for game logic and API routes

## Installation

1. Clone the repository:
   bash
   git clone https://github.com/YourUsername/Bitasmbl-ChessConnect.git
   cd Bitasmbl-ChessConnect
   

2. Server setup:
   bash
   cd server
   npm install
   
   Create a `.env` file in `server/` with the following variables:
   dotenv
   PORT=4000
   JWT_SECRET=your_jwt_secret
   REDIS_URL=redis://localhost:6379
   

3. Client setup:
   bash
   cd ../client
   npm install
   

4. Start a local Redis instance (if not already running):
   bash
   docker run -d --name chessconnect-redis -p 6379:6379 redis
   

## Usage

### Development

1. Start the backend (with hot reload):
   bash
   cd server
   npm run dev
   
2. Start the frontend:
   bash
   cd ../client
   npm start
   
3. Open your browser at `http://localhost:3000` to play.

### Production (Docker)

1. Build and run containers:
   bash
   docker-compose up --build
   
2. The client will be served at `http://localhost:80` and the API at `http://localhost:4000`.

## Implementation Steps

1. Initialize the project structure with `/server` (Express) and `/client` (React).
2. Configure Express server with JWT authentication middleware for all API routes.
3. Define and enforce chess rules on the server using a chess engine or custom logic.
4. Integrate Socket.IO in the server to handle real-time game events and broadcasts.
5. Set up Redis client in the server for in-memory state storage and pub/sub across instances.
6. In the React app, connect to the backend via REST for auth and via Socket.IO for live moves.
7. Create game lobby, match-making, and in-game UI components in React.
8. Write unit tests (using Jest) for server game logic and API routes to ensure rule enforcement and auth.
9. Add Dockerfiles for server and client; configure `docker-compose.yml` for multi-container orchestration.
10. Document environment variables, scripts, and API endpoints for contributors.

## API Endpoints

- POST `/api/auth/register` – Register a new user (email, password)
- POST `/api/auth/login` – Authenticate and receive JWT token
- POST `/api/games` – Create a new game session (auth required)
- GET `/api/games/:gameId` – Fetch current game state (auth required)
- POST `/api/games/:gameId/move` – Submit a move; server enforces chess rules (auth & JWT required)
- GET `/api/users/me` – Fetch current user profile (auth required)