# Authorization Application

## Prerequisites
Users Application must be running, because Authorization application fetches user data from it.

## Configuration

The service scans environment for variables:
- `AUTH_API_PORT` - the port the service takes.
- `USERS_API_ADDRESS` - base URL of [Users API](/users-api).
- `JWT_SECRET` - secret value for JWT generator. Must be shared amongst all components.

The following data hardcodes:

|  Username | Password  |
|-----------|-----------|
| admin     | admin     |
| johnd     | foo       |
| janed     | ddd       |