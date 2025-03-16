# Deploying Minifolio


It is easiest to deploy Minifolio using Docker Compose. Here is a reference `docker-compose.yml`, which you can adapt to your needs.


```yml
# Minifolio
# Example docker-compose.yml
#
# Usage:
# * The data directory will be set up inside `./data` on the host system
# * The private_data directory will be set up inside `./private_data` on the
#   host system.
services:
  minifolio:
    image: maddyguthridge/minifolio

    hostname: minifolio
    restart: always
    ports:
      - 127.0.0.1:3000:3000/tcp
    volumes:
      - "./data:/data:rw"
      - "./private_data:/private_data:rw"

    environment:
      DATA_REPO_PATH: "/data"
      PRIVATE_DATA_PATH: "/private_data"
      HOST: 0.0.0.0
      PORT: 3000
```

