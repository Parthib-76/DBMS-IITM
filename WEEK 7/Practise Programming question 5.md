# WEEK 7 Practise Question 5

write a Python program to print the playground of the given team id. team_id is given in a file named 'team.txt' resides in the same folder as python program file.
 • The output of the python program is only playground name.
 • For example, if the team_id is 'T0002' . Then output must be Villa Park only

## SOLUTION:

```python 
import sys, os, psycopg2 as p
f = open("team.txt" , "r")
n = f.read()
conn = p.connect(
database = sys.argv[1],
user = os.environ.get('PGUSER'),
password = os.environ.get('PGPASSWORD'),
host = os.environ.get('PGHOST'),
port = os.environ.get('PGPORT'))
cur = conn.cursor()
query = "Select playground from teams where team_id = '{}' ".format(n)
cur.execute(query)
result = cur.fetchall()

for i in result :
     print (i[0])

cur.close()
conn.close()
```
