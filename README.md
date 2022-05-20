# setup
vscode, github

## 👩‍💻 setup vscode 

Badge | URL
------------ | -------------
 <a href="https://github.com/sing3demons/awesome-go"> <img src="https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white" /> </a> | <a href="https://github.com/sing3demons/go-docker-mysql/blob/main/README.md">go - docker - mysql</a>


<br/>
## git commit -m 
- feat (✨): ฟีเจอร์ใหม่ 
- fix (🐛): แก้ไขบัค
- refactor (📦): ปรับโครงสร้าง​ (ไม่ได้เพิ่มฟีเจอร์ แต่ก็ไม่ได้แก้บัค)
- style (💎): การแก้ไขโค้ดที่ไม่ได้เปลี่ยนแปลงความหมาย เช่น เติม semicolon, ลบ whitespace
- test (🚨): เพิ่ม/แก้ไข Test
- perf (🚀): ปรับปรุงประสิทธิภาพการทำงาน
- build (🔨): การแก้ไขที่กระทบกระบวนการ Build
- ci (⚙️): ปรับการตั้งค่า CI เช่น ปรับขั้นตอนการทำงานของ GitHub Actions
- docs (📚): การแก้ไขที่เกี่ยวกับเอกสาร เช่น แก้ README

### วิธีใช้งานก็แค่เติมนำหน้า Commit Message ไปเลย เช่น:

```
feat: add confirmation dialog on delete
```
```
fix: isOdd returns true when input is 0
```
```
refactor: remove unnecessary else after return
```
<br/>

<hr>
### Setup vscode React  ![](https://img.shields.io/badge/Code-React-informational?style=flat&logo=react&logoColor=white&color=6aa6f8)

cmd + shift + p > Preferences: Open Workspace Settings (JSON)

#### setting.json
```json
{
  "editor.formatOnSave": true,
  "emmet.syntaxProfiles": { "javascript": "jsx" },
  "emmet.includeLanguages": { "javascript": "javascriptreact" },
  "emmet.triggerExpansionOnTab": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": { "editor.defaultFormatter": "esbenp.prettier-vscode" }
}
```
<br>

```
touch .prettierrc
```

```json
{ 
"semi": false, 
"singleQuote": true 
}
```

#### esLint
```
touch .eslintrc
```
```
{
  "extends": ["react-app", "plugin:prettier/recommended"]
}
```
```
yarn add -D eslint-plugin-prettier eslint-config-prettier prettier
```

