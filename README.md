## Building a To-Do NodeJs App Image:

1. download app files

```bash
 git clone https://github.com/docker/getting-started-app.git
```

2. Change to App Directory:

```bash
cd getting-started-app/
```

3. Write the Dockerfile

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

4. Build the Docker image

```bash
docker build -t to-do-app .

# -t : TAG v1.0
# . : directory where image will be built ( current working directory)
```

5. Run the App container

```bash
docker run -d -p 3000:3000 to-do-app
```

6. Check your App

```
URL: localhost:3000
```

7. Push the Docker image to Registry

```bash
# 1.login to your docker hub repository
docker login

# 2.change the tag of your image so you can push it to your repository 
docker tag to-do-app:latest ibrahimmintal/to-do-app:v1.0

# 3. Push Image to Docker Hub
docker push ibrahimmintal/to-do-app:v1.0

```
