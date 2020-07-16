# dea.d

Both APIs are tag-based, this means each request sent must be sent with a tag that will be used to reference the request for a status message or a reply.

## Client API

Posting a new message:

```json
{
    "action" : "post",
    "tag" : <tag>,
    "payload" : {
        "text" : "Hello world"
    }
}
```

Enabling a channel:

> Channels are basically continuous feeds of data. There are several channels, "posts", "notifications" and "messages"

```json
{
	"action" : "openChannel",
	"tag" : <tag>,
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
	"tag" : <tag>,
	"payload" : "<user>@<remoteServer>"
}
```

Unsubscribing from a user:

```json
{
	"action" : "unsubscribe",
	"tag" : <tag>,
	"payload" : "<user>@<remoteServer>"
}
```
