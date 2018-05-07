## IniDataObject

The `IniDataObject` reads a `ini` file containing multiple `keys`. Every `key` has a name and a value, delimited by an equals sign (=). The name appears to the left of the equals sign. The `IniDataObject` creates an `DoubleExchangeItem` for each `key` with the id equal to the `key` name.

### Example files

Ini file containing two keys
```ini
; comment text
elasticity = 4.0
viscosity  = 1E-3
```

### Configuration

```xml
<dataObject className="IniDataObject">
  <path>file.ini</path>
</dataObject>
```


```xml
<dataObject className="IniDataObject">
  <path>file.ini</path>
  <arg>keys="elasticity"</arg>
  <arg>timeInfoKeys=start_time,end_time</arg>
  <arg>timeInfoPattern=%Y-%m-%dT%H:%M:%S</arg>
</dataObject>
```

ISO8601 %Y-%m-%dT%H:%M:%S
Unix timestamp %s



### Exchange items

| property | value                         |
| -------- | ----------------------------- |
| type     | `DoubleExchangeItem`          |
| id       | `key` name                    |
| count    | number of `key`-`value` pairs |

## IniTimeInfoDataObject

The `IniTimeInfoDataObject` reads a `ini` file containing multiple `keys`. Every `key` has a name and a value, delimited by an equals sign (=). The name appears to the left of the equals sign. The `IniTimeInfoDataObject` create a `TimeInfo` exchange item from the `key` value. The value should eithe be a string containing the date and time or an float containing the Unix time stamp, i.e. seconds since Jan 01 1970 (UTC).

### Example files

File containing `start_time` and `end_time` as iso8601 date time string.

```ini
; comment text
start_time = 2018-05-03T12:00:00Z 
end_time   = 2018-05-03T13:00:00Z 
```

File containing `start_time` and `end_time` as unix timestamp.

```ini
; comment text
start_time = 1525380220 
end_time   = 1525380260
```

### Configuration

```xml
<dataObject className="IniTimeInfoDataObject">
  <path>file.ini</path>
  <arg>datetimeformat="yyyy-MM-dd'T'HH:mm:ssZ"</arg>
</dataObject>
```

### Exchange items

| property | value                         | example  |
| -------- | ----------------------------- | -------- |
| type     | `TimeInfo`                    |          |
| id       | `key` name                    | `start_time`, `end_time` |
| count    | number of `key`'s             | 2        |

