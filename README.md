# Full-Stack FastAPI and React Template

Welcome to the Full-Stack FastAPI and React template repository. This repository serves as a demo application for interns, showcasing how to set up and run a full-stack application with a FastAPI backend and a ReactJS frontend using ChakraUI.

## Project Structure

The repository is organized into two main directories:

- **frontend**: Contains the ReactJS application.
- **backend**: Contains the FastAPI application and PostgreSQL database integration.

Each directory has its own README file with detailed instructions specific to that part of the application.

## Getting Started

To get started with this template, please follow the instructions in the respective directories:

- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)

## Prerequisites

- Node.js (version 14.x or higher)
- npm (version 6.x or higher)
- Python 3.8 or higher
- Poetry (for dependency management)
- PostgreSQL
- Docker and Docker Compose

## Environment Variables

Create a `.env` file in the root directory with the following content, adjusting the values as needed:

```env
# .env
TRAEFIK_API_INSECURE=true
TRAEFIK_DASHBOARD_PORT=8080
DOMAIN_NAME=yourdomain.com
POSTGRES_DB=mydatabase
POSTGRES_USER=postgres
POSTGRES_PASSWORD=mysecretpassword
PROXY_MANAGER_EMAIL=admin@example.com
PROXY_MANAGER_PASSWORD=changeme
```

## Manual Deployment

### Frontend

1. **Navigate to the frontend directory**:

   ```sh
   cd frontend
   ```

2. **Install dependencies**:

   ```sh
   npm install
   ```

3. **Run the development server**:

   ```sh
   npm run dev
   ```

4. **Configure API URL**:
   Ensure the VITE_API_URL is correctly set in the `.env` file.

### Backend

1. **Navigate to the backend directory**:

   ```sh
   cd backend
   ```

2. **Install dependencies using Poetry**:

   ```sh
   poetry install
   ```

3. **Set up the database with the necessary tables**:

   ```sh
   poetry run bash ./prestart.sh
   ```

4. **Run the backend server**:

   ```sh
   poetry run uvicorn app.main:app --reload
   ```

5. **Update configuration**:
   Ensure you update the necessary configurations in the `.env` file, particularly the database configuration.

### PostgreSQL

Ensure that PostgreSQL is installed and running. Create a new database and user with the details specified in the `.env` file.

## Docker Deployment

### Setup

1. **Clone the repository and navigate to the root directory**:

   ```sh
   git clone <repository-url>
   cd <repository-name>
   ```

2. **Ensure you have Docker and Docker Compose installed**.

3. **Create a `.env` file in the root directory** with the content provided above.

### Running with Docker Compose

1. **Build and start the services**:

   ```sh
   docker-compose up -d
   ```

2. **Check the status of the containers**:

   ```sh
   docker-compose ps
   ```

3. **Access the services**:
   - Frontend: `http://yourdomain.com`
   - Backend API: `http://yourdomain.com/api`
   - Backend API Docs: `http://yourdomain.com/docs`
   - Adminer (PostgreSQL management): `http://db.yourdomain.com`
   - Traefik Dashboard: `http://yourdomain.com:8080` (if enabled)
   - Proxy Manager Dashboard: `http://proxy.yourdomain.com`

## Project Structure

```sh
.
├── frontend
│   ├── src
│   ├── public
│   ├── package.json
│   ├── .env
│   └── README.md
├── backend
│   ├── app
│   ├── tests
│   ├── pyproject.toml
│   ├── prestart.sh
│   ├── .env
│   └── README.md
├── Dockerfile.frontend
├── Dockerfile.backend
├── docker-compose.yml
├── .env
├── .gitignore
└── README.md
└── LICENSE
```

### Additional Notes

- Make sure to properly set the environment variables for both development and production environments.
- For production, disable insecure options in Traefik and ensure the Traefik dashboard is not publicly accessible.
