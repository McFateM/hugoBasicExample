NAME=jtreminio_com
HOST=static.grinnell.edu
IMAGE="jtreminio/jtreminio.com"
docker container run -d --name ${NAME} \
    --label traefik.backend=${NAME} \
    --label traefik.docker.network=traefik_webgateway \
    --label traefik.frontend.rule=Host:${HOST} \
    --label traefik.port=80 \
    --label com.centurylinklabs.watchtower.enable=true \
    --network traefik_webgateway \
    --restart always \
    ${IMAGE}

NAME=jtreminio_com
HOST=static.grinnell.edu
IMAGE="jtreminio/jtreminio.com"
docker container run -d --name ${NAME} \
    --label traefik.backend=${NAME} \
    --label traefik.docker.network=traefik_webgateway \
    --label "traefik.frontend.rule=Host:${HOST};PathPrefixStrip:/${NAME}/" \
    --label traefik.port=80 \
    --label com.centurylinklabs.watchtower.enable=true \
    --network traefik_webgateway \
    --restart always \
    ${IMAGE}


NAME=hugoBasicExample
HOST=static.grinnell.edu
IMAGE="mcfatem/hugobasicexample"
docker container run -d --name ${NAME} \
    --label traefik.backend=${NAME} \
    --label traefik.docker.network=traefik_webgateway \
    --label traefik.frontend.rule=Host:${HOST} \
    --label traefik.port=80 \
    --label com.centurylinklabs.watchtower.enable=true \
    --network traefik_webgateway \
    --restart always \
    ${IMAGE}


NAME=hugoBasicExample
HOST=static.grinnell.edu/${NAME}
IMAGE="mcfatem/hugobasicexample"
docker container run -d --name ${NAME} \
    --label traefik.backend=${NAME} \
    --label traefik.docker.network=traefik_webgateway \
    --label "traefik.frontend.rule=Host:${HOST};PathPrefixStrip:/${NAME}/" \
    --label traefik.port=80 \
    --label com.centurylinklabs.watchtower.enable=true \
    --network traefik_webgateway \
    --restart always \
    ${IMAGE}
