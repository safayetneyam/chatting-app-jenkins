## Manual Run Locally in Docker Engine

curl.exe -o html.tpl https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/html.tpl

trivy fs --format template --template "@html.tpl" -o report.html .

```bash

docker compose up mongo -d

docker build -t chat-b:n08 ./backend
docker build -t chat-b:n08 ./frontend

docker run -p 5001:5001 --name chat-b --network 08-fullstack-chat-app_default --env-file .env -d --restart unless-stopped chat-b:n08

docker run -p 5174:4173 --name chat-f --restart unless-stopped chat-f:n08

docker rm -f chat-f
docker rm -f chat-b

docker rmi chat-f:n08
docker rmi chat-b:n08

docker compose down mongo -v

```

```bash
$NETWORK = docker inspect (docker compose ps -q mongo) --format '{{range $k, $v := .NetworkSettings.Networks}}{{$k}}{{end}}'
$NETWORK
```

# ✨ Full Stack Realtime Chat App ✨

![Demo App](/frontend/public/screenshot-for-readme.png)

[Video Tutorial on Youtube](https://youtu.be/ntKkVrQqBYY)

Highlights:

- 🌟 Tech stack: MERN + Socket.io + TailwindCSS + Daisy UI
- 🎃 Authentication && Authorization with JWT
- 👾 Real-time messaging with Socket.io
- 🚀 Online user status
- 👌 Global state management with Zustand
- 🐞 Error handling both on the server and on the client
- ⭐ At the end Deployment like a pro for FREE!
- ⏳ And much more!

### Setup .env file

Copy `.env.example` to `.env` in the project root and fill in the application secrets:

```shell
cp .env.example .env
```

The Docker Compose MongoDB service is available to the backend as `mongo`, so keep the MongoDB URI in the root `.env` as:

```dotenv
MONGODB_URI=mongodb://mongo:27017/chat_app
PORT=5001
JWT_SECRET=replace-with-a-long-random-secret

CLOUDINARY_CLOUD_NAME=your-cloudinary-cloud-name
CLOUDINARY_API_KEY=your-cloudinary-api-key
CLOUDINARY_API_SECRET=your-cloudinary-api-secret

NODE_ENV=production
```

### Run with Docker

```shell
docker compose up --build
```

Open http://localhost:5174 after the containers are healthy. The frontend connects directly to the published backend at port 5001. MongoDB data is persisted in the `mongo_data` Docker volume.

### Run locally

For local development, use `NODE_ENV=development`, set `MONGODB_URI` to a reachable MongoDB instance, and run:

```shell
npm start
```
