# AI Planning Software Repository

A centralized platform for accessing AI planning software metadata, with features to discover, filter, sort, and add new software metadata.

## Master Thesis Report
For a complete overview of the research, please access the PDF [Design and implementation of a platform for discovering and sharing AI planning software](https://github.com/imsaurabh1/MasterThesis_Report/blob/main/MasterThesis_SaurabhAdhau.pdf).

## Prerequisites

- **Docker Desktop**  
  Docker Desktop is required to run the application in a containerized environment. It can be installed from the official [Docker website](https://docs.docker.com/desktop/).

### Note

To run the project correctly, please ensure that the following ports are free on your local system:

- **Port 3000**: It will be used by the frontend 
- **Port 5000**: It will be used by the backend

If these ports are already in use, you need to stop the other services or modify the `docker-compose.yml` file to use different ports.

## Steps to Run the Application

1. **Open Docker Desktop**  
   Make sure Docker Desktop is running before proceeding.

2. **Clone the Repository**  
   Clone the repository using the following command:  
   ```bash
   git clone <repository_url>
   ```

3. **Navigate to the Project Folder**  
   Move to the project directory with:  
   ```bash
   cd <project_folder>
   ```

4. **Start Docker Desktop**  
   If not already running, open Docker Desktop.

5. **Build and Start the Containers**  
   Use the following command to build and start the containers:  
   ```bash
   docker-compose up --build
   ``` 
   It may take a few minutes to set up the project completely. Once the backend has started successfully, you should see the following message in the console:  
   **backend  | Server is running on port 5000**  
   After this, you can access the application

6. **Access the Application**  
   Open a web browser and go to: [http://localhost:3000](http://localhost:3000)

## Optional Steps

### Running Test Cases

1. **Frontend Tests**  
   To run the frontend test cases, open a command prompt and type:  
   ```bash
   docker exec -it frontend npm test
   ```

2. **Backend Tests**  
   To run the backend test cases, use:  
   ```bash
   docker exec -it backend npm test
   ```

## Steps for Admin

1. **Login to the Database**  
   Open a command prompt and login to the database using the command:  
   ```bash
   docker exec -it mysql_db mysql -u root -p
   ```  
   When prompted, enter the password as `"admin"`.

2. **Manage Records in the Database**  
   The admin can read, delete, or modify records using the following commands. Note that the admin receives the software ID via email when a new record is added.

   - **Read Records**  
     To read the details of a specific record, use:  
     ```sql
     SELECT * FROM ai_tools.ai_planning_softwares WHERE id = "ID_value"\G
     ```

   - **Delete a Record**  
     To delete a specific record from the database, run:  
     ```sql
     DELETE FROM ai_tools.ai_planning_softwares WHERE id = "ID_value";
     ```

   - **Update a Record**  
     To update a specific record, you can use a command like:  
     ```sql
     UPDATE ai_tools.ai_planning_softwares
     SET column_name = 'new_value'
     WHERE id = "ID_value";
     ```

## Stopping and Restarting the Project

To stop the project, press `Ctrl+C` in the terminal where the project is running. This will stop all running containers.

If you want to remove the containers and associated networks after stopping the project, run the following command:
```bash
docker-compose down
```
To run the project again, simply use the following command:
```bash
docker-compose up
```


## Additional Project Information

- **Frontend**: 
   - The frontend is built using **React version 18.3.1** and **npm version 8.19.3**.
   - It utilizes both **standard CSS** and **Tailwind CSS** for styling.
   - **Material UI** components are used for input fields.
   - The frontend testing is done using **Jest** and **React Testing Library**.

- **Backend**: 
   - The backend is built using **Node.js version 18.13.0** and **npm version 8.19.3**.
   - It uses **Express** to handle API requests and **Nodemailer** for email functionality.
   - Backend testing is done using **Mocha**, **Chai**, **Sinon**, and **Supertest**.

- **Database**: 
   - The project uses **MySQL version 8.4.0** for managing the database.

- **Containerization**: 
   - The project uses **Docker version 27.2.0** and **Docker Compose version v2.29.2** for containerization.

