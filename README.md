# postgres-queries

Create readonly user for a database

```
\c my_db

CREATE USER readonly_user WITH PASSWORD 'password';
GRANT CONNECT ON DATABASE my_db TO readonly_user;
GRANT USAGE ON SCHEMA public TO readonly_user;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO readonly_user;
GRANT SELECT ON ALL SEQUENCES IN SCHEMA public TO readonly_user;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO readonly_user;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON SEQUENCES TO readonly_user;
```

Delete  readonly_user

```
REVOKE ALL PRIVILEGES ON ALL TABLES IN SCHEMA public FROM readonly_user;
REVOKE ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public FROM readonly_user;
REVOKE ALL PRIVILEGES ON ALL FUNCTIONS IN SCHEMA public FROM readonly_user;
REVOKE ALL PRIVILEGES ON SCHEMA public FROM readonly_user;
ALTER DEFAULT PRIVILEGES IN SCHEMA public REVOKE ALL ON SEQUENCES FROM readonly_user;
ALTER DEFAULT PRIVILEGES IN SCHEMA public REVOKE ALL ON TABLES FROM readonly_user;
ALTER DEFAULT PRIVILEGES IN SCHEMA public REVOKE ALL ON FUNCTIONS FROM readonly_user;
REVOKE USAGE ON SCHEMA public FROM readonly_user;
REVOKE ALL PRIVILEGES ON DATABASE my_db FROM readonly_user;
DROP USER readonly_user ;
```
