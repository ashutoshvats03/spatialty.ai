
Postgres setup using docker
```cmd
	docker run -d ^
  --name my-postgres ^
  --restart unless-stopped ^
  -e POSTGRES_USER=postgres ^
  -e POSTGRES_PASSWORD=postgres ^
  -e POSTGRES_DB=postgres ^
  -p 5432:5432 ^
  -v pgdata:/var/lib/postgresql/data ^
  postgres:16
```


``` cmd
REM Check status
docker ps

REM open postgresSQL shell (psql)
docker exec -it my-postgres psql -U postgres -d postgres

REM view logs
docker logs -f my-postgres

REM start or stop
docker stop my-postgres
docker start my-postgres
```


Env setup
```
UPSTASH_REDIS_REST_URL= <"your_url">
UPSTASH_REDIS_REST_TOKEN= <"your_token">

DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=postgres
DB_NAME=postgres
```
If any port related issue comes , then 
```
netstat -ano | findstr :5432
taskkill /PID <PID> /F
```
Before running the backend
- Set up uv 
```
Install the uv package globally using documenation
uv init
uv venv
.venv/Scripts/activate
```
- To setup tables in postgres
```
python manage.py makemigrations
python manage.py migrate
```
- To get install the packages
```
uv add -r requirements.txt
```

