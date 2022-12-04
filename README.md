# whatsapp
A WhatsApp API client that connects through the WhatsApp Web browser app
Created meta for developer account. 
https://developers.facebook.com/docs/whatsapp/sample-app-endpoints#
https://developers.facebook.com/docs/whatsapp/cloud-api/get-started

Follow through the api creation with glitch
https://speckle-dandelion-bridge.glitch.me
Push the api to my whatsapp account. 
unable to verify token.

Used the 2nd method WhatsApp Business Platform On-Premises API
https://talented-star-tuna.glitch.me

var express = require('express')
  , bodyParser = require('body-parser');

var app = express();

app.use(bodyParser.urlencoded({extended: false}));
app.use(bodyParser.json())

app.get("/", function (request, response) {
  response.send('Simple WhatsApp Webhook tester</br>There is no front-end & Reave went for a Jog!');
});

app.get('/webhook', function(req, res) {
  if (
    req.query['hub.mode'] == 'subscribe' &&
    req.query['hub.verify_token'] == 'token'
  ) {
    res.send(req.query['hub.challenge']);
  } else {
    res.sendStatus(400);
  }
});

app.post("/webhook", function (request, response) {
  console.log('Incoming webhook: ' + JSON.stringify(request.body));
  response.sendStatus(200);
});

var listener = app.listen(process.env.PORT, function () {
  console.log('Your app is listening on port ' + listener.address().port);
});


Apparently, fb banned my token, otherwise I think my token should work. 

Access token invalidation FYI
This application has been identified as having access tokens associated with it posted in a public GitHub repository. As a security measure, we have invalidated the session for these particular tokens.
As stated in our Platform Terms, you must not transfer or share access tokens and secret keys, except with a Service Provider who helps you build, run or operate your app. These tokens must be kept secret and not shared publicly. Disclosing access tokens to the public may result in unauthorized access to your app.
This action was taken as part of the GitHub secret scanning program. We have partnered with GitHub on this scanning program to protect Facebook users by automatically invalidating Facebook access tokens when they are shared in a public GitHub repository.

Rectified and it seemed to be working. 

![WhatsApp Image 2022-12-04 at 22 55 02](https://user-images.githubusercontent.com/104077738/205497808-6c293e89-8cfb-4a58-8e83-51f78906e640.jpeg)
![image](https://user-images.githubusercontent.com/104077738/205497864-b03df9b4-2d03-4efa-a604-e51a813a7f9b.png)
![image](https://user-images.githubusercontent.com/104077738/205497960-4637d100-d12d-4b42-adea-f13f652150a9.png)
![image](https://user-images.githubusercontent.com/104077738/205497967-7aa38fca-2928-46a0-be24-746e6e455f19.png)
![image](https://user-images.githubusercontent.com/104077738/205497982-d0fc8655-73f3-45ac-93f9-c69384b09fab.png)


