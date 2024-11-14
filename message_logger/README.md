# Message Logs Generator
This service is written in Python. This is a simple consumer that listens for
new messages in Redis queue and prints message content to stdout. Message can be
anything, there is no additional processing.

## Configuration

The service scans environment for variables:
- `REDIS_HOST` - host of Redis
- `REDIS_PORT` - port of Redis
- `REDIS_CHANNEL` - channel the processor is going to listen to.