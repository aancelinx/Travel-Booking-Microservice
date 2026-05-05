# base stage
FROM node:18-alpine AS base
WORKDIR /usr/src/app

COPY package*.json ./
RUN npm ci

# development stage
FROM base AS development

COPY . .
RUN npm run build

# production stage
FROM base AS production

COPY --from=development /usr/src/app/dist ./dist

CMD ["node", "./dist/main.js"]


