FROM node:16-alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# from=builder says to take artifacts from the build command of our application
COPY --from=builder /app/build /usr/share/nginx/html  
CMD ["npm", "run", "start"]