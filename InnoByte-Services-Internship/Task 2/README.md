# Node.js Project with MongoDB and NodeMailer


## Table of Contents
- Project Overview
- Features
- Technologies Used
- Installation
- Running the Project
- Connecting to MongoDB
- API Endpoints
- Project Structure
- Screenshots
- License

## Project Overview
- This project is a Node.js application using MongoDB for data storage and NodeMailer for sending confirmation emails upon user signup.

-  The project includes user authentication endpoints for signup, login, and user profile.

## Features
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
- Clone the repository:

```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```
### Install dependencies:

```bash
npm install
```
### Set Up Environment Variables:

Create a .env file in the root directory and add your MongoDB URI and NodeMailer configuration. For example:
```bash
MONGODB_URI=your-mongodb-uri
NODEMAILER_USER=your-email@example.com
NODEMAILER_PASS=your-email-password
```


## Running the Project
Start the Server:

To start the Node.js server, run:

```sh
npm start
```

The server will run on http://localhost:4500.

Test the Endpoints:

- Signup: POST /api/signup
- Login: POST /api/login
- Profile: GET /api/profile

## Connecting to MongoDB
To connect to MongoDB, ensure you have a MongoDB URI set in your .env file. The URI should point to your MongoDB instance.


## Using NodeMailer
NodeMailer is used to send emails from your Node.js application. Here's a brief overview of how to set it up:

### Install NodeMailer:

```sh
npm install nodemailer
```


### Configure NodeMailer:
In your Node.js project, set up NodeMailer with your email service provider. For example:

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
  from: 'your-email@example.com',
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

### Trigger Email on Signup:
Extend the /api/signup endpoint to send a confirmation email upon successful registration.


## Project Structure

The project structure is organized as follows:

```arduino
Copy code
your-repo-name/
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
