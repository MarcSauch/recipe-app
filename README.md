# Recipe App Docker Setup

This directory contains the Docker configuration to run the complete Recipe App stack.

## Architecture

- **Frontend**: Angular application
- **Backend**: Deno API server
- **Database**: PostgreSQL database

## Quick Start

### Production Mode
```bash
docker-compose up -d
```

### Development Mode (with frontend hot-reload)
```bash
docker-compose --profile development up -d
```

## Services

### Frontend (Port 80 & 4200)
- Production build 
- Available at http://localhost or http://localhost:4200

### Backend (Port 8010)
- Deno API server
- Available at http://localhost:8010

### Database (Port 5432)
- PostgreSQL database
- Host: localhost:5432
- Database: recipe_db
- User: recipe_user
- Password: recipe_password

## Development

### Frontend Development Mode
The development profile includes a frontend-dev service that runs the Angular dev server with hot-reload:
```bash
docker-compose --profile development up frontend-dev
```
Access at http://localhost:4201

### Backend Development
The backend service is configured with file watching for development:
```bash
docker-compose up backend
```

## Environment Variables

You can override default environment variables by creating a `.env` file:

```env
POSTGRES_DB=recipe_db
POSTGRES_USER=recipe_user
POSTGRES_PASSWORD=recipe_password
DATABASE_URL=postgresql://recipe_user:recipe_password@database:5432/recipe_db
```

## Useful Commands

### View logs
```bash
docker-compose logs -f [service_name]
```

### Rebuild services
```bash
docker-compose build
```

### Stop all services
```bash
docker-compose down
```

### Reset database (removes all data)
```bash
docker-compose down -v
docker volume rm recipe-app_postgres_data
```

## Network Configuration

All services run on a custom bridge network `recipe-network` for secure internal communication.

