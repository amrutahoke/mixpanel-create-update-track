# mixpanel-create-update-track
Example to use the mixpanel-create-update-track module

var express = require('express');
var mixpanel = require('mixpanel-create-update-track');
var bodyParser = require('body-parser');
var app = express();

app.use(bodyParser.urlencoded({extended:false}));

app.use(bodyParser.json())

# To create a user on the mixpanel
app.post('/create', function(req, res){
	console.log("APP :" + req.body.name);
	mixpanel.createUserProfile(req, res);
});

# To update the tags or properties in the user profile
app.post('/updateTags', function(req, res){
	mixpanel.updateTags(req, res);
});

# To track the user event
app.post('/track', function(req, res){
	mixpanel.trackUserEvent(req, res);
});

# To remove a user profile from mixpanel
app.post('/remove', function(req, res){
	mixpanel.removeUserProfile(req, res);
});

app.listen(port);

#Required POST body for the above end points

1. /create 
{
    "id": "77777",
    "name": "user first name",
    "lastName": "user last name",
    "email": "user@examples.com",
    "phone": "user mobile number",
    "token": "mixpanel account token"
}

2. /updateTags
{
    "id": "77777",
    "token": "mixpanel account token",
    "tags": [
        {
            "tag": "tag1",
            "enable": "state"
        },
        {
            "tag": "tag2",
            "enable": "state"
        }
        ]
}

3. /track
{
    "id": "77777",
    "token": "mixpanel account token",
    "event": "Log In",
    "referredBy": "Friend"
}

4. /remove
{
    "id": "77777",
    "token": "mixpanel account token",
}








