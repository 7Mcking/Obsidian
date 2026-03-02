# JS Language
```
var -> define a variable

for(;;){} -> for loop

if () { //If else

} else {

}

```
# Class Hierarchy
```
SpreadsheetApp -> Spreadsheet -> Sheet
```
### SpreadsheetApp Class Methods
```
getActiveSpreadSheet()
```
### Spreadsheet Class Methods
```
getActiveSheet()
getSheetByName()
```
### Sheet Class methods
```
getRange(int row, int column)
setValue(T value)
getValue()
clear(); -> Clears everything
clearContent();-> Clears only Content
```
## Logger Methods
```
Logger.clear()
```
## Custom Functions

**For auto complete to work**
```
add comments on top of the function and expose it to the sheet using @customfunction
add hints what the input to the function is using 
@param x
```
