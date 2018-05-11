# sftp-service
sftp service for testing purposes.
## config
Based on [atomz/sftp](https://hub.docker.com/r/atmoz/sftp/).
In current setup, there is a user named 'user' which can upload files in folder 'share'.
Further private config is required, see next sections.

### password authentication
In docker-compose.override.yml e.g.
```
version: '3.4'
services:
  sftp:
    ports:
      - "2222:22"
    command: user:aPassword:::share
```
### key authentication
In docker-compose.override.yml e.g.
```
version: '3.4'
services:
  sftp:
    ports:
      - "2222:22"
    volumes:
      - /path/to/your/id_rsa.pub:/home/user/.ssh/keys/id_rsa.pub:ro
      - /path/authorized_keys:/home/user/.ssh/keys/authorized_keys:ro
```
## running
```
docker-compose up
```
