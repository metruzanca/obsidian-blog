See https://stackoverflow.com/questions/24718706/backup-restore-a-dockerized-postgresql-database

## Backup your databases
```sql
docker exec -t your-db-container pg_dumpall -c -U postgres > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql
```

## Restore your databases

```sql
cat your_dump.sql | docker exec -i your-db-container psql -U postgres
```

