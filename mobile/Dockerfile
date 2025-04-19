FROM node:18

WORKDIR /app

# Kopiér package.json og lockfile først for bedre caching
COPY package*.json ./

# Installer afhængigheder
RUN npm install

# Kopiér resten af projektet ind
COPY . .

# Start appen via ny lokal CLI
CMD ["npx", "expo", "start", "--tunnel"]
