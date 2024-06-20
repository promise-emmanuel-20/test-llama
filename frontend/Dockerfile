FROM node:20-alpine as build

WORKDIR /app
ARG NEXT_PUBLIC_CHAT_API
CMD ["npx", "-y", "serve@latest", "out"]

# Install dependencies
COPY package.json package-lock.* ./
RUN npm install

# Build the application
COPY . .
RUN npm run build

# ====================================
FROM build as release

CMD ["npm", "run", "start"]