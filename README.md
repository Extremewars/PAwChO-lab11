# PAwChO-lab11

## Utworzenie sieci mostkowej

```bash
docker network create --driver=bridge --subnet=10.0.0.0/24 lab11net
```

## Utworzenie kontenerów z przypiętymi plikami lokalnymi

```bash
docker run --rm -dt --name web1 \
  --network=lab11net \
  --ip=10.0.0.2 \
  -v /home/pawel/lab11/html:/usr/share/nginx/html:ro \
  -v /home/pawel/lab11/logs/web1:/var/log/nginx \
  -p 8080:80 \
  nginx:latest

docker run --rm -dt --name web2 \
  --network=lab11net \
  --ip=10.0.0.4 \
  -v /home/pawel/lab11/html:/usr/share/nginx/html:ro \
  -v /home/pawel/lab11/logs/web2:/var/log/nginx \
  -p 8082:80 \
  nginx:latest

docker run --rm -dt --name web3 \
  --network=lab11net \
  --ip=10.0.0.6 \
  -v /home/pawel/lab11/html:/usr/share/nginx/html:ro \
  -v /home/pawel/lab11/logs/web3:/var/log/nginx \
  -p 8084:80 \
  nginx:latest
```

## Działanie strony

![Działanie polecenia curl](/zdjecia/curl.png)


![Działanie strony](/zdjecia/website.png)

## Działanie logów

![Działanie logów](/zdjecia/logs.png)
