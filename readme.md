# Import NYC Taxi into a docker of PostgreSQL

download and extract the NYC Taxi rides data from this link into the data directory
https://docs.timescale.com/timescaledb/latest/tutorials/nyc-taxi-cab/#main-content

launch a postgreSQL docker 
```
# envrionment variables
export DOCKER_NAME=pg101
export PORT_TO_USE=5432
export PG_USER=myuser
export PG_PASSWORD=mypass
export PG_DATABASE=mydb
export PG_HOST_PATH=$HOME/docker_db_fs/$DOCKER_NAME

# create the host filesystem for the DB data directory
mkdir -p $PG_HOST_PATH

# docker run command
docker run -d                                      \
     --name $DOCKER_NAME                           \
     -p     $PORT_TO_USE:5432                      \
     -e     POSTGRES_USER=$PG_USER                 \
     -e     POSTGRES_PASSWORD=$PG_PASSWORD         \
     -e     POSTGRES_DB=$PG_DATABASE               \
     -e     PGDATA=/var/lib/postgresql/data/pgdata \
     -v     $PG_HOST_PATH:/var/lib/postgresql/data \
     postgres:latest
```

## Create a python virtual environment
```
python -m venv venv
```

## Install the required packages
```
pip install -r requirements.txt
```

## Open the notebook and run the cells
*the ```pip install``` also appears on the first cell of the notebook
  


