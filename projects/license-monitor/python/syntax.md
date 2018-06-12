| Syntax Check |  |
| :--- | :--- |
| Check type of object | type\(obj\) [r1](https://stackoverflow.com/questions/35490420/how-to-check-type-of-object-in-python) |
| Conver none type to int or String | [r1](https://stackoverflow.com/questions/3930188/how-to-convert-nonetype-to-int-or-string) |
| read a txt file into a string | data = myfile.read\(\) [r1](https://stackoverflow.com/questions/8369219/how-do-i-read-a-text-file-into-a-string-variable-in-python) |
| var increment ++ | number += 1 [py doesn't support ++](https://stackoverflow.com/questions/2632677/python-integer-incrementing-with/2632870) |
| list all file of a directory | os.listdir\(\) [r1](https://stackoverflow.com/questions/3207219/how-do-i-list-all-files-of-a-directory), [r2](http://www.bogotobogo.com/python/python_traversing_directory_tree_recursively_os_walk.php) |
| check if a string is empty | if not myString [r1](https://stackoverflow.com/questions/9573244/most-elegant-way-to-check-if-the-string-is-empty-in-python) |
| writing HTML using Python | [r1](http://www.dalkescientific.com/writings/NBN/writing_html.html) |



**Code Snippet**

```
# SQL processing
import cx_Oracle
con = cx_Oracle.connect('pythonhol/welcome@127.0.0.1/orcl')
cur = con.cursor()
cur.execute('select * from departments order by department_id')
               
res = cur.fetchall()
print res
            
cur.close()
con.close()


```

```
# Dates/time difference
from datetime import datetime
date_format = "%m/%d/%Y"    # for time_diff: %H:%M:%S 
a = datetime.strptime('8/18/2008', date_format)
b = datetime.strptime('9/26/2008', date_format)
delta = b - a
diff_days = delta.days
hours = timedelta.days * 24   # convert into hours
hours = (timedelta.seconds) / 3600    # convert into seconds

# 
from datetime import date
f_date = date(2014, 7, 2)
l_date = date(2014, 7, 11)
delta = l_date - f_date
print(delta.days)

Ref: 
https://stackoverflow.com/questions/3096953/how-to-calculate-the-time-interval-between-two-time-strings
https://stackoverflow.com/questions/151199/how-do-i-calculate-number-of-days-between-two-dates-using-python
https://www.odoo.com/forum/help-1/question/how-to-calculate-hours-and-minutes-between-two-date-time-fields-76191



```



