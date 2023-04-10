# POSTGRESQL QUERY OPTIMIZATION

Download postgres-air database from https://drive.google.com/drive/folders/13F7M80Kf_somnjb-mTYAnh1hW1Y_g4kJ and decompress downloaded data and locate one with .sql extension and move it to the backups folder and name it postgres_air.sql

Create postgres docker container (you can adjust port and password)

```docker-compose up -d```

After that run this command to create database postgres_air

```docker exec -it container_name psql -U postgres -c "CREATE DATABASE postgres_air;"```

Next backup data with downloaded postgres_air.sql file

```cat ./backups/postgres_air.sql | docker exec -i container_name psql -U postgres postgres_air```

Create indexes via script provided in backups directory

```docker exec -i container_name psql -U postgres postgres_air < ./backups/create_indexes.sql```