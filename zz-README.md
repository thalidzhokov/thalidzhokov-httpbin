# thalidzhokov-httpbin
Обертка для поднятия собственного сервиса httpbin.org
Применяется на httpbin.org.ru и не блокирует запросы из РФ.

### Как запустить локально
- `docker compose -f zz-docker-compose.yml up -d`

### Как запустить на хосте
- `cp zz.env .env`
- Указать домен и электронную почту в .env
- `docker compose -f zz-docker-compose.yml up -d`

### Как работает
- На входе traefik обслуживает порты 80 и 443
- Трафик направляется на контейнер zz-httpbin
