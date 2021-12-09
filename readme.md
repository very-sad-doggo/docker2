1. Creating network: 
docker network create --driver=bridge --subnet=172.28.0.0/16 --ip-range=172.28.5.0/24 --gateway=172.28.5.254 backend_network

2. Frontend (docker_homework/fronetnd folder)
Creating image for frontend. "docker build . -t vladimir/frontend"
Running frontend. docker run -d -p 3000:3000 --network backend_network --ip 172.28.5.9 --name frontend vladimir/frontend

3. Database (docker_homework folder)
Creating image for database. "docker build . -t database:01 
Running databse. docker run -d -p 5432:5432 --restart=on-failure:10 -e POSTGRES_PASSWORD=django -e POSTGRES_USER=django -e POSTGRES_DB=django -e USERMAP_UID=999 -e USERMAP_GID=999 -d -v postgres:/var/lib/postgresql/data --network backend_network --ip 172.28.5.5 --name database database:01

4. Backend (docker_homework/lib_catalog folder) 
Creating image for backend. "docker build . -t vladimir/backend"
Running backend. docker network create --driver=bridge --subnet=172.28.0.0/16 --ip-range=172.28.5.0/24 --gateway=172.28.5.254 backend_network