# eLearning Platform

## Project Overview

This eLearning platform enables teachers to create courses, upload materials, manage students, and facilitate real-time communication. Students can enroll in courses, access materials, leave feedback, and engage in real-time chat. Notifications are sent when new materials are uploaded or when students enroll in courses.

---

## Project Structure

```
eLearning_project/
┣ Backend/
┃ ┣ accounts/
┃ ┣ api/
┃ ┣ chat/
┃ ┣ core/
┃ ┣ courses/
┃ ┣ email_simulation/
┃ ┣ feedback/
┃ ┣ media/
┃ ┣ notifications/
┃ ┣ user_permissions/
┃ ┣ .env
┃ ┣ db.sqlite3
┃ ┣ manage.py
┃ ┣ pytest.ini
┃ ┗ requirements.txt
┣ Frontend/
┃ ┣ public/
┃ ┣ src/
┃ ┣ .browserslistrc
┃ ┣ .editorconfig
┃ ┣ .gitattributes
┃ ┣ .gitignore
┃ ┣ .prettierignore
┃ ┣ .prettierrc.js
┃ ┣ LICENSE
┃ ┣ eslint.config.mjs
┃ ┣ index.html
┃ ┣ package-lock.json
┃ ┣ package.json
┃ ┗ vite.config.mjs
┗ .gitignore
```

---

## Prerequisites

- **Python 3.12**
- **Node.js (latest stable version)**

---

## How to Run the Project

### Backend (Django)

1. Navigate to the `Backend` directory:
   ```sh
   cd Backend
   ```
2. Create and activate a virtual environment:
   ```sh
   python -m venv venv
   python3 -m venv venv # MacOS
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```
3. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
4. Start WebSockets and background tasks:
   ```sh
   daphne -b 127.0.0.1 -p 8000 core.asgi:application  # WebSockets
   redis-server # Redis 
   celery -A core worker --loglevel=info  # Background tasks
   ```
5. To approve a new user, run Django's default development server:

   ```sh
   python manage.py runserver 8080 # To access the admin panel

   and go to te admin panel: http://localhost:8080/admin/
   ```

6. Admin Credentials
   ```sh
   email: admin@email.com
   password: admin123
   ```

### Frontend (React + Vite)

1. Navigate to the `Frontend` directory:
   ```sh
   cd Frontend
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Start the development server:
   ```sh
   npm start
   ```

The frontend should be accessible at [http://127.0.0.1:3000](http://localhost:3000)  
The admin panel at [http://127.0.0.1:8080/admin/](http://localhost:8080/admin/)  
The Daphne server at [http://127.0.0.1:8000](http://localhost:8000)

---

## Demo Accounts

### Teachers:

email: testuser1@example.com  
password: testuser1

email: testuser2@example.com  
password: testuser2

email: teacher1@email.com  
password: teacher1

### Students:

email: student1@example.com  
password: student1

email: samsmith@email.com  
password: samsmith1

email: michaellynch@email.com  
password: michaellynch

email: testuser3@example.com  
password: testuser3

---

## How to Test the Application

### Backend Tests

`Important:` Make sure Daphne, Celery and Redis are running `before` running the tests

Run the following command in the `Backend` directory:

```sh
pytest
```

This will execute all Django tests, including API, serializers, and WebSocket tests.

---

## Notes

- API documentation: [http://127.0.0.1:8000/api/docs/](http://localhost:8000/api/docs/)
- Static files are not loaded by Daphne, therefore, run Django's development server to access the admin panel to approve a new user
- The WebSocket, Redis and Celery processes must be running for real-time notifications and background tasks to function properly.

---

## Author

Giuseppe Babino
