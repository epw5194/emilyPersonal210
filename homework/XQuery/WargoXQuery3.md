# XQuery 3
## Emily Wargo 

### Querying the database so we can see each song 
```
xquery version "3.1";
    let $disneySongs := collection('/db/disneySongs/')
        for $d in $disneySongs
    return $d
```
- non-name spaced xml 

### 1. FLWOR Statement for Song Titles 
```
let $disneySongs := collection('/db/disneySongs/')//xml
  for $d in $disneySongs
let $title := $disneySongs//metadata/title
return $title
``` 

### 2.Count of lines in each song 
```
let $disneySongs := collection('/db/disneySongs/')//xml
  for $d in $disneySongs
let $title := $disneySongs//metadata/title
let $lineCount := $d//ln => count()
return $lineCount 
```
**93 items returned**
### 3. Measure length of song by measuring how many lines it has 
- character count
```
xquery version "3.1";
let $disneySongs := collection('/db/disneySongs/')//xml
let $songCount := $disneySongs 
  for $d in $disneySongs
let $title := $d//metadata/title
let $lineCount := $d//ln => count()
let $songStrings := $d//song ! normalize-space()
let $songSL := $songStrings ! string-length()
return $songSL
```
- string lengths grabs eveyr character and counts it (can use as a comparison metric)
- simple map (!) takes a thing one at a time and evaluate it
- get result for each turn of the "for" loop (for each song in songs, return me this inofrmation)
  - cardinality: error made when simple map takes ech node and counts it, usually defaults to one (having a million ones)
  - arrow operator takes a sequence and gives a result for each set of things 

### 4. Order by to organize in descending order from highest to lowest
```
let $disneySongs := collection('/db/disneySongs/')//xml
let $songCount := $disneySongs 
  for $d in $disneySongs
let $title := $d//metadata/title
let $lineCount := $d//ln => count()
let $songStrings := $d//song ! normalize-space()
let $songSL := $songStrings ! string-length()
order by $songSL descending
return $songSL
```
- ascending is default, so descending will order longest to shortest

### 5. Bundle each song title with its word count
```
  $countTitle := $title => count()
    return concat($title, :, $countTitle)
```
### 6. Longest and Shortest only 
- result of 93 seperate items 
- go through whole sequence and get me them all: rrow operator becasue i have a sequence of 93 items (all items need to be read and calculated which is the biggest and which is the smallest)
    - if one doesnt work, try the other (**!** or **=>**)
```
```

### 7. "For" loop for title & other information
- what song titles are associated with min and max song lengths 
- care about the title, not length/count 
    - use "where"
    - return the "$title" function 
- output together, conact together the title & the string/song length

#### 7a. Return HTML
to make an HTML file, wrap XQUERY in curly braces. write HTML file around it and add "html" tags  
