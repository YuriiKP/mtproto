# mtproto

## Официальный MTProxy
Ссылка на официальный репозиторий: https://github.com/TelegramMessenger/MTProxy

### Установка и запуск без docker compose
```bash
docker run -d \
  --name mtproto-proxy \
  --restart unless-stopped \
  -p 443:443 \
  -v proxy-config:/data \
  telegrammessenger/proxy:latest
```

### Логи
В логах можно найти ссылки на подключение
```bash
docker logs mtproto-proxy
```

## MTG v2

Страница на гит: https://github.com/9seconds/mtg?tab=readme-ov-file
### Создаем ключ
```bash
docker run --rm nineseconds/mtg:2 generate-secret google.com
```

### Создаем конфиг файл
```bash
vi config.toml
```
Минимальный вариант конфига
```bash
secret = "ee473ce5d4958eb5f968c87680a23854a0676f6f676c652e636f6d"
bind-to = "0.0.0.0:3128"
```

### Запуск
```bash
docker run -d -v $PWD/config.toml:/config.toml -p 443:3128 --name mtg-proxy --restart=unless-stopped nineseconds/mtg:2
```

### Конфигурация
```bash
docker exec mtg-proxy /mtg access /config.toml --ipv4 IP_АДРЕС
```
