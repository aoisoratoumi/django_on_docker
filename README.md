# Docker上でDjangoのアプリを作成する際のひな型

## 開発時

```bash
$ docker-compose build
```

```bash
$ docker-compose up -d
```

## デプロイ時

```bash
$ docker-compose down -v

$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput
$ docker-compose -f docker-compose.prod.yml exec web python manage.py collectstatic --noinput
```