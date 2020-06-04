FROM node:12-alpine AS BUILDER

WORKDIR /angular8-app

# Dependencies
COPY package.json /angular8-app/package.json
COPY angular8-app/package-lock.json /angular8-app/package-lock.json
RUN npm install

ARG buildtype

# Project sources
COPY . /angular8-app
RUN npm run build-prod

FROM nginx:1.17.5-alpine
COPY --from=BUILDER /angular8-app/dist/angular8-springboot-client /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
