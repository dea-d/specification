# dea.d

Both APIs are tag-based, this means each request sent must be sent with a tag that will be used to reference the request for a status message or a reply. There is a tag being added to all message payloads therefore, this however is something protocol-specification wise we need not worry about, as [tristanable](https://github.com/deavmi/tristanable) will take care of it, we must only keep track of our tags being used and which ones are expected where.

## Client API

### Posting a post

Posting a new post can be accomplished by the following:

```json
{
    "action" : "post",
    "payload" : {
        "text" : "Hello world",
        "parent" : <parentID>
    }
}
```

1. If a post is to be a reply to another post then the key `"parent"` must exist with an integer referring to the parent post's ID, `<parentID>`.

The reply will be the following:

```json
{
	"status" : <statusCode>,
	"return" : <postID>
}
```

1. The ID of the newly created post will be in the key `"return"` as an integer, `<postID>`.

### Deleting a post

Deleting a post can be accomplished by the following:

```json
{
    "action" : "delete",
	"payload" : <postID>
}
```

1. The ID of the post to delete is `<postID>` in the key `"payload"`.

The reply will be the following:

```json
{
	"status" : <statusCode>
}
```

### Channel management

> Channels are basically continuous feeds of data. There are several channels, "posts", "notifications" and "messages"

Enabling a channel:

```json
{
	"action" : "openChannel",
	"payload" : "<channelName>"
}
```

Disabling a channel:

```json
{
	"action" : "closeChannel",
	"payload" : "<channelName>"
}
```

## Server API

TODO:

1. Pull posts from a remote user
	1. To facilitate timeline of a profile viewing
2. Subscribe to a live feed of posts of a remote user
	1. To facilitate a timeline
	2. This channel ca be accessed and then provided a tagged-stream of updates, **live**, streamed to the client host


Subscribing to a user:

```json
{
	"action" : "subscribe",
	"payload" : "<user>@<remoteServer>"
}
```

Unsubscribing from a user:

```json
{
	"action" : "unsubscribe",
	"payload" : "<user>@<remoteServer>"
}
```
