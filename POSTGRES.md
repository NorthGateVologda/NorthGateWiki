## Документация по базе данных корпорации *NorthGate*

Общая информация о взаимодействии с базой данных.

## Полезные команды

Подключение из терминала с суперпользователем:

```sh
NIFI_CONT=$(sudo docker ps --filter "name=db_postgres" -q)
sudo docker exec -it $NIFI_CONT /bin/bash
su - postgres
psql -d northgate
```

Закрытие сессий:

```sql
SELECT pg_terminate_backend(pid)
FROM pg_stat_activity
WHERE pid <> pg_backend_pid()
AND datname = 'northgate';
```
