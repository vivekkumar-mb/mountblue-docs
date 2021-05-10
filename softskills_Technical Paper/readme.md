# **DOM (Document Object Model)**

**Introduction**:
The Document Object Model (DOM) is a programming interface for [HTML](https://en.wikipedia.org/wiki/HTML) and [XML](https://en.wikipedia.org/wiki/XML#:~:text=Extensible%20Markup%20Language%20(XML)%20is,free%20open%20standards%E2%80%94define%20XML.)(Extensible markup language) documents. It defines the logical structure of documents and the way a document is accessed and manipulated.

**Note**: It is called a Logical structure because DOM doesn’t specify any relationship between objects.

DOM is a way to represent the webpage in a structured hierarchical way so that it will become easier for programmers and users to go through the document. With DOM, it becomes easy to access and manipulate tags, IDs, classes, Attributes or Elements using commands or methods provided by the Document object.

## **Structure of a DOM**

### *Example: XML*

``` xml
<Table>
   <ROWS>
      <TR>
         <TD>Car</TD>
         <TD>Scooter</TD>
      </TR>
      <TR>
         <TD>MotorBike</TD>
         <TD>Bus</TD>
      </TR>
   </ROWS>
</Table>
```

### **DOM logical tree**

![Image of DOM Structure](DOM_table_example.png)

## **Accessing the DOM**

You don't have to do anything special to begin using the DOM. Different browsers have different implementations of the DOM, and these implementations exhibit varying degrees of conformance to the actual DOM standard, but every web browser uses some document object model to make web pages accessible through JavaScript.

When you create a script–whether it's inline in a  `<script>` element or included in the web page by means of a script loading instruction–you can immediately begin using the API for the `document` or `window` elements to manipulate the document itself or to get at the children of that document, which are the various elements in the web page.

This following JavaScript will display an alert when the document is loaded:

``` html
<body onload="window.alert('Welcome to my home page!');">
```

Another example. This function creates a new H1 element, adds text to that element, and then adds the H1 to the tree for this document:

``` html
<html>
  <head>
    <script>
       // run this function when the document is loaded
       window.onload = function() {

         // create a couple of elements in an otherwise empty HTML page
         const heading = document.createElement("h1");
         const heading_text = document.createTextNode("Big Head!");
         heading.appendChild(heading_text);
         document.body.appendChild(heading);
      }
    </script>
  </head>
  <body>
  </body>
</html>
```

## **How To Access Elements in the DOM**

**Introduction**

In Understanding the DOM Tree and Nodes, we went over how the DOM is structured as a tree of objects called nodes, and that nodes can be text, comments, or elements. Usually when we access content in the DOM, it will be through an HTML element node.

To be proficient at accessing elements in the DOM, it is necessary to have a working knowledge of CSS selectors, syntax and terminology as well as an understanding of HTML elements. This are some ways to access elements in the DOM: by ID, class, tag, and query selectors.

**Overview**
|Gets | Selector Syntax | Method |  
|-----------|:-----------:|-----------:|  
|ID |#demo |getElementById()
|Class| .demo |getElementsByClassName()
|Tag |demo |getElementsByTagName()
|Selector(single) || querySelector()
|Selector (all) || querySelectorAll()

</br>

### *Example: HTML*
``` html 
<html>
<head>
  <title>getElementById example</title>
</head>
<body>
  <p id="para">Some text here</p>
  <button onclick="changeColor('blue');">blue</button>
</body>
</html>
```
* Here is an example of the way to get the `id` of the `p` tag and change the color of the content of that `id`, by calling the function `changeColor()`.
### *Example: getElementById()* 


``` javascript 
function changeColor(newColor) {
  var elem = document.getElementById('para');
  elem.style.color = newColor;
}
```
## **Some JavaScript Helper Methods**

1. **`every()`** Method: This method is used to check if all elements of an array pass the test that is implemented by the passed higher-order function. What compiler does under the hood is, it iterates over the employees array and check for all employee, if he is a developer or not. As in this case, it should return false.

>Input

``` javascript
const employees = [
  { name: "Sam",      age: 25, role: "Developer" },
  { name: "John",     age: 32, role: "Manager"   },
  { name: "Ronaldo",  age: 29, role: "Architect" },
  { name: "Perker",   age: 25, role: "Developer" },
  { name: "Sophia",   age: 38, role: "Director"  },
  { name: "kristine", age: 21, role: "Developer" },
];
  
function isDeveloper(employee) {
  return employee.role === "Developer";
}
console.log(employees.every(isDeveloper));
```

>Output:

```javascript
false
```

2. **`fill()`** Method: This method fills the array with a static value. It overrides all array values starting from the first element(0th index) and up to the last element (array.length-1) index.

>Input

```javascript
const employees = [
    { name: "Sam",      age: 25, role: "Developer" },
    { name: "John",     age: 32, role: "Manager"   },
    { name: "Ronaldo",  age: 29, role: "Architect" },
    { name: "Perker",   age: 25, role: "Developer" },
    { name: "Sophia",   age: 38, role: "Director"  },
    { name: "kristine", age: 21, role: "Developer" },
];
          
const newEmployees = employees.fill(
    { name: "Sam", age: 25, role: "Developer" });
console.log(employees);
  
console.log(newEmployees === employees);    // true
```

>Output:

```javascript
[
 { name: 'Sam', age: 25, role: 'Developer' },
 { name: 'Sam', age: 25, role: 'Developer' },
 { name: 'Sam', age: 25, role: 'Developer' },
 { name: 'Sam', age: 25, role: 'Developer' },
 { name: 'Sam', age: 25, role: 'Developer' },
 { name: 'Sam', age: 25, role: 'Developer' }
]

true
```

3. **`filter()`** Method: This method filters the array that passes the test with the function passed to it. It returns a new array.

>Input

```javascript
const employees = [
    { name: "Sam",      age: 25, role: "Developer" },
    { name: "John",     age: 32, role: "Manager"   },
    { name: "Ronaldo",  age: 29, role: "Architect" },
    { name: "Perker",   age: 25, role: "Developer" },
    { name: "Sophia",   age: 38, role: "Director"  },
    { name: "kristine", age: 21, role: "Developer" },
];
          
function filterDevEmp(employee) {
  return employee.role === "Developer";
}
const filteredDevEmployees = employees.filter(filterDevEmp);
console.log(filteredDevEmployees);
```

>Output:

```javascript
[
 { name: 'Sam', age: 25, role: 'Developer' },
 { name: 'Perker', age: 25, role: 'Developer' },
 { name: 'kristine', age: 21, role: 'Developer' }
]
```

>References

1. To Know More about aceessing the DOM Elements [click](https://www.digitalocean.com/community/tutorials/how-to-access-elements-in-the-dom#:~:text=Accessing%20Elements%20by%20ID,method%20of%20the%20document%20object.&text=In%20order%20to%20be%20accessed,must%20have%20an%20id%20attribute.)
2. CheckOut [this](https://www.geeksforgeeks.org/dom-document-object-model/) Amazing Article About DOM, on geekforgeeks.
3. Some More Resource for JavaScript [Helper Methods](https://www.geeksforgeeks.org/javascript-helper-methods/)
