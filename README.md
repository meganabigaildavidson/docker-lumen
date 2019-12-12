# Docker + Lumen with Nginx and SQlite

This quick and simple setup for lumen with SQlite

## Build the lumen-cli image

```bash
cd images/lumen-cli
docker build -t lumen-cli .
```

## Build the php-7.3 image

```bash
cd images/php
docker build -t php .
```

## Create Lumen App

now, create the app in the current  directory named `app`

```bash
cd ../../
docker run  --rm -it -v $(pwd):/app lumen-cli lumen new app
```

### Build & Run

```bash
docker-compose up --build -d
```

Navigate to [http://localhost:80](http://localhost:80) and you should see the default lumen page


### Stop docker

```bash
docker-compose down
```

### Install some lumen extras
[https://github.com/flipboxstudio/lumen-generator](https://github.com/flipboxstudio/lumen-generator)

```bash
cd app
docker run --rm -v $(pwd):/app composer composer require flipbox/lumen-generator
```

### Running artisan commands

```bash
cd app
docker run --rm -it -v $(pwd):/app php php /app/artisan ...
```

