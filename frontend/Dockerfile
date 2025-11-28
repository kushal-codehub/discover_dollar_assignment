# build stage
FROM node:18-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
# build; adjust if your package.json build script differs
RUN npm run build -- --configuration production

# runtime stage with nginx
FROM nginx:stable-alpine
# remove default html
RUN rm -rf /usr/share/nginx/html/*
# copy built Angular app - adjust dist/<project-name> if needed
COPY --from=build /app/dist/angular-15-crud /usr/share/nginx/html

# copy custom nginx config
COPY frontend/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
