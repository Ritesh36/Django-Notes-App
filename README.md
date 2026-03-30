
# Notes App Production Deployment

This project was created by **Ritesh**. It is a full-stack notes application using Django (backend API), React (frontend), and Nginx as a reverse proxy, all containerized with Docker and orchestrated using Docker Compose.

## Production Deployment

Follow these steps to deploy the application in a production environment:

### Prerequisites
- Docker and Docker Compose must be installed on your server.

### Deployment Flow
1. **Clone the repository**
	```sh
	git clone <your-repo-url>
	cd django-notes-app-main
	```

2. **Build and start all services**
	```sh
	docker-compose up --build -d
	```
	This command will:
	- Build the Docker images for Django, Nginx, and MySQL
	- Start all containers in detached mode

3. **Verify all containers are running**
	```sh
	docker ps
	```
	You should see containers for `nginx`, `django_cont`, and `mysql`.

4. **Access the application**
	- Open your browser and go to: [http://localhost:80/](http://localhost:80/)

### Useful Commands
- View logs for a service:
  ```sh
  docker logs <service-name>
  ```
- Stop all containers:
  ```sh
  docker-compose down
  ```

---
**Deployment Summary:**
- Nginx listens on port 80 and proxies requests to the Django backend.
- Django serves the React build and API endpoints.
- Static files are served from the `staticfiles/` directory.
- Database data is persisted in a Docker volume (`mysql-data`).

---
**Project by Ritesh**
