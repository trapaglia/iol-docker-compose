FROM debian:bullseye

# Actualiza e instala paquetes necesarios
RUN apt-get update && apt-get install -y \
    git \
    curl \
    build-essential \
    pkg-config \
    m4 \
    sqlite3 \
    nodejs \
    npm \
    opam \
    && apt-get clean

# Instala Elm
RUN npm install -g elm

WORKDIR /app

CMD [ "bash" ]

