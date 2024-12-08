# Python home assignment
## Goal
Write a webserver that creates bots using API and write tests for all bots functionality.

## Instructions
Write a RESTful webserver which supports all of the following HTTP methods, POST, PUT, GET, PATCH, DELETE.

This server should have an in-memory database (can be a simple dictionary) that represents bot objects.

You can use Flask, or any web framework you'd like.

The list of intents for the bots should be stored in the bots db and EVERY new intent will be added to the db.

Intent types (you can add more if you want):
* play_sound
* tell_joke
* disconnect

Each bot should have the following attributes:
* id – Random number
* name – Should be unique
* url - External URL (it isn't used by the application)
* intents - Array of supported intents

## Requirements 
* Running webserver
* Use object-oriented design for both the server and the tests.
* At least 5 tests executed by pytest.
* Avoid code duplication as much as possible.

## Bonus
* Use PyTest mark.
* Create a HTML report of the tests.
* Try to think of special scenarios to test.
* Use fixtures.

If you have any questions, contact naama.rais@audiocodes.com

Turning in the project should be done in one of the following methods:
* Private Github repo – grant view permissions to @naamarais
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
