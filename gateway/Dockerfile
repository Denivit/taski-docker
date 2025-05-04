# Явно указываем платформу и используем alpine-версию для уменьшения размера
FROM --platform=linux/amd64 nginx:1.22.1-alpine

# Копируем конфигурацию Nginx
COPY nginx.conf /etc/nginx/templates/default.conf.template

# Опционально: копируем статические файлы (если нужно)
# COPY ./static /usr/share/nginx/html

# Nginx автоматически использует шаблон default.conf.template
# и заменяет переменные окружения при запуске контейнера