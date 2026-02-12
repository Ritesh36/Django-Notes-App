## Production Deployment Guide

This project is a full-stack notes application using Django (backend API), React (frontend), and Nginx as a reverse proxy, all containerized with Docker and orchestrated using Docker Compose.

### Prerequisites
- Docker and Docker Compose installed on your server or production environment.

### Deployment Steps

1. **Clone the repository:**
	```sh
	git clone <your-repo-url>
	cd django-notes-app-main
	```

2. **Build and start the containers:**
	```sh
	docker-compose up --build -d
	```
	This will build and start three containers:
	- `mysql`: MySQL database
	- `django_cont`: Django backend (with Gunicorn)
	- `nginx`: Nginx reverse proxy

3. **Access the application:**
	- Open your browser and go to: [http://localhost:80/](http://localhost:80/)

### Notes
- Nginx listens on port 80 and proxies requests to the Django backend.
- Django serves the React build and API endpoints.
- Static files are collected and served from the `staticfiles/` directory.
- Database data is persisted in a Docker volume (`mysql-data`).

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
For troubleshooting, ensure all containers are running and healthy:
```sh
docker ps
```
