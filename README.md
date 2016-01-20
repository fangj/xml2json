# xml2json
This function acts as an XML to JSON converter. The function is extremely small and is in pure JavaScript, therefore it has no dependencies. 
The converter takes XML attributes into consideration. 
## Installation
```
npm install *our_package*
or
use the function directly in your code
```
## Usage
### Without XML attributes
```javascript
var xml = ‘<person><name>John Doe</name></person>’;
var json = xml2json(xml); 

console.log(json); 
// prints ‘{“person”: {“name”: “John Doe”}}’
```
### With XML attributes
#### Single attribute
```javascript
var xml = ‘<person id=”1234”><name>John Doe</name></person>’;
var json = xml2json(xml);

console.log(json); 
// prints ‘{“person”: {“id”: “1234”, “name”: “John Doe”}}’
```
#### Multiple attributes
```javascript
var xml = ‘<person id=”1234” age=”30”><name>John Doe</name></person>’;
var json = xml2json(xml); 

console.log(json); 
// prints ‘{“person”: {“id”: “1234”, “age”: “30”, “name”: “John Doe”}}’
```
### Special cases
#### Orphan values
```javascript
var xml = ‘<person id=”1234”>Something</person>’;

// The xml string is converted to : 
// <person><id>1234</id>Something</person>’
//
// This line now contains an orphan value
// the xml string is then converted to :
// ‘<person><id>1234</id><_@ttribute>Something</_@ttribute></person>’

var json = xml2json(xml);
console.log(json); 
// prints ‘{“person”: {“id”: “1234”, “_@ttribute”: “Something”}}’
```
