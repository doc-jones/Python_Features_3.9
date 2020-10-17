# New Features in Python 3.9

'''Note: This is the first version of Python to default to the 64-bit installer on Windows. The installer now also actively disallows installation on Windows 7.

ZoneInfo get its timezone information from an IANA database installed on your computer'''

1. New zoneinfo Library  
2. Updating Dictionaries  
3. More Flexible Decorators  
4. Annotated Type Hints  
5. More Changes  
6. Should you Upgrade?  
7. Summary  
  
## Time Zone Support  
  
```Before 3.9
>>>from datetime import datetime, timezone
>>>datetime.now()`
datetime.datetime(2020, 9,  8, 2, 45, 416684)
>>>datetime.now(tz=timezone, utc)
datetime.datetime(2020, 9,  8, 2, 47, 24553, tzinfo=datetime.timezone.utc)```

```**Now with zoneinfo**

>>>from zoneinfo import ZoneInfo
>>>ZoneInfo("America/New_York")
zoneinfo.ZoneInfo(key='America/New_York')
```

```**Set new timezone**

>>>datetime.now(tz=ZoneInfo("Europe/Oslo))
datetime.datetime(2020, 9, 23, 19, 27, 38, 544399, tzinfo=zoneinfo.ZoneInfo(key='Europe/Oslo'))```


```**Change timezone - .astimezone method**

>>>release_date = datetime(2020, 18, 5, 3, 9, tz=ZoneInfo("America/New_York"))
>>>release_date.astimezone(ZoneInfo("Europe/Oslo"))
datetime.datetime(2020, 10, 5 12, 9, tz=zoneinfo.ZoneInfo(key="Europe/Olso"))```

```**Timezone Database - expected value varies by computer**
>>>len(zoneinfo.available_timezones())
595
```

```**Timezone Name - .tzname method**
>>>tz = ZoneInfo("America/San_Francisco")
>>>tz.tzname(datetime(2020, 10, 5))
'PDT'
>>>tz.tzname(datetime(2020, 12, 5))
'PST'
```

If your computer doesn't come with the database installed Python provides one you can install.  
`python -m pip install tzdata`
