# MariaDB Docker Compose Setup  
   
This repository contains a Docker Compose file for setting up a MariaDB version 10.1.48 instance using Docker.  
   
## Prerequisites  
   
- Docker  
- Docker Compose  
   
## Setup  
   
1. Clone this repository to your local machine.  
   
2. Navigate to the project directory.  
   
3. Create a `.env` file in the project directory to store your environment variables. This file should contain the following:  
   
```  
MYSQL_ROOT_PASSWORD=your_root_password  
MYSQL_DATABASE=your_database_name  
MYSQL_USER=your_username  
MYSQL_PASSWORD=your_password  
```  
   
Replace `your_root_password`, `your_database_name`, `your_username` and `your_password` with your actual root password, database name, username and password respectively.  
   
4. Run the Docker Compose file:  
   
```  
docker-compose up -d  
```  
   
The `-d` flag is for running the containers in detached mode, which means that the containers run in the background and won't display logs in the console.  
   
This will pull the MariaDB 10.1.48 image from Docker Hub, if it's not already present on your machine, and will start a MariaDB container.  
   
The container's port 3306 is mapped to your machine's port 3306, so you can connect to your database on `localhost:3306`.  
   
Your MariaDB data is stored in a Docker volume named `mariadb_data`.  
   
## Connect to the database  
   
You can connect to your database using MariaDB command line client or a database management tool like MySQL Workbench or DBeaver.  
   
The following are the details you will need:  
   
- Hostname: `localhost`  
- Port: `3306`  
- User: The username you specified in the `.env` file.  
- Password: The password you specified in the `.env` file.  
- Database: The database name you specified in the `.env` file.  
   
## Stop the containers  
   
To stop the containers, run:  
   
```  
docker-compose down  
```  
   
This will stop and remove the containers, but your data will persist in the `mariadb_data` volume. To also remove the volumes, add the `--volumes` or `-v` flag:  
   
```  
docker-compose down --volumes  
```