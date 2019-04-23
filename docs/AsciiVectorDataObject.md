## AsciiVectorDataObject

The `AsciiVectorDataObject` reads an ASCII file containing one value on each line and creates a single exchange item of type `ArrayExchangeItem` containing all the values. Alternatively, when using the `as_separate_exchange_items` in the dataobject configuration, an exchange item is created for each separate value.

### Example file

```
1.0
2.0
0.9
```

### Configuration

```xml
<dataObject className="AsciiVectorDataObject">
  <path>waterlevel.dat</path>
  <id>DATA_OBJECT_ID</id>
  <!-- Optional argument -->
  <arg>as_separate_exchange_items</arg>
</dataObject>
```

### Exchange items

With the standard configuration a single exchange item is created containing all values in an array.
For the example file above this results in:

| property | value                         | example  |
| -------- | ----------------------------- | -------- |
| type     | `ArrayExchangeItem`           |          |
| id       | file name without extension   | `waterlevel` |
| count    | one per file                  | 1        |

When using the `as_separate_exchange_items` option a separate exchange item for each line/value is created.
For the example file above this results in:

| property | value                                | example  |
| -------- | ------------------------------------ | -------- |
| type     | `DoubleExchangeItem`                 |          |
| id       | base: file name without extension, numbered for each value in the file   | `waterlevel@1`, `waterlevel@2`, `waterlevel@3` |
| count    | one for each line containing a value | 3        |




