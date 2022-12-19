# How to fix the "Unable to type in input" issue in React

Hello World!

When we work with forms in React, we may encounter an issue where we won't be able to type in the input field/text box if the `value` property is set. I would be showing what is the actual issue and how I fixed it.

## Scenario

### Requirement

I have an API, which would require three fields namely Email, Name and Message, which need to be passed in the body of the API. In the UI, we would be getting those values in an input field or text area and would be using a button to trigger the API call.

The structure expected in the API is something like this:

```json
{
"email": "testxyz@test.com",
"name": "Test",
"message": "Hi, this is a test message."
}
```

### Implementation

In the React app, I've created a component with 2 input fields for getting the `name` and `email`, a text area for getting the `message` and a button to trigger the API call and send the 3 values. This is what the component looked like:

```javascript
import { useState } from "react";
import callApi from "../axios/axios";
import "./contact.scss";
const Contact = () => {
  const payloadInitial = {
    sender: "",
    email: "",
    message: "",
  };
  const initialClass = "form-input";
  const [payload, setPayload] = useState(payloadInitial);
  // Captures Sender name
  const setName = (name) => {
    const temp = payload
    temp.sender = name
    setPayload(temp)
  };
  // Captures Email
  const setEmail = (email) => {
    const temp = payload
    temp.email = email
    setPayload(temp)
  };
  // Captures Message
  const setMessage = (message) => {
    const temp = payload
    temp.message = message
    setPayload(temp)
    checkCanSend();
  };
  // Triggers API call on button click
  const sendMessage = (evt) => {
    evt.preventDefault();
    callApi
      .post("/email", payload)
      .then((res) => {
        console.log("Response: ", res)
      })
      .catch((err) => {
        console.error("Something went wrong: ", err)
      });
  };
  return (
    <div className="form-container">
      <h2 className="form-title">Write to me</h2>
      <div className="form-container">
        <!--Input to get sender name-->
        <label>Your Name</label>
        <input
          type={"text"}
          aria-label="Your Name"
          value={payload.sender}
          onChange={(e) => setName(e.target.value)}
        ></input>
        <!--Input to get sender email-->
        <label>Your Email</label>
        <input
          type={"email"}
          aria-label="Your Email"
          value={payload.email}
          onChange={(e) => setEmail(e.target.value)}
        ></input>
        <!--Textbox to get the message-->
        <label>Type in your message</label>
        <textarea
          rows={8}
          value={payload.message}
          onChange={(e) => setMessage(e.target.value)}
        ></textarea>
        <!--Button to trigger API call-->
        <button onClick={(e) => sendMessage(e)} className="send-button">
          Send Message
        </button>
      </div>
    </div>
  );
};

export default Contact;
```

In the above component, we are listening to the change of input fields using the `onChange` event and setting the new values to the `payload` state.

## Issue

The above code was causing an issue, where I was not able to type more than one character.

![Issue with input field, where it was accepting only one character.](https://cdn.hashnode.com/res/hashnode/image/upload/v1670076356808/o6kBSWZ5x.gif align="center")

## Solution

The solution for the issue is: In the onClick function, instead of storing the state in a temp variable, changing the value in the temp and setting temp to the state, we should **update the state directly**.

In our case, let us consider the `setName` function. The function should be changed like this:

```javascript
const setName = (name) => {
    setPayload((prev) => ({
      ...prev,
      sender: name,
    }));
    checkCanSend();
  }
```

Now the state is updated directly, without having any temp variables.

Now we can type on the input field.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1670077209221/pxklNdObF.gif align="left")

The final code would be:

```javascript
import { useState } from "react";
import callApi from "../axios/axios";
import "./contact.scss";
const Contact = () => {
  const initialClass = "form-input";
  const [payload, setPayload] = useState(payloadInitial);
  // Captures Sender name
  const setName = (name) => {
    setPayload((prev) => ({
      ...prev,
      sender: name,
    }));
    checkCanSend();
  };
  // Captures Email
  const setEmail = (email) => {
    setPayload((prev) => ({
      ...prev,
      email,
    }));
    checkCanSend();
  };
  // Captures Message
  const setMessage = (message) => {
    setPayload((prev) => ({
      ...prev,
      message,
    }));
    checkCanSend();
  };
  // Triggers API call on button click
  const sendMessage = (evt) => {
    evt.preventDefault();
    callApi
      .post("/email", payload)
      .then((res) => {
        console.log("Response: ", res)
      })
      .catch((err) => {
        console.error("Something went wrong: ", err)
      });
  };
  return (
    <div className="form-container">
      <h2 className="form-title">Write to me</h2>
      <div className="form-container">
        <!--Input to get sender name-->
        <label>Your Name</label>
        <input
          type={"text"}
          aria-label="Your Name"
          value={payload.sender}
          onChange={(e) => setName(e.target.value)}
        ></input>
        <!--Input to get sender email-->
        <label>Your Email</label>
        <input
          type={"email"}
          aria-label="Your Email"
          value={payload.email}
          onChange={(e) => setEmail(e.target.value)}
        ></input>
        <!--Textbox to get the message-->
        <label>Type in your message</label>
        <textarea
          rows={8}
          value={payload.message}
          onChange={(e) => setMessage(e.target.value)}
        ></textarea>
        <!--Button to trigger API call-->
        <button onSubmit={(e) => sendMessage(e)} className="send-button">
          Send Message
        </button>
      </div>
    </div>
  );
};

export default Contact;
```

Hope this solution is helpful to fix the "Unable to type in the input field" issue. Looking forward to your feedback. Thank you!