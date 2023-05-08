FROM nginx:latest

# Устанавливаем UID 1001
RUN usermod -u 1001 nginx

#Копируем конфиг и содержимое app
COPY nginx.conf /etc/nginx/nginx.conf
COPY ./app /app

# Запускаем web-сервер на порту 8000
EXPOSE 8000/tcp

# Запускаем nginx
CMD ["nginx", "-g", "daemon off;"]