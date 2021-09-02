# Postgres

### Download Postgres
- Postgres
```
sudo apt -y install postgresql postgresql-contrib
```
- Python Kit
```
python -m pip install pyscopg2
```

### How to use Postgres
- Connection
```
import psycopg2
conn = psycopg2.connect(host=host, port=5432, user=user, password=password)
```
- Set autocommit
```
conn.autocommit = True  #自動commit
```
- use
```
conn.cursor()
conn.execute(SQL)
```