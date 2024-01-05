FROM mcr.microsoft.com/mssql/server:2017-latest
ENV MSSQL_SA_PASSWORD=myPassword
ENV ACCEPT_EULA=Y

COPY ./db.bak /var/opt/mssql/backup/db.bak
# COPY restore.sql restore.sql
# RUN (/opt/mssql/bin/sqlservr --accept-eula & ) | grep -q "Starting database restore" && /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P 'myPassword' -d master -i restore.sql
# RUN   docker exec -it mssql-server /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "myPassword" -Q "RESTORE DATABASE Database1 FROM DISK = '/var/opt/mssql/backup/db.bak' WITH MOVE 'Database1_Data' TO '/var/opt/mssql/data/db.mdf', MOVE 'Database1_Log' TO '/var/opt/mssql/data/db.ldf'"