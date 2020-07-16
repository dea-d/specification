# dea.d

Both APIs are tag-based, this means each request sent must be sent with a tag that will be used to reference the request for a status message or a reply. There is a tag being added to all message payloads therefore, this however is something protocol-specification wise we need not worry about, as [tristanable](https://github.com/deavmi/tristanable) will take care of it, we must only keep track of our tags being used and which ones are expected where.

## Client API

Posting a new message:

```json
{
    "action" : "post",
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
