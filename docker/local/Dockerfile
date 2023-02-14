# first satge : 
FROM node:alpine AS dependencies
RUN apk add --no-cache libc6-compat
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci

# second stage  : 

FROM node:alpine AS runner
WORKDIR /app
COPY . .
COPY --from=dependencies /app/node_modules ./node_modules

ENTRYPOINT ["npm", "run", "dev"]
