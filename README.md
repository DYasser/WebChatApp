# WebChatApp
<p align="center">A local web chat application where the users can chat together in a virtual chat.</p> 

## What I Used

To create this project I used [`Angular`](https://github.com/angular/angular) for all front-end tasks and [`NodeJs`](https://github.com/nodejs/node) for the back-end.

## How to run

Clone the repository using `git clone https://www.github.com/DYasser/WebChatApp` then set up angular and nodejs before opening the folder. Open the folder and run in git bash or any command-line interpreter the command `npm start` to start the nodeJs server, then type `npm start` or `ng serve` inside the client folder to run the angular server.

Finally, open `localhost:4200` in your browser to be able to see the chat and use it.

## Preview

Upon starting the program we get the main menu screen where only one input and button are there. The user needs to input a nickname with a maximum length of 7 characters.

Here a preview of what I stated just now.

![Main Menu Screenshot](https://github.com/DYasser/WebChatApp/blob/main/demo0.png)

After clicking on the **Chat** button, the user is directly being brought to the chat where he can input his messages and click on the green send button to send his messages.

The right of the screen is where the user can see who is online. 

I created a feature that makes the program know when it is the user that typed and when it is someone else. Using that feature, I am able to show all the user's messages to the right with a label `Me` to its left to show that it is his/her message. Meanwhile, they show the opposite for any other user that is messaging there. 

I avoided all the bugs such as sending a blank message or any other typical bugs like this one.

You can find below a demo of what I explained.

![Chat Screenshot](https://github.com/DYasser/WebChatApp/blob/main/demo.png)

## Creation process

