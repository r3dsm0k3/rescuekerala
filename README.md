# rescuekerala

Website for coordinating rehabilitation of people affected in the 2018 Kerala Floods

Join our slack channel

https://join.slack.com/t/keralarescue/shared_invite/enQtNDE4NzUyNjg4MjQ3LTJiMDU0ZmFhODNlNDE3ZDc4ZmFlMGI0YmQ0MzI0NWYyNThlOTgwYTM2Y2JlYzMxMDMxMzUwY2E2MmVmNDQyNmE


# Kerala Rescue

Website for coordinating rehabilitation of people affected in the 2018 Kerala Floods

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.


### Using Docker

- Only pre-requisite is having docker and docker-compose installed 
 > To install docker and necessary tools refer to the official documentation [here](https://github.com/IEEEKeralaSection/rescuekerala/pull/445)
- Execute `sh docker.sh` in this directory (if you do not have permissions on the `docker.sh`, do `chmod +x docker.sh`)
> Now you can open the site in a browser (localhost:8000) and continue test/development. Since the local directory (rescuekerala) is mapped to the container as "/rescuekerala", whatever changes that is made in the host directory are reflected inside the container too. When the source files are changed in the host machine, the webserver typically restarts automatically, the UI needs to be refreshed
- Server will start running at `localhost:8000`
- `Ctrl+C` to stop

### Prerequisites

You will need to have following softwares in your system

- Python 3
- Postgres
- git

### Installing

Setting up development environment

create database and user in postgres for kerala rescue and give privileges

```
psql user=postgres
Password: 
psql (10.4 (Ubuntu 10.4-0ubuntu0.18.04))
Type "help" for help.

postgres=# CREATE DATABASE rescuekerala;
CREATE DATABASE
postgres=# CREATE USER rescueuser WITH PASSWORD 'password';
CREATE ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE rescuekerala TO rescueuser;
GRANT
postgres=# \q

```
Clone the repo
```
git clone https://github.com/IEEEKeralaSection/rescuekerala.git
cd rescuekerala
```

Copy sample environment file and configure it as per your local settings

```
cp .env.example .env
```

If you cant copy the environment or is facing difficulty in starting the server , Copy the settings file from
https://github.com/vigneshhari/keralarescue_test_settings for local testing

Install dependencies

```
pip3 install -r requirements.txt
```

Run Database migrations

```
python3 manage.py migrate
```

Setup staticfiles
```
python3 manage.py collectstatic
```

Run the server

```
python3 manage.py runserver
```
Now open localhost:8000 in the browser
