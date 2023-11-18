---
title: "How to host your webpage in Firebase?"
datePublished: Fri Apr 28 2017 10:18:47 GMT+0000 (Coordinated Universal Time)
cuid: clp3rf2zg000208l8hwbnhrdc
slug: how-to-your-webpage-in-firebase
canonical: https://medium.com/@Sriram23/how-to-your-webpage-in-firebase-666fed4fc129
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/JVSgcV8_vb4/upload/615e00426f9bf95229f456702969f3c5.jpeg
tags: hosting, firebase, web-development, firebase-hosting, hosting-webpage

---

Hello World!

In this article, let's see how we can deploy our web application using Firebase.

To start with, first check whether `npm` is installed in your computer. To check, just type the below command in your terminal Window.

```bash
npm --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066055985/LjQTHml5Kj.png align="left")

If you don't have firebase tools in your computer, install it through the following command

```bash
npm install –g firebase-tools
```

Next, we have to create an application in [Firebase](http://console.firebase.google.com).

If you have an account in firebase, just login to the console. Else create one here

> [console.firebase.google.com](http://console.firebase.google.com)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066057314/YgzT9zBAN.png align="left")

Signing in to Firebase

Next, create a new project in Firebase. Name it and select country.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066058559/Eeof1rfEK.png align="left")

Creating a new project in Firebase

Now, come back to the terminal and move to the destination, where your webpage is situated.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066059847/xmLLwH73Y.png align="left")

Moved to the destination of Web page I have already created

Now we have to login into firebase. Use the command for login to firebase

```bash
firebase login
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066061159/2cBOCsaqa.png align="left")

When the command is given, it redirects to your browser

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066062590/3tGkuaRat.png align="left")

Click Allow to access your firebase through terminal

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066064316/4HcFhUWBo.png align="left")

Now we have successfully logged in to firebase. Now let’s host our webpage in Firebase

Enter the below command

```bash
firebase init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066065701/u5uMvE1ZL.png align="left")

Select the HOSTING option

Select the project that we have created .

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066066974/tQU-YJgga.png align="left")

Selecting the project

> What file should be used for Database Rules? database.rules.json

For this just hit the Enter key.

> Do you want to install dependencies with npm now? (Y/n)

For this give ‘yes’ (y)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066068722/6B6-15ApX.png align="left")

After installing required, it prompts for What do you want to use as your public directory? (public). For this just give any name (like www).

> What do you want to use as your public directory? (public)

Move the webpage files into the folder that we have created(www).

> Configure as a single-page app (rewrite all urls to /index.html)?

For this give *NO.*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066070273/E1tnnj5i6.png align="left")

Now the initialization process is completed. Now we have to deploy the website.

```bash
firebase deploy
```

Now the webpage is successfully deployed and link is displayed in the console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066071754/OAZxZ5K1b.png align="left")

Now, open the browser and enter the URL. The site will appear.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672066073121/4hX31vJ7u8.png align="left")

Hope this is useful to you. Let me know what you think in the comments.