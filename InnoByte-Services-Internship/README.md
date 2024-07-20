# InnoByte-Services-Internship :
## Task 1 - Node.js Authentication API & Task 2 - Email Confirmation

- Welcome to the Node.js Authentication API and Email Confirmation project!
- This repository contains two distinct yet related tasks:
- a Node.js API for user authentication and a project demonstrating email confirmation with NodeMailer.
- Below, you'll find comprehensive documentation covering both tasks, including setup instructions, features, technologies used, and more.

## Table of Contents
- Project Overview
- Features
- Technologies Used
- Installation
- Running the Project
- Connecting to MongoDB
- Using NodeMailer
- API Endpoints
- Project Structure
- Screenshots
- License

## Project Overview
This repository includes two main tasks:

### Task 1 - Node.js Authentication API
- A Node.js API built with Express.js for user authentication, including signup, login, and profile management.
- It utilizes MongoDB for data storage and JWT for secure authentication.

### Task 2 - Node.js Project with MongoDB and NodeMailer
- An extension of Task 1 that includes email confirmation functionality using NodeMailer.
- This task demonstrates how to send confirmation emails upon user signup, providing a complete user authentication and verification workflow.

## Features

### Task 1:
- User signup with username, email, and password
- Password hashing for enhanced security
- User login with JWT token generation
- Protected user profile endpoint
- Input validation

### Task 2:
- User authentication (signup, login, profile)
- Sending confirmation emails upon signup
- JWT token generation and validation
- Input validation and password hashing

## Technologies Used
- Node.js
- Express.js
- MongoDB
- Mongoose
- NodeMailer
- JSON Web Tokens (JWT)
- bcrypt

## Installation
To set up the project on your local machine, follow these steps:

- Clone the Repository:

```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```

- Install Dependencies:

```bash
npm install
```

### Running the Project
- Set Up Environment Variables:

Create a .env file in the root directory and add the following variables:

```env
MONGODB_URI=your_mongodb_uri
JWT_SECRET=your_secret_key
NODEMAILER_USER=your-email@example.com
NODEMAILER_PASS=your-email-password
```

- Start the Server:

```bash
npm start
```

The server will run on http://localhost:4500 by default.

## Connecting to MongoDB
- Ensure you have a MongoDB URI set in your .env file.
- This URI should point to your MongoDB instance.
- If you don't have a MongoDB cluster, you can create one at MongoDB Atlas.

### Using NodeMailer
NodeMailer is used to send emails from your Node.js application.

Follow these steps to configure it:

- Install NodeMailer:

```bash
npm install nodemailer
```

- Configure NodeMailer:

```js
const nodemailer = require('nodemailer');

const transporter = nodemailer.createTransport({
  service: 'gmail',
  auth: {
    user: process.env.NODEMAILER_USER,
    pass: process.env.NODEMAILER_PASS,
  },
});

const mailOptions = {
  from: process.env.NODEMAILER_USER,
  to: 'user-email@example.com',
  subject: 'Confirmation Email',
  text: 'Your confirmation code is XYZ123',
};

transporter.sendMail(mailOptions, (error, info) => {
  if (error) {
    console.log(error);
  } else {
    console.log('Email sent: ' + info.response);
  }
});
```

- Trigger Email on Signup:

Extend the /api/signup endpoint in Task 1 to send a confirmation email upon successful registration.

## API Endpoints
### Task 1 - Authentication API
 User Signup: /api/signup

Method: POST
Body: { "username": "your_username", "email": "your_email", "password": "your_password" }

User Login: /api/login

Method: POST
Body: { "email": "your_email", "password": "your_password" }

User Profile: /api/profile

Method: GET
Headers: { "Authorization": "Bearer <your_jwt_token>" }

### Task 2 - Email Confirmation

Extend the Task 1 API with email confirmation functionality.

## Project Structure

```arduino
your-repo-name/
├── Task 1/
│   ├── Project 1 SS/
│   ├── public/
│   ├── src/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── routes/
│   │   └── utils/
│   ├── views/
│   ├── .env
│   ├── app.js
│   └── package.json
└── Task 2/
    ├── models/
    │   └── User.js
    ├── routes/
    │   └── auth.js
    ├── views/
    │   └── home.ejs
    ├── .env
    ├── app.js
    ├── package.json
    └── README.md
```



## License

This project is licensed under the MIT License. See the LICENSE file for details.
