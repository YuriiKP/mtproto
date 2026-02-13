# mtproto

## Официальный MTProxy

### Установка и запуск без docker compose
```
docker run -d \
  --name mtproto-proxy \
  --restart unless-stopped \
  -p 443:443 \
  -v proxy-config:/data \
  telegrammessenger/proxy:latest
```

### Логи
В логах можно найти ссылки на подключение
```
docker logs mtproto-proxy
```

## MTG v2

Страница на гит: https://github.com/9seconds/mtg?tab=readme-ov-file
### Создаем ключ
```
docker run --rm nineseconds/mtg:2 generate-secret google.com
```

### Создаем конфиг файл
```
vi config.toml
```
Минимальный вариант конфига
```
secret = "ee473ce5d4958eb5f968c87680a23854a0676f6f676c652e636f6d"
bind-to = "0.0.0.0:443"
```

### Запуск
```
docker run -d -v $PWD/config.toml:/config.toml -p 443:3128 --name mtg-proxy --restart=unless-stopped nineseconds/mtg:2
```
