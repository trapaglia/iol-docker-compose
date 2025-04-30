sudo apt update
sudo apt install -y \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/$(. /etc/os-release && echo "$ID")/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/$(. /etc/os-release && echo "$ID") \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo docker run hello-world

sudo usermod -aG docker $USER
newgrp docker

docker compose up --build (si le agreagas -d corre en segundo plano)
docker ps
docker exec -it trader bash
docker compose logs frontend
docker compose logs -f (tiempo real)
docker compose restart frontend
docker compose down (apaga)
docker compose down -v (destruye)


limpiar viejos
docker image prune -a
docker container prune

interactuar entre servicios
ping frontend

conectar a otra base de datos
"postgresql://trader_user:securepass456@db:5432/tu_basededatos"



sudo lsblk
sudo mkfs.ext4 -F /dev/sdb
sudo mkdir -p /mnt/datadisco
sudo mount /dev/sdb /mnt/datadisco
df -h
sudo blkid
sudo vim /etc/fstab
UUID="tu_UUID"  /mnt/datadisco  ext4  defaults,nofail  0  2

sudo systemctl stop docker
sudo rsync -aP /var/lib/docker/ /mnt/dockerdata/
⚠️ Usamos rsync en lugar de mv para evitar problemas de permisos y asegurar una copia exacta.
sudo mv /var/lib/docker /var/lib/docker.bak
sudo ln -s /mnt/dockerdata /var/lib/docker
sudo systemctl start docker
docker info | grep "Docker Root Dir"

