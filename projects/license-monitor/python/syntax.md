| Syntax Check |  |
| :--- | :--- |
| Check type of object | type\(obj\) [r1](https://stackoverflow.com/questions/35490420/how-to-check-type-of-object-in-python) |
| Conver none type to int or String | [r1](https://stackoverflow.com/questions/3930188/how-to-convert-nonetype-to-int-or-string) |
| read a txt file into a string | data = myfile.read\(\) [r1](https://stackoverflow.com/questions/8369219/how-do-i-read-a-text-file-into-a-string-variable-in-python) |
| var increment ++ | number += 1 [py doesn't support ++](https://stackoverflow.com/questions/2632677/python-integer-incrementing-with/2632870) |
| list all file of a directory | os.listdir\(\) [r1](https://stackoverflow.com/questions/3207219/how-do-i-list-all-files-of-a-directory), [r2](http://www.bogotobogo.com/python/python_traversing_directory_tree_recursively_os_walk.php) |
| check if a string is empty | if not myString [r1](https://stackoverflow.com/questions/9573244/most-elegant-way-to-check-if-the-string-is-empty-in-python) |
| writing HTML using Python | [r1](http://www.dalkescientific.com/writings/NBN/writing_html.html) |
| convert tuple to dict | [r1](https://www.tutorialspoint.com/How-I-can-convert-a-Python-Tuple-into-Dictionary) |
| Iterating over dict | [r1](https://dev-notes.eu/2017/09/iterating-over-dictionary-in-python/), |
| f-string: f"This is my {variable}" | [r1](https://hackernoon.com/a-closer-look-at-how-python-f-strings-work-f197736b3bdb) |
| String formatters : .format\(\) | [r1](https://www.digitalocean.com/community/tutorials/how-to-use-string-formatters-in-python-3), [r2](https://pyformat.info/), [r3](https://stackoverflow.com/questions/28343745/how-do-i-print-a-sign-using-string-formatting) |
| return multiple values | [r1](https://stackoverflow.com/questions/9752958/how-can-i-return-two-values-from-a-function-in-python) |
| cx\_Oracle: timedelta | [r1](https://pymotw.com/2/datetime/) |
| convert datetime obj to a string | [r1](https://stackoverflow.com/questions/10624937/convert-datetime-object-to-a-string-of-date-only-in-python) |
| why use epoch\(timestamp\) | [r1](https://stackoverflow.com/questions/20822821/what-is-a-unix-timestamp-and-why-use-it) |
| convert date str with timezone t epoch: use datetime.timestamp\(\) | [r1](https://stackoverflow.com/questions/42110761/converting-date-string-with-timezone-to-epoch),[ r2, ](https://www.tutorialspoint.com/How-to-convert-Python-datetime-to-epoch-with-strftime) |
| convert datetime to a timezone | [r1](https://howchoo.com/g/ywi5m2vkodk/working-with-datetime-objects-and-timezones-in-python),[ r2](https://stackoverflow.com/questions/25668415/why-does-python-new-york-time-zone-display-456-instead-400) |
| convert timestamp with timezone to datetime to date str | [r1](https://timestamp.online/article/how-to-convert-timestamp-to-datetime-in-python),[ r2](https://stackoverflow.com/questions/9744775/how-to-convert-integer-timestamp-to-python-datetime), [r3](https://coderwall.com/p/-uuawg/how-do-i-convert-a-unix-timestamp-to-human-readable-format-in-python) |

**Code Snippets**

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

```
# Timestamp to datetime to date str (timezone)
def timestamp_to_date(time_stamp):
    #date = datetime.strftime("%m/%d/%Y-%H:%M:%S", time_stamp)
    ny_tz = pytz.timezone('America/New_York')  // Ref: https://docs.oracle.com/cd/B19306_01/server.102/b14225/ch4datetime.htm#i1007699
    timestamp_to_datetime = datetime.fromtimestamp(time_stamp, tz=ny_tz)
    datetime_to_date = datetime.strftime(timestamp_to_datetime, "%m/%d/%Y-%H:%M:%S")
    return datetime_to_date
    
# date str to datetime to timestamp    
def datestr_to_timestamp(date_str):
    # OFFSET TIMEZONE
    ny_tz = pytz.timezone('America/New_York')
    date_to_datetime = datetime.strptime(date_str, "%m/%d/%Y-%H:%M:%S")
    add_tz = ny_tz.localize(date_to_datetime)
    datetime_to_timestamp = add_tz.timestamp()
    return datetime_to_timestamp
```



