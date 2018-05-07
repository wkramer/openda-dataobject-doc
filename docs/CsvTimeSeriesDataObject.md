## CsvTimeSeriesDataObject

### Configuration

```xml
<dataObject className="CsvTimeSeriesDataObject">
    <path>file.csv</path>
</dataObject>
```

### Example file

```csv
datetime,parameter1,parameter2
2018-05-03T12:00:00Z,1.0,2.78
2018-05-03T12:05:00Z,2.0,3.14
2018-05-03T12:10:00Z,3.0,1.62
```

### Exchange items

| property | value                         | example  |
| -------- | ----------------------------- | -------- |
| type     | `TimeSeries`                  |          |
| id       | column header                 | `parameter1`, `parameter2` |
| count    | number of columns - 1         | 2        |