# Event Management REST API


### Steps

1. Install dependencies:
    ```bash
    npm install
    ```

2. Set up environment variables:

3. Start the server:
    ```bash
    npm start
    ```



---

## API Endpoints

### User Endpoints

- **Sign Up**
  - `POST /api/users/signup`

- **Login**
  - `POST /api/users/login`

- **View Profile**
  - `GET /api/users/profile`


### Event Endpoints

- **Create an Event**
  - `POST /api/events`

- **Get All Events**
  - `GET /api/events`

- **Get Event by ID**
  - `GET /api/events/:id`

- **Update Event**
  - `PATCH /api/events/:id`

- **Delete Event**
  - `DELETE /api/events/:id`

### RSVP Endpoints

- **RSVP to Event**
  - `POST /api/events/:id/rsvp`

- **Get User's RSVP Events**
  - `GET /api/users/my-events`
