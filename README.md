<p align="center">
  <img height=400px width=600px style='display:block; margin:auto' src='https://d1dwq032kyr03c.cloudfront.net/upload/images/20200908/201297986I73Dv2Ocj.png'/>
</p>  

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
### Use Case
1. Research
```
sql = f'SELECT * FROM "{table}"'
cursor = conn.cursor()
cursor.execute(sql)
data_list = cursor.fetchall()
conn.close()
```
2. Create  
```
sql = f'create table "{table}"\
                      (id Serial Primary key          # Serial 為postgres序列(不須加入int)
                      test1 varchar(25) Foreign key
                      test2 int default 0
                      test3 varchar(25) default Null)'
cursor = conn.cursor()
cursor.execute(sql)
conn.commit()
conn.close()
```
3. Update  
```
sql = f'update "{table}"(test1, test2) VALUES("test", "tewtt")'
cursor = conn.cursor()
cursor.execute(sql)
conn.commit()
conn.close()
```
4. Delete
```
sql = f'delete from "{table}" where test1 = "test"'
cursor = conn.cursor()
cursor.execute(sql)
conn.commit()
conn.close()
```
5. Reset Sequence
```
sql = f'ALTER SEQUENCE "{table}" RESTART WITH 1'
cursor = conn.cursor()
cursor.execute(sql)
conn.commit()
conn.close()
```

