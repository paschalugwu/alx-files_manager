# 0x04. Files Manager

## Overview
This project aims to build a simple platform to upload and view files, integrating key back-end technologies such as Node.js, Express, MongoDB, Redis, and Kue for background processing. The primary features include user authentication, file management, and thumbnail generation.

### Team
- Paschal Ugwu
- Amarachi Nnanta

## Features
- **User Authentication**: Secure login system with token-based authentication.
- **File Management**: Upload, view, and manage files.
- **Permissions**: Control file access permissions.
- **Thumbnails**: Generate and view image thumbnails.

## Learning Objectives
- Create an API with Express.
- Authenticate users.
- Store data in MongoDB.
- Use Redis for temporary data storage.
- Implement background processing with Kue.

## Resources
- Node.js
- Express
- MongoDB
- Redis
- Mocha
- Bull
- Image Thumbnail
- Mime-Types

## Project Structure
```
├── utils
│   ├── redis.js
│   └── db.js
├── controllers
│   ├── AppController.js
│   ├── UsersController.js
│   ├── AuthController.js
│   └── FilesController.js
├── routes
│   └── index.js
└── server.js
```

## Tasks

### 1. Redis Utils
- **File**: `utils/redis.js`
- **Class**: `RedisClient`
  - **Constructor**: Initializes Redis client, handles errors.
  - **Methods**:
    - `isAlive()`: Checks if Redis connection is successful.
    - `get(key)`: Retrieves a value by key.
    - `set(key, value, duration)`: Stores a value with an expiration time.
    - `del(key)`: Deletes a value by key.

### 2. MongoDB Utils
- **File**: `utils/db.js`
- **Class**: `DBClient`
  - **Constructor**: Initializes MongoDB client with environment variables.
  - **Methods**:
    - `isAlive()`: Checks if MongoDB connection is successful.
    - `nbUsers()`: Counts documents in the `users` collection.
    - `nbFiles()`: Counts documents in the `files` collection.

### 3. First API
- **Files**: `server.js`, `routes/index.js`, `controllers/AppController.js`
- **Endpoints**:
  - `GET /status`: Returns Redis and MongoDB status.
  - `GET /stats`: Returns counts of users and files.

### 4. Create a New User
- **Files**: `routes/index.js`, `controllers/UsersController.js`
- **Endpoint**: `POST /users`
  - Creates a new user with email and password.
  - Validates input and handles errors.
  - Hashes the password with SHA1.
  - Stores user in the `users` collection.

### 5. Authenticate a User
- **Files**: `routes/index.js`, `controllers/AuthController.js`, `controllers/UsersController.js`
- **Endpoints**:
  - `GET /connect`: Generates authentication token.
  - `GET /disconnect`: Invalidates the token.
  - `GET /users/me`: Retrieves user information based on the token.

### 6. First File
- **Files**: `routes/index.js`, `controllers/FilesController.js`
- **Endpoint**: `POST /files`
  - Validates user token.
  - Handles file upload with various attributes.
  - Stores files in a specified folder and in the `files` collection.

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/paschalugwu/alx-files_manager.git
   ```
2. Navigate to the project directory:
   ```sh
   cd alx-files_manager
   ```
3. Install dependencies:
   ```sh
   npm install
   ```

## Running the Project
1. Start the server:
   ```sh
   npm run start-server
   ```

## Testing
1. Run tests:
   ```sh
   npm run test
   ```

## Contributing
1. Fork the repository.
2. Create a new branch:
   ```sh
   git checkout -b feature-name
   ```
3. Commit your changes:
   ```sh
   git commit -m 'Add some feature'
   ```
4. Push to the branch:
   ```sh
   git push origin feature-name
   ```
5. Open a pull request.

## License
This project is licensed under the MIT License.

## Acknowledgements
- ALX Africa
- Team Members: Paschal Ugwu, Amarachi Nnanta

---

This README provides a concise and clear overview of the project's objectives, structure, tasks, and usage instructions. For detailed implementation, refer to the individual files mentioned in each task section.
