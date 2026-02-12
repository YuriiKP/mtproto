# mtproto

### Установка и запуск
`
docker run -d \
  --name mtproto-proxy \
  --restart unless-stopped \
  -p 443:443 \
  -v proxy-config:/data \
  telegrammessenger/proxy:latest
`

### Логи
В логах можно найти ссылки на подключение
`docker logs mtproto-proxy`
