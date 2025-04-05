# WEEK 7 Practise Question 3
 Write a Python program to output the jersey number of the player. Player's name is given in a file named 'player.txt' resides in the same folder as python program file. 
The output of the python program is only jersey number.  
For example, if the jersey number of the player is 99. Then output must be 99 only. Note: No spaces.

## Solution
```python
import sys, os, psycopg2 as p
f = open("player.txt" , "r")
n = f.read()

connect = p.connect(
database = sys.argv[1],
user = os.environ.get('PGUSER') ,
password = os.environ.get('PGPASSWORD') ,
host = os.environ.get('PGHOST'),
port = os.environ.get('PGPORT'))

cursor = connect.cursor()
query = "select jersey_no from players where name = '{}' ".format(n)
cursor.execute(query)
result = cursor.fetchall()
for i in result:
    print(i[0])

cursor.close()
connect.close()
```
