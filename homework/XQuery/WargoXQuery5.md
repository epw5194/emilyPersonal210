# Query Assignment 5
## Emily Wargo 

### 1. Start 
```
xquery version "3.1";
let $blues := collection('/db/blues')
return $blues
```
- 1087 results


### 2. Gathering all titles 
```
xquery version "3.1";
let $blues := collection('/db/blues')
let $title := $blues//metadata/title ! normalize-space() =>distinct-values() 
    for $b at $pos in $blues 
    let $titleCount := $blues//metadata/title
return $titleCount
```
- 1180242 results 

### 3. Identifying Artists 
```
xquery version "3.1";
let $blues := collection('/db/blues')
let $title := $blues//metadata/title ! normalize-space() =>distinct-values() 
    for $b at $pos in $blues 
    let $titleCount := $blues//metadata/title
let $artist := $blues//metadata/artist ! normalize-space() =>distinct-values() 
return $artist
```
- 38045 results 

### 4. Counting the characters in titles 

### 5. Returning the string/concat of titles, character count and author associated 

### 6.Sort Titles alphabetical

### 7. HTML

<!--- i had very high hopes for learning more Xquery with this assignment it is definitely taking me more time than i had thought. this week i have not be able to allocate proper time. this is what i have and i will turn in  completed version ovr the weekend. this is all so new and it takes some adjusting  --->
