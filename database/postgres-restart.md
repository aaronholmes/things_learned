# Postgres on Mac - Running / Cannot Connect

### Problem

Postgres has been installed on MacOS (Catalina) by using brew, but cannot be connected to. Running `brew services start postgresql` indicates that Postgres is running. `brew services restart postgresql` has no effect and users still cannot connect (Default cannot connect / is postgres running error message).

### Solution

A crashed process may have left a rogue postmaster.pid file on the file system. Try clearing this and then starting Postgres:

  ```
  brew services stop postgresql
  rm /usr/local/var/postgres/postmaster.pid 
  brew services start postgresql
  ```
