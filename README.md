# Notification with WebSocket, Vue and Redis Pub/Sub

This small project allow you to push notificatio in a Vue application from a Redis `PUBLISH` using WebSockets.

![notification-demo](https://user-images.githubusercontent.com/541250/80476373-96def200-894a-11ea-88f3-f69f8decc88e.gif)

A blog post will soon be published, to explain the details.

## Run the application:


```
> git clone https://github.com/tgrall/redis-websockets-vue-notifications.git

> cd redis-websockets-vue-notifications

```

**Run the WebSocket Server**

You can change the HTTP Port and the Redis connection string in the `./notif-server/server.js`.

```
> cd ./notif-server

> npm install

> node server.js

```   

**Run the Vue Web Front application**

```
> cd ./web-client

> npm install

> npm run serve
```

Open your browser to http://localhost:8080

**Push notifications to the application**

Open `redis-cli` ou [Redis Insight](https://redislabs.com/redisinsight/) and publish messages on the `app:notifications` channel.

```
127.0.0.1:6379> PUBLISH app:notifications "Hello from Redis!" 

127.0.0.1:6379> PUBLISH app:notifications "Another message!" 
```

You should see some notifications poping up in the Vue application.

Test aio_skFY70eE5IsWEzglni5P6l2mIaVB
