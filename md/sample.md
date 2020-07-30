
## Some sample
### Table sample
|  TH  |  TH  |
| ---- | ---- |
|  First Column  |  Second Column  |
|  First Column  |  Second Column  |


# Group Quick start

## Create message [POST /messages]

Start out by creating a message for the world to see.

+ Request (application/json)

        { "message": "Hello World!" }

+ Response 201

    + Headers

            Location: /messages/1337

## Create a new task [POST /tasks]

Now create a task that you need to do at a later date.

+ Request (application/json)

        {
            "name": "Exercise in gym",
            "done": false,
            "type": "task"
        }

+ Response 201

    + Headers

            Location: /tasks/1992


# Notes [/notes/{id}]

+ Parameters

    + id: abc123 (required) - Unique identifier for a note

## Get a note [GET]
Gets a single note by its unique identifier.

+ Response 200 (application/json)

    + Body

            {
                "id": "abc123",
                "title": "This is a note",
                "content": "This is the note content."
                "tags": [
                    "todo",
                    "home"
                ]
            }

    + Schema

            {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "string"
                    },
                    "title": {
                        "type": "string"
                    },
                    "content": {
                        "type": "string"
                    },
                    "tags": {
                        "type": "array",
                        "items": {
                            "type": "string"
                        }
                    }
                }
            }

## Update a note [PATCH]
Modify a note's data using its unique identifier. You can edit the `title`,
`content`, and `tags`.

+ Request (application/json)

    + Body

            {
                "title": "This is another note",
                "tags": [
                    "todo",
                    "work"
                ]
            }

    + Schema

            {
                "type": "object",
                "properties": {
                    "title": {
                        "type": "string"
                    },
                    "content": {
                        "type": "string"
                    },
                    "tags": {
                        "type": "array",
                        "items": {
                            "type": "string"
                        }
                    }
                },
                "additionalProperties": false
            }

+ Response 204
