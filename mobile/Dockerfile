FROM node:18

WORKDIR /app
COPY . .

RUN npm install -g expo-cli && npm install

CMD ["npx", "expo", "start", "--tunnel"]
