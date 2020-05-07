# Postgres on Mac - Running But Cannot Connect

### Problem

Postgres has been installed on MacOS (Catalina) but cannot be connected to. Running `brew services start postgresql` indicates that Postgres is running. `brew services restart postgresql` has no effect.

### Solution

A crashed process may have left a rogue postmaster.pid file on the file system. Try clearing this and then starting Postgres:

  ```
  brew services stop postgresql
  rm /usr/local/var/postgres/postmaster.pid 
  brew services start postgresql
  ```
