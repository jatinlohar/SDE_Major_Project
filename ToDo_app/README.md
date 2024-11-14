# todos-api

This service is written in NodeJS, it provides CRUD operations over TODO entries.
It keeps all the data in memory. CREATE and DELETE operations are logged by
sending appropriate message to a Redis queue. The messages are then processed by
`message_logger`.


TODO object looks like this:
```
{
    id: 1,
    userId: 1,
    content: "Create new todo"
}
```

Log message looks like this:
```
{
    opName: CREATE,
    username: username,
    todoId: 5,
}
```

## Configuration

The service scans environment for variables:
- `TODO_API_PORT` - the port the service takes.
- `JWT_SECRET` - secret value for JWT token processing.
- `REDIS_HOST` - host of Redis
- `REDIS_PORT` - port of Redis
- `REDIS_CHANNEL` - channel the processor is going to listen to