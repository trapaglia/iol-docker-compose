FROM debian:bullseye

# Instala herramientas básicas y dependencias
RUN apt-get update && apt-get install -y \
    git \
    curl \
    build-essential \
    libsqlite3-dev \
    libgmp-dev \
    zlib1g-dev \
    sqlite3 \
    && apt-get clean

# Instala GHCup para GHC y Cabal
RUN curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | bash -s -- --yes

# Ajusta PATH
ENV PATH="/root/.ghcup/bin:$PATH"

# Asegura tener cabal y ghc
RUN ghcup install ghc recommended && \
    ghcup install cabal latest && \
    ghcup set ghc recommended && \
    ghcup set cabal latest

WORKDIR /app

CMD [ "bash" ]

