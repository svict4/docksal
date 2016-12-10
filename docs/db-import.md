# Automatic database import

The `db` service container can perform automatic import of database dump upon initialization.

# Setting up

#### 1. Create a folder for database dumps

Create a folder for database dumps inside project root called `db` (name can differ).

#### 2. Put `*.sql` or `*.sql.gz` file(s) into the newly created `db` folder.

!!! note "You can put multiple files" 
    You can put multiple `*.sql` and `*.sql.gz` files. They will all be imported in an alphabetical order. Database that is set in `MYSQL_DATABASE` variable is used.

#### 3. Add the following configuration

Add the following to `db` service in the project's `docksal.yml` file:

```yml
db:
  ...
  volumes:
    - ${PROJECT_ROOT}/db:/docker-entrypoint-initdb.d:ro
  ...
```

#### 4. Re-create containers

Run `fin reset`