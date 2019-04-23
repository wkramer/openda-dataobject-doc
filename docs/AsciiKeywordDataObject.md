## AsciiKeywordDataObject

This data object searches for the `oda:` keyword in inline comments of Ascii files.
Prerequisite is that the model supports an Ascii input or output file which allows inline comments.
For instance YAML allows inline comments.  

For each occurance of the keyword in the `AsciiKeywordDataObject` searches for an integer or a floating point value and creates a new exchange item. The `id` of the exchange item is taken from the full comment, e.g.  `oda:my_id` results in a exchange item id `my_id`. When the line contains multiple values, multiple exchange items are generated where the exchange item is numbered like `my_id@1` , `my_id@2` etc.

### Example file

This is a YAML file with the additional inline comments `#oda:time_control` and `#oda:reaction_time`.

```yaml
%YAML 1.1
---
# input for 1d reactive pollution model
#
# simulation timespan
time: [ 0.0, 60.0, 15000.0] #oda:time_control
#unit is always seconds
unit : 'seconds'
# sources mass/m^3/s
reaction_time: 2000.0  #oda:reaction_time
```

### Configuration

```xml
<dataObject className="AsciiKeywordDataObject">
  <path>config.yaml</path>
  <id>DATA_OBJECT_ID</id>
</dataObject>
```

### Exchange items

| property | value                                        | example  |
| -------- | -------------------------------------------- | -------- |
| type     | `DoubleExchangeItem`                         |          |
| id       | part of keyword without prefix               | `reaction_time` |
|          | numbered when line contains multiple values  | `time_control@1` , `time_control@2`, `time_control@3` |




