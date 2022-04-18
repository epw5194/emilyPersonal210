# XPath Exercise 1 
## Emily Wargo 
1.`<div>`

- a. acts & scenes 
```
//div//head
19 items
``` 

This Xpath gives us all instances that the head element is within the div element. It gives us both the scenes and acts becasue both are wrapped in a `<head>` element, wrapped in a `<div>` element. although, the scene can be found wrapped in the act, making the hierarchy, act is stated first, like `//div/head/div/head`  
 
- b. just acts  
 ```
//body/div/head
5 items 
``` 

Finding just the acts required me to go back and search for the acts' parent elements (`<body>`), in order to distinguish it from other `<div>` elements, that have differnt parents (like `<head>`)
 
-  c. just scenes  
```
//div/div/head
10 items 
```

The first `<div>` element containes both `<head>` and another `<div>` elements. The scenes are listed under `<header>` in the second `<div>` element and therefore 
 - d. senes in Act 2 only   
```
//body/div[2]
3 items 
```

This XPath gives the second act only and the scenes within the second act. 

2.`<stage>`

 - a. stage directions
 ```
 //stage
``` 


This jumps to any stage direction that could be nested inside of any parent element. 
 - b. stage directions within act 3
 
 - c. stage directions inside lines 
 
 - d. stage directions inside speech 
 
 - e. stage directions not inside a spech 
 
 - f. 
 
3.attrbitues

- a. 

- b. `//sp[@who= "Miranda"]` 

