# Alwatr PostgreSQL Container

Alpine-based PostgreSQL container image with orchestrations, packaged by Alwatr.

## Environment Variables

| Variable                                | Default Value        | Description        |
|-----------------------------------------|----------------------|--------------------|
| `POSTGRES_CHECKPOINT_COMPLETION_TARGET` | `0.7`                |                    |
| `POSTGRES_CHECKPOINT_SEGMENTS`          | `32`                 | <=9.4              |
| `POSTGRES_DATESTYLE`                    | `iso, mdy`           |                    |
| `POSTGRES_DB`                           | `postgres`           |                    |
| `POSTGRES_DEFAULT_STATISTICS_TARGET`    | `100`                |                    |
| `POSTGRES_DEFAULT_TEXT_SEARCH_CONFIG`   | `pg_catalog.english` |                    |
| `POSTGRES_EFFECTIVE_CACHE_SIZE`         | `1GB`                |                    |
| `POSTGRES_DB_EXTENSIONS`                |                      | Separated by comma |
| `POSTGRES_LC_MESSAGES`                  | `en_US.utf8`         |                    |
| `POSTGRES_LC_MONETARY`                  | `en_US.utf8`         |                    |
| `POSTGRES_LC_NUMERIC`                   | `en_US.utf8`         |                    |
| `POSTGRES_LC_TIME`                      | `en_US.utf8`         |                    |
| `POSTGRES_LOG_TIMEZONE`                 | `UTC`                |                    |
| `POSTGRES_MAINTENANCE_WORK_MEM`         | `128MB`              |                    |
| `POSTGRES_MAX_CONNECTIONS`              | `100`                |                    |
| `POSTGRES_MAX_WAL_SIZE`                 | `2GB`                | >=9.5              |
| `POSTGRES_MIN_WAL_SIZE`                 | `1GB`                | >=9.5              |
| `POSTGRES_SHARED_BUFFERS`               | `512MB`              |                    |
| `POSTGRES_SHARED_MEMORY_TYPE`           | `posix`              | >=9.4              |
| `POSTGRES_TIMEZONE`                     | `UTC`                |                    |
| `POSTGRES_PASSWORD`                     |                      | REQUIRED           |
| `POSTGRES_USER`                         | `postgres`           |                    |
| `POSTGRES_WAL_BUFFERS`                  | `16MB`               |                    |
| `POSTGRES_WORK_MEM`                     | `5MB`                |                    |

## Orchestration Actions

```shell
make COMMAND [params ...]
 
commands:
    import source=</path/to/dump.zip or http://example.com/url/to/dump.sql.gz> [user password db host  binary] 
    backup filepath=</path/to/backup.sql.gz> [user password host db ignore=<"table1;table2"> nice ionice] 
    query query=<SELECT 1> [user password db host] 
    query-silent query=<SELECT 1> [user password db host]
    check-ready [user password db host max_try wait_seconds delay_seconds]  
    
default params values:
    user $POSTGRES_USER
    password $POSTGRES_PASSWORD
    db $POSTGRES_DB
    host localhost
    max_try 1
    wait_seconds 1
    delay_seconds 0
    ignore ""
    binary 0
    nice 10
    ionice 7    
```
