# Event Management REST API


### Prerequisites

- Install [Node.js](https://nodejs.org/) (v16 or higher recommended)
- Install [MongoDB](https://www.mongodb.com/try/download/community) or use a cloud service like [MongoDB Atlas](https://www.mongodb.com/atlas/database)

### Steps

1. Clone the repository:
    ```bash
    git clone <repository_url>
    cd event-management-api
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Set up environment variables:
    - Create a `.env` file in the root directory.
    - Add the following environment variables:
      ```env
      PORT=5000
      MONGO_URI=<your_mongodb_connection_string>
      JWT_SECRET=<your_jwt_secret>
      ```

4. Start the server:
    ```bash
    npm start
    ```

5. For development with auto-restart:
    ```bash
    npx nodemon server.js
    ```

---

## API Endpoints

### User Endpoints

- **Sign Up**
  - `POST /api/users/signup`
  - **Body:**
    ```json
    {
      "name": "John Doe",
      "email": "john@example.com",
      "password": "password123"
    }
    ```

- **Login**
  - `POST /api/users/login`
  - **Body:**
    ```json
    {
      "email": "john@example.com",
      "password": "password123"
    }
    ```
  - **Response:**
    ```json
    {
      "token": "your_jwt_token"
    }
    ```

- **View Profile**
  - `GET /api/users/profile`
  - **Header:** `Authorization: Bearer <token>`

### Event Endpoints

- **Create an Event**
  - `POST /api/events`
  - **Header:** `Authorization: Bearer <token>`
  - **Body:**
    ```json
    {
      "name": "Wildlife Seminar",
      "description": "A seminar about wildlife preservation.",
      "date": "2024-12-10",
      "time": "10:00 AM",
      "location": "Auditorium",
      "maxAttendees": 50
    }
    ```

- **Get All Events**
  - `GET /api/events`
  - **Query Parameters (Optional):** `location`, `date`

- **Get Event by ID**
  - `GET /api/events/:id`

- **Update Event**
  - `PATCH /api/events/:id`
  - **Header:** `Authorization: Bearer <token>`
  - **Body:** (Fields to update)

- **Delete Event**
  - `DELETE /api/events/:id`
  - **Header:** `Authorization: Bearer <token>`

### RSVP Endpoints

- **RSVP to Event**
  - `POST /api/events/:id/rsvp`
  - **Header:** `Authorization: Bearer <token>`

- **Get User's RSVP Events**
  - `GET /api/users/my-events`
  - **Header:** `Authorization: Bearer <token>`

---

## Hosting on Heroku

1. Install the Heroku CLI:
    ```bash
    npm install -g heroku
    ```

2. Log in to Heroku:
    ```bash
    heroku login
    ```

3. Create a new Heroku app:
    ```bash
    heroku create
    ```

4. Add environment variables to Heroku:
    ```bash
    heroku config:set MONGO_URI=<your_mongodb_connection_string>
    heroku config:set JWT_SECRET=<your_jwt_secret>
    ```

5. Deploy your app:
    ```bash
    git add .
    git commit -m "Initial deployment"
    git push heroku main
    ```

6. Access your app:
    - Visit the URL provided by Heroku after deployment.

---

## Testing

Use [Postman](https://www.postman.com/) to test the API endpoints. Make sure to include the **Authorization** header with your JWT token for protected routes.

---

## Troubleshooting

- **MongoDB Connection Error:** Verify your `MONGO_URI` in the `.env` file or Heroku settings.
- **Invalid Token Error:** Ensure you’re passing the JWT token in the `Authorization` header.
- **Port Conflict:** Ensure the `PORT` in `.env` doesn’t conflict with other services.

---

## License

This project is licensed under the MIT License.
