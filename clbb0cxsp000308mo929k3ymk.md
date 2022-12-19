# How to send emails with API?

Hello World!

Let us see how we can send emails just by calling an API.

# Prerequisites

1.  Fundamental knowledge of Javascript, Node.js, and Express.js.
    
2.  Gmail Account
    
3.  Node
    
4.  Editor of your choice (E.g. VS Code)
    
5.  Postman (To test the API)
    

# Gmail Configuration

To send emails from API, we need to configure Gmail with the below things:

*   Headover to [https://myaccount.google.com/security](https://myaccount.google.com/security)
    
*   Enable 2-step verification.
    
*   Click on App passwords.
    
*   Google would prompt you for your password. Type in your password and enter.
    
*   Select `Other (Custom Name)` in the "Select App" drop-down.
    
*   Provide a name and click on `Generate` button.
    
*   You will be getting a password. Store it in a safe place.
    

# Server

Let us create a simple express server, where we will be creating our API that sends an email

```bash
yarn init -y
# OR
npm init -y
```

Install the following dependencies

*   Express
    
*   Dotenv - Where we will be storing the password and sender email address
    
*   Nodemailer - An NPM package to send emails.
    
*   Body-parser
    

```bash
yarn add express dontenv nodemailer body-parser
```

Let's create a `.env` file in the root level to store sensitive data

```bash
PORT = 4000
EMAIL = "youremail@yourdomain.com"
EMAIL_PASS = "your_password"
```

Now let's write a basic express server which serves some static content. Create `server.js` file and add the following

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const nodemailer = require('nodemailer');
const app = express();
app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());

app.get('/', (req, res) => {
  res.send('The server is running');
});
app.listen(process.env.PORT || 4000, () => console.log('Backend is running on localhost:4000'));
```

Now we have written a simple get request, that would print `The server is running` message when we hit the `/` path.

Type `node server` in the terminal to run the application. The app would run in `localhost:4000` . Open it in the browser, you would be seeing the `"The server is running"` message in the browser. Now we've successfully set up an express server.

# The Send Email API

Now let's create an API for sending emails. Create a post request, get necessary details like subject, message and recipient email from the request body, create a node mailer instance and send the email.

```javascript
app.post('/send-email', (req,res)=>{
  const mailTransporter = nodemailer.createTransport({
    service: 'gmail',
    // getting sender email and password from .env file
    auth: {
        user: process.env.EMAIL,
        pass: process.env.EMAIL_PASS
    }
  });
  
  // Getting the recipient email, subject and the message from the req body
  const mailDetails = {
    from: process.env.EMAIL,
    to: req.body.to,
    subject: req.body.subject,
    text: req.body.message
  };
  // Sending email through the node mailer
  mailTransporter.sendMail(mailDetails, (err, data) => {
    if(err) {
        // Returning the error message in case of any errors
        res.send(err)
    } else {
        // Returning Success message when email is sent successfully
        res.send(`Email sent successfully to ${req.body.to}`)
    }
});
})
```

The final code would be

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const nodemailer = require('nodemailer');
const app = express();
app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());

app.get('/', (req, res) => {
  res.send('The server is running');
});

app.post('/send-email', (req,res)=>{
  const mailTransporter = nodemailer.createTransport({
    service: 'gmail',
    // getting sender email and password from .env file
    auth: {
        user: process.env.EMAIL,
        pass: process.env.EMAIL_PASS
    }
  });
  
  // Getting the recipient email, subject and the message from the req body
  const mailDetails = {
    from: process.env.EMAIL,
    to: req.body.to,
    subject: req.body.subject,
    text: req.body.message
  };
  // Sending email through the node mailer
  mailTransporter.sendMail(mailDetails, (err, data) => {
    if(err) {
        // Returning the error message in case of any errors
        res.send(err)
    } else {
        // Returning Success message when email is sent successfully
        res.send(`Email sent successfully to ${req.body.to}`)
    }
});
})

app.listen(process.env.PORT || 4000, () => console.log('Backend is running on localhost:4000'));
```

# Testing API

Now we are done with writing the API. Let's run the server and send an email.

Once the server is up, head over to the Postman app. Create a new Post request.

Enter `localhost:4000/send-email` in the URL bar.

Head over to the 'Body' tab, and click on the 'raw' radio button. Type in the details in JSON format like this.

```json
{
    "to": "receiver@someemail.com",
    "subject": "This is a test email",
    "message": "Hi, I've sent this email from an API!"
}
```

Hit the send button to send the message.

![Testing the API in Postman](https://cdn.hashnode.com/res/hashnode/image/upload/v1670257430679/udlF6pbiA.png align="left")

![Received email](https://cdn.hashnode.com/res/hashnode/image/upload/v1670257469575/KkM27YK4Z.jpg align="left")

Hope this is helpful to you. Looking forward to your feedback. Thank you!