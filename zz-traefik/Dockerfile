FROM traefik:latest

LABEL name="zz-traefik"
LABEL version="0.1"
LABEL maintainer="Albert Thalidzhokov <thalidzhokov@gmail.com>"

# Аргументы
ARG ACME_EMAIL

# USER
RUN whoami

# WORKDIR
RUN pwd

# Обновляем пакеты
RUN apk update

# Устанавливаем curl
RUN apk add curl

# Копируем конфиги
COPY ./conf/headers.yaml /etc/traefik/conf/headers.yaml
COPY ./conf/tls.yaml /etc/traefik/conf/tls.yaml
COPY ./dist.traefik.yaml /tmp/dist.traefik.yaml

# Меняем email в настройках в /traefik.yaml
# Если ACME_EMAIL не установлен, то устанавливаем test@example.com
RUN if [ -n "${ACME_EMAIL}" ]; then \
        sed -e "s/your-email@example.com/${ACME_EMAIL}/g" \
        /tmp/dist.traefik.yaml > /traefik.yaml; \
    else \
        sed -e "s/your-email@example.com/test@example.com/g" \
        /tmp/dist.traefik.yaml > /traefik.yaml; \
    fi;