<hr>
![](https://img.shields.io/badge/Code-Vue-informational?style=flat&logo=react&logoColor=white&color=6aa6f8)

# Setup vscode Vue 👋

## setting.json
```json
{
  "editor.formatOnSave": true,
  "editor.detectIndentation": false,
  "emmet.includeLanguages": { "vue-html": "html", "vue": "html" },
  "emmet.syntaxProfiles": { "vue-html": "html", "vue": {} },
  "files.associations": { "*.vue": "vue" },
  "vetur.format.defaultFormatter.html": "prettyhtml",
  "vetur.format.defaultFormatter.js": "prettier",
  "vetur.format.defaultFormatterOptions": {
    "prettier": {
      "printWidth": 120,
      "semi": false,
      "singleQuote": true,
      "tabWidth": 4,
      "trailingComma": "none",
      "bracketSpacing": true,
      "jsxBracketSameLine": true,
      "arrowParens": "avoid"
    },
    "prettyhtml": { "tabWidth": 4, "printWidth": 120, "singleQuote": false }
  }
}
```
<hr>
# Dockerfile
```
Dockerfile
```
```
FROM golang:alpine

RUN mkdir /app

WORKDIR /app

ADD go.mod .
ADD go.sum .

RUN go mod download
ADD . .

RUN go get github.com/githubnemo/CompileDaemon

EXPOSE ${PORT}

ENTRYPOINT CompileDaemon --build="go build main.go" --command=./main
```
```
docker build -t hello_world:1.0 .
```
```
docker run --rm -d -p 8000:8000 hello_world:1.0 --name go-blog
```
# .env

```
.env
```
```
MYSQL_ROOT_PASSWORD=root
DB_USER=user
DB_PASSWORD=*******
DB_HOST=db
DB_PORT=3306
DB_NAME=golang
SERVER_PORT=8000
ENVIRONMENT=local
PORT=8080
```

# mysql

```
docker-compose.yml
```
```yml 
version: '3.9'
services:
  db:
    image: mysql:5.7.22
    ports:
      - "3305:3306"
    restart: always
    environment:
      - "MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}"
      - "MYSQL_USER=${DB_USER}"
      - "MYSQL_PASSWORD=${DB_PASSWORD}"
      - "MYSQL_DATABASE=${DB_NAME}" 
    volumes:
     - .db_data:/var/lib/mysql
  web:
    build: .
    ports:
      - "8000:${PORT}"
    volumes:
      - ".:/app"
    restart: always
    depends_on:
      - db
    links:
      - "db:database"
```

#  postgres
```
docker-compose.yml
```

```yml 
version: '3.8'
services:
    db:
        image: postgres
        environment:
          - POSTGRES_DB=${DB_NAME}
          - POSTGRES_USER=${DB_USER}
          - POSTGRES_PASSWORD=${DB_PASSWORD}
        ports:
          - 5432:5432
        volumes:
          - ./db_data:/var/lib/postgresql/data
        restart: always
    web:
        build: .
        ports:
          - "8080:${PORT}"
        volumes:
          - ".:/app"
        restart: always
        depends_on:
          - db
        links:
          - "db:database"
```

# mongo
```
version: '3.1'

services:

  mongo:
    image: mongo
    container_name: "mongo"
    restart: always
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: password
    ports: 
        - 27017:27017
    volumes: 
        - .gomongodbdata:/data/db
```

```
"mongodb://root:example@localhost:27017"
```


# redis
```
version: '3.5'

services:
    redis:
    container_name: "redis"
    image: redis:alpine
     # Specify the redis.conf file to use and add a password.
    command: redis-server /usr/local/etc/redis/redis.conf --requirepass passw0rd
    ports:
      - 6379:6379
     # map the volumes to that redis has the custom conf file from this project.
    volumes:
      - $PWD/redis.conf:/usr/local/etc/redis/redis.conf
```
```
redis.conf
```
redis.conf > maxmemory 41943040
```
# Use the official redis.conf file supplied by redis.
# As a test use a simple config for testing.
maxmemory 41943040
```

# nginx
```
nginx:
    image: nginx:latest
    container_name: webserver
    restart: unless-stopped
    ports:
      - 80:80
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - webapi #connect web 
```

# nginx.conf

```
user nginx;
# can handle 1000 concurrent connections
events {
    worker_connections 1024;
}
# forwards http requests
http {
        # http server
        server {
              # listens the requests coming on port 80
              listen 80;
              access_log  off;
              # / means all the requests have to be forwarded to api service
              location / {
                # resolves the IP of api using Docker internal DNS
                proxy_pass http://webapi:8080;
              }
        }
}
```


# .env 

```
.env
```
```
PORT=8080
DB_HOST=db
DB_USER=dnz-dev
DB_PASSWORD=dnz-dev
DB_NAME=dnz-dev
```

run command 
``` 
docker-compose up --build 
```
<hr>
# dotnet-setup

# สร้าง Database โดย Microsoft.EntityFrameworkCore
  - ติดตั้ง dotnet-ef

```
dotnet tool install --global dotnet-ef
```

```
dotnet add package Microsoft.EntityFrameworkCore.Design
```

   สร้าง mogrations
  
```
dotnet ef migrations add "Initial Migrations"
```

  - สร้าง database
  
```
dotnet ef database update
```

```
dotnet new gitignore
```

---

- extention vs code
1. Essential ASP.NET Core 3 Snippets
2. SQL Serber(mssql)
3. C#
4. dotnet core commands
5. Auto-Using for C#
6. C# Namespace Authocompletion
7. C# extensions
8. MSBuild project tools

- Gen self cert - https
```
dotnet dev-certs https —trust
```
# Docker - Microsoft SQL Server
```
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Passw0rd1234!' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-CU10-ubuntu-20.04
```

# ติดตั้งdotnet ef
https://docs.microsoft.com/en-us/ef/core/cli/dotnet

- For windown
```
dotnet ef dbcontext scaffold "Server=localhost,1433;user id=sa; password=Passw0rd1234!; Database=istock;" Microsoft.EntityFrameworkCore.SqlServer -o Entities -c DatabaseContext --context-dir Data
```

- For Mac
```
dotnet ef dbcontext scaffold ‘Server=localhost,1433;user id=sa; password=Passw0rd1234!; Database=istock;’ Microsoft.EntityFrameworkCore.SqlServer -o Entities -c DatabaseContext --context-dir Data
```

# postgrateSQL Docker
```
docker run --name postgres -e POSTGRES_PASSWORD=syspass1234 -p 5432:5432  -d postgres
```
```
docker run -it --rm --name postgres -e POSTGRES_PASSWORD=syspass1234 -p 5432:5432 -d postgres
```

<hr>
