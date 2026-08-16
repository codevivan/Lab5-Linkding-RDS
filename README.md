# Lab 5 – Deploy and Connect Database for Lab 4 EC2 Application

## Project
Linkding Bookmark Manager deployed on Amazon EC2 and connected to Amazon RDS PostgreSQL.

## Architecture

User
  |
  v
Public EC2 IP
  |
  v
Nginx Reverse Proxy
  |
  v
Linkding Docker Container
  |
  v
Amazon RDS PostgreSQL

## Technologies Used

- Amazon EC2
- Amazon RDS PostgreSQL
- Docker
- Docker Compose
- Nginx
- Linkding
- PostgreSQL

## Database Configuration

Database Engine: PostgreSQL

Database Name: linkding

Database User: linkding_admin

Database Port: 5432

The RDS database is connected privately to the EC2 instance.

## EC2 Application

The Linkding application runs inside a Docker container on the EC2 instance.

The application is exposed through Nginx and accessed using the EC2 public IP address.

## Database Connection

The Linkding application was configured using environment variables:

- LD_DB_ENGINE=postgres
- LD_DB_DATABASE=linkding
- LD_DB_USER=linkding_admin
- LD_DB_HOST=<RDS-ENDPOINT>
- LD_DB_PORT=5432
- LD_DB_OPTIONS={"sslmode":"require"}

Database credentials are stored in `.env` and are NOT uploaded to GitHub.

## CRUD Operations

All CRUD operations were successfully demonstrated from the running EC2 application.

### Create
Created new bookmarks through the Linkding application.

### Read
Viewed existing bookmarks stored in the RDS PostgreSQL database.

### Update
Modified bookmark information through the application.

### Delete
Deleted bookmarks through the application.

## Security

The RDS Security Group allows PostgreSQL traffic on port 5432 only from the EC2 Security Group.

Public access from `0.0.0.0/0` is not allowed.

The EC2 application is accessible through the public IP address, while the RDS database remains private.

## Verification

Database connectivity was verified using PostgreSQL commands.

The Linkding health endpoint returned:

`{"version": "1.45.0", "status": "healthy"}`

The application was successfully accessed through the EC2 public IP.

## Repository Contents

- README.md – Project documentation
- docker-compose.yml – Docker deployment configuration
- .gitignore – Prevents sensitive files from being uploaded

## Conclusion

The Lab 4 Linkding application was successfully connected to Amazon RDS PostgreSQL. The application performs Create, Read, Update and Delete operations using the deployed RDS database while maintaining database security through EC2 Security Group based access.
