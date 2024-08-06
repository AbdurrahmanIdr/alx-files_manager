# File Manager Project

## Description
This project is a backend application that provides a platform to upload, manage, and view files. It includes features such as user authentication, file management, and background processing. The project is built using Node.js, Express, MongoDB, Redis, and Kue for background jobs.

## Features
1. **User Authentication**
   - User authentication via a token.
   - Create new users.
   - Authenticate users and provide session tokens.

2. **File Management**
   - List all files.
   - Upload new files (supports files and images).
   - Change file permissions.
   - View files.
   - Generate thumbnails for images.

3. **Background Processing**
   - Background jobs using Kue for tasks such as thumbnail generation.

## Technologies Used
- **Node.js**: JavaScript runtime for building server-side applications.
- **Express**: Web framework for Node.js.
- **MongoDB**: NoSQL database for storing user and file data.
- **Redis**: In-memory data structure store for caching and session management.
- **Kue**: Priority job queue for Node.js backed by Redis.
- **Mocha**: Testing framework for JavaScript.
- **ESLint**: Tool for identifying and reporting on patterns in JavaScript.

## Project Structure
- **utils/redis.js**: Redis client for caching and session management.
- **utils/db.js**: MongoDB client for database operations.
- **server.js**: Main server file to set up the Express server.
- **routes/index.js**: Defines all API routes.
- **controllers/AppController.js**: Controller for basic app status and stats.
- **controllers/UsersController.js**: Controller for user-related operations.
- **controllers/AuthController.js**: Controller for authentication operations.
- **controllers/FilesController.js**: Controller for file-related operations.

## Installation and Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/AbdurrahmanIdr/alx-files_manager.git
   cd alx-files_manager
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up environment variables:
   ```bash
   cp .env.example .env
   ```

4. Update the `.env` file with your configuration:
   ```env
   DB_HOST=localhost
   DB_PORT=27017
   DB_DATABASE=files_manager
   REDIS_HOST=localhost
   REDIS_PORT=6379
   PORT=5000
   FOLDER_PATH=/tmp/files_manager
   ```

5. Start the server:
   ```bash
   npm start
   ```

## Usage
### Endpoints
- **GET /status**: Check if Redis and MongoDB are alive.
- **GET /stats**: Get the number of users and files in the database.
- **POST /users**: Create a new user.
- **GET /connect**: Authenticate a user and generate a session token.
- **GET /disconnect**: Sign out a user.
- **GET /users/me**: Retrieve the authenticated user's information.
- **POST /files**: Upload a new file.
- **GET /files/:id**: Retrieve a file by ID.
- **GET /files**: List all files.

### Example Requests
1. **Create a New User**:
   ```bash
   curl -X POST -H "Content-Type: application/json" -d '{"email": "test@example.com", "password": "password123"}' http://localhost:5000/users
   ```

2. **Authenticate a User**:
   ```bash
   curl -X GET -H "Authorization: Basic dGVzdEBleGFtcGxlLmNvbTpwYXNzd29yZDEyMw==" http://localhost:5000/connect
   ```

3. **Upload a File**:
   ```bash
   curl -X POST -H "X-Token: YOUR_TOKEN" -H "Content-Type: application/json" -d '{"name": "myfile.txt", "type": "file", "data": "base64_encoded_content"}' http://localhost:5000/files
   ```

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Authors
- **Almeida Idris** - [Your GitHub Profile](https://github.com/AbdurrahmanIdr)
