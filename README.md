# Docker-RoR6-Nginx
For begining of Ruby on Rails and Nginx with Docker.

#### Includes the following components:
- Ruby 2.6.5
- Ruby on Rails 6.0.2
- Nginx 1.15.8
- Mysql 5.7
- Redis 5.0.7

## Usage
Clone this repo
```
$ git clone https://github.com/yusukehigasa/Docker-RoR6-Nginx.git
```

### Make new app
```
$ docker-compose run app rails new . --force --database=mysql --skip-bundle --skip-git
```

### Modify `config/database.yml`
```[yml]
default: &default
  adapter: mysql2
  encoding: utf8
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: root # <- MYSQL_ROOT_PASSWORD of docker-compose.yml
  host: db # <- Service Name of docker-compose.yml
```

### Build the docker containers
```
$ docker-compose build
```

### Install webpacker for RoR6 has this
```
$ docker-compose run app rails webpacker:install
```

### Run the docker containers
```
$ docker-compose up
```

### DB Migration on the App
```
$ docker-compose run app rails db:create
```

### If you need console on RoR Container
```
$ docker-compose run app ash
```
NOTE: alpine has not **bash**, be prepared **ash** instead of bash

### If you need console on Nginx Container
```
$ docker-compose run web bash
```

### Watch Nginx's logs
```
$ docker-compose logs web
$ docker-compose logs -f web
```

### Watch the App
Open http://localhost:3000 in your browser.

#### Thank you for check out this.

## Author
Yusuke Higasa / [@higa_chan](https://twitter.com/higa_chan)
