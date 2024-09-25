
Hay 7 tipos de networks en docker.


## Docker 

```bash
sudo docker network ls
```


## default
```
docker run -itd --rm --name messi alpine 
docker run -itd --rm --name ronaldo alpine 
docker run -itd --rm --name neymar nginx 

docker ps -q | xargs -n 1 docker inspect --format '{{ .NetworkSettings.IPAddress }} {{ .Name }}' | sed 's/ \// /'
```

## conectar a neymar

```
docker run -itd --rm -p80:80 --name neymar nginx 
```

## crear tu propio network

```
sudo docker network create barca
docker run -itd --rm --network=barca --name messi alpine 
docker run -itd --rm --network=barca --name neymar nginx 
```
## crear tu propio network

```
docker run -itd --rm --network=host --name neymar nginx 
```
## crear macvlan 

```
sudo docker network create -d  macvlan \
  --subnet 192.168.50.0/24 \
  --gateway 192.168.50.1 \
  -o parent=eth0.10 \
  barca

sudo ip link set ____ promsic on

docker run -itd --rm --network=barca --name neymar nginx 
```


## crear macvlan 

```
sudo docker network create -d ipvlan \
  --subnet 192.168.50.0/24 \
  --gateway 192.168.50.1 \
  -o parent=eth0.10 \
  barca


docker run -itd --rm --network=barca --name neymar nginx 
```



