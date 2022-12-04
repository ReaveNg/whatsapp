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
  response.send('Reave</br>Went for a Jog!');
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

Access token invalidationFYI
This application has been identified as having access tokens associated with it posted in a public GitHub repository. As a security measure, we have invalidated the session for these particular tokens.
As stated in our Platform Terms, you must not transfer or share access tokens and secret keys, except with a Service Provider who helps you build, run or operate your app. These tokens must be kept secret and not shared publicly. Disclosing access tokens to the public may result in unauthorized access to your app.
This action was taken as part of the GitHub secret scanning program. We have partnered with GitHub on this scanning program to protect Facebook users by automatically invalidating Facebook access tokens when they are shared in a public GitHub repository.
