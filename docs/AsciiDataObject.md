## AsciiDataObject
An ASCII file containing one value on each line. The `AsciiDataObject` store all values in a single `ArrayExchangeItem`.

### Example file

```
1.0
2.0
0.9
```

### Configuration

```xml
<dataObject className="AsciiDataObject">
  <path>waterlevel.dat</path>
</dataObject>
```

### Exchange items

| property | value                         | example  |
| -------- | ----------------------------- | -------- |
| type     | `ArrayExchangeItem`           |          |
| id       | file name without extension   | `waterlevel` |
| count    | one per file                  | 1        |



