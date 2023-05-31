# Django

## vagrant立ち上げ&SSH接続
```
vagrant up
vagrant ssh
```

## djangoのプロジェクト作成
```
cd /vagrant/api

docker build -t api .

mkdir src

docker run -it --rm --mount type=bind,source="$(pwd)"/src,target=/src api

python3 -m django startproject config .
python3 -m django startapp app

exit
```

/api/src/config/settings.py編集
```
ALLOWED_HOSTS = ['*']
```

## docker compose立ち上げ
```
cd /vagrant
docker compose up -d

// 下記のサイトで確認
http://192.168.30.30:8000/
```

## mysql疎通確認
/api/src/config/settings.py編集
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'api',
        'USER': 'docker',
        'PASSWORD': 'docker',
        'HOST': 'db',
        'PORT': 3306
    }
}
```

migration
```
docker exec -it api sh

python manage.py migrate

exit
```

## 管理者ユーザを作成
```
docker exec -it api sh

python manage.py createsuperuser --email admin@example.com --username admin

exit

// 下記のサイトで確認
http://192.168.30.30:8000/admin/
```
