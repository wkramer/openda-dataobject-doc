## TimeSeriesFormatterDataObject.md

The `TimeSeriesFormatterDataObject` is suitable for use with files that contain time series. The actual reading and writing to the file is delegated to a `TimeSeriesFormatter`. 
For instance a csv file can be read using the `DelimitedTextTimeSeriesFormatter`.

### Example file

A CSV file containing times and values

```
time,value
60.0,0.0
120.0,0.0
180.0,0.0
240.0,0.0
300.0,0.0
360.0,0.0
420.0,0.0
480.0,0.0
540.0,0.0
600.0,0.0
660.0,25.469859691191957
720.0,25.469859691191957
```

### Configuration

```xml
<dataObject className="TimeSeriesFormatterDataObject">
  <path>timesSeriesFormatter.xml</path>
  <id>DATA_OBJECT_ID</id>
</dataObject>
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<timeSeriesFormatterConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <formatter class="org.openda.exchange.timeseries.DelimitedTextTimeSeriesFormatter">
    <!-- select the column containing times -->
    <dateTimeSelector>0</dateTimeSelector>
    <!-- select the column containing values -->
    <valueSelector>1</valueSelector>
    <!-- the character used as delimiter -->
    <delimiter>,</delimiter>
    <!-- the character used for comments -->
    <commentMarker>#</commentMarker>
    <!-- the number of header lines to skip -->
    <skipLines>1</skipLines>
    <!--  The role of the time series: input, output or inout
          when input is select OpenDA will not write to this file -->
    <role>inout</role>
  </formatter>
  <timeSeries id="model.locA.concentration1">
    c1_locA.csv
  </timeSeries>
  <timeSeries id="model.locB.concentration1">
    c1_locB.csv
  </timeSeries>
</timeSeriesFormatterConfig>
```

Note:  `<dateTimeSelector>` and `<valueSelector>` are not implemented yet. 
For now it is assumed that the first column in the file contains times and the second contains values.
Currently the lines skipped by with the `<skipLines>` will be retained when writting to file.

### Exchange items

| property | value                         | example  |
| -------- | ----------------------------- | -------- |
| type     | `TimeSeriesExchangeItem`           |          |
| id       | id from configured in `timesSeriesFormatter.xml`  | `model.locA.concentration1`, `model.locB.concentration1` |
| count    | as many as configured in `timesSeriesFormatter.xml` | 2        |




