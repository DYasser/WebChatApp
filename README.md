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

As I said earlier, I created this project using `Angular` and `NodeJs`. So, all the code that is going to be displayed is either `JavaScript`, `TypeScript`, `Html`, or `CSS`.

```html
<app-username (userNameEvent)="userNameUpdate($event)" *ngIf="!userName"></app-username>
```

I first created using `Angular`'s feature to use the *app-username* route if there was no username inputted yet.

I then coded the *app-username* page creating and centering both the input and the button that enters the user into the website when entering a valid username. 

So, going back to the first code. When the username isn't empty the page doesn't show the *app-username* page but instead this:

```html
<div class="container" *ngIf="userName">
    <h4 class="nametag">Welcome {{userName}}</h4>
    <h1 class="title">Chat App</h1>
    <div class="chatbox row">
        <div class="message_list">
            [...]
        </div>
        <div class="chatbox_user-list column">
            <h2 class="head" style="text-align: center;">Online</h2>
            <div class="chatbox_user--active" *ngFor="let user of userList">
                <p>{{user}}</p>
            </div>
        </div>
    </div>
    <input type="text" [(ngModel)]="message">
    <button (click)="sendMessage()">Send</button>
</div>
```

We can see here the welcome message that is going to be displayed top right with the username. Then, I sliced the screen into two spaces: one for the messages, and one showing the online users using an ngFor loop that goes through all the users in an userlist.

```typescript
sendMessage():void {
  this.socket.emit('message', this.message);
  if(/\S/.test(this.message)){
    this.messageList.push({message: this.message, userName: this.userName, mine:true});
    this.message = '';
  }
}
```

I used `socket` to send messages and show them to all users. `socket.io-client` is a special library that can be used like I did here in order to send messages. I also tested the message to see if it is not blank. In case it was blank there will be nothing sent and the user would need to type something and just then he would be able to send a message.

I added a flag called `mine` that helps understand what message is what user's.

```html
<div class="message_list">
    <div class="chatbox_messages column" *ngFor="let msg of messageList" [ngClass]="{mine: msg.mine}" >
        <div class="user-message">
            <div class="message-box" *ngIf="msg.mine">
                <p class="name"> Me</p>
                <p class="message">{{msg.message}}</p>
            </div>
            <div class="message-box" *ngIf="!msg.mine">
                <p class="name-others"> {{msg.userName}}</p>
                <p class="message-others">{{msg.message}}</p>
            </div>
        </div>
    </div>
</div>
```

as shown in the code above, I used an ngIf statement to see whether a message was mine or not. In order to get that special look and make the user knows what are his/her messages and what were other's.

>       this is the end of the documentation
