# Python home assignment
## Goal
Write a webserver that creates bots using API and write tests for all bots functionality.

## Instructions
Write a RESTful webserver which supports all of the following HTTP methods, POST, PUT, GET, PATCH, DELETE.

This server should have an in-memory database (can be a simple dictionary) that represents bot objects.

The list of intents for the bots should be stored in the bots db and EVERY new intent will be added to the db.

EVERY time the bot attempts to execute a command for example: play_sound it should check in the current configuration if the bot supports it.

Intent types (you can add more if you want):
* play_sound
* tell_joke
* disconnect

Each bot should have the following attributes:
* id – Random number
* name – Should be unique
* url - External URL (it isn't used by the application)
* intents - Array of supported intents

API:
* Require authenticating and all operations fail if not authenticated
* Support 2 types of authentications 
  * Basic auth using username and pass.
  * Token auth using a shared string that appears in the message. Example:
```json
{
  "token": "sup3rs3cr3t"
}
```

## Requirements 
* Running webserver
* Use object-oriented design for both the server and the tests
* At least 5 tests executed by pytest 
 
## Bonus
* Use PyTest mark.
* Create a HTML report of the tests
* Try to think of special scenarios to test 
* Use: Fixtures
 
If you have any questions, contact Orgad at: 03-9764063

Turning in the project should be done in one of the following methods:
* Private Github repo – grant view permissions to @orgads
* Dropbox link

## Sample interaction
POST /bot/sample-bot
```json
{
  "url": "http://example.com"
}
```
->
```json
{
  "id": "17",
  "name": "sample-bot",
  "intents": [],
  "url": "http://example.com"
}
```

GET /bot/sample-bot

->

```json
{
  "id": "17",
  "name": "sample-bot",
  "intents": [],
  "url": "http://example.com"
}
```

PUT /bot/sample-bot
```json
{
  "intents": ["play-sound", "tell-joke"]
}
```
->
```json
{
  "id": "17",
  "name": "sample-bot",
  "intents": ["play-sound", "tell-joke"]
}
```

Notice that url is gone, because PUT replaces the entire object

PATCH /bot/sample-bot
```json
{
  "url": "http://example.com"
}
```
->
```json
{
  "id": "17",
  "name": "sample-bot",
  "intents": ["play-sound", "tell-joke"],
  "url": "http://example.com"
}
```

DELETE /bot/sample-bot

->

200 OK
