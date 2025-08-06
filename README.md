## Building a To-Do NodeJs App Image:

1. download app files

```bash
 git clone https://github.com/docker/getting-started-app.git
```

1. Change to App Directory:

```bash
cd getting-started-app/
```

1. Write the Dockerfile

```bash
vim Dockerfile
```

```docker
FROM    node:18-alpine
WORKDIR /app
COPY    . .
RUN     yarn install --production && yarn cache clean
ENTRYPOINT      ["node"]
CMD     ["src/index.js"]
EXPOSE  3000
```

1. Build the Docker image

```bash
docker build -t to-do-app .

# -t : TAG v1.0
# . : directory where image will be built ( current working directory)
```

1. Run the App container

```bash
docker run -d -p 3000:3000 to-do-app
```

1. Check your App

```
URL: localhost:3000
```

1. Push the Docker image to Registry
