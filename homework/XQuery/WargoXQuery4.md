# XQuery Assignment 4
## Emily Wargo 
I am trying to count the charcters in song titles, order them from longest to shortest and then returning the string of title & their character count in order from longest to shortest (with their position included)
I started with the example from class, and tried to work backwards. 
### 1. What I'm working with 
```
xquery version "3.1";
<html>
    <head><title>Disney Song Title Lengths</title>
    </head>
<body>
    <h1>Order of Disney Songs by the longest to shortest title lengths:</h1>
<ul>
{
let $disneySongs := collection('/db/disneySongs/')//xml
let $titleCount := $disneySongs
let $songLengthsAll :=
                 for $d in $disneySongs
                 let $length := $d//title ! string-length()
                 return $length
let $maxSongLength := $songLengthsAll => max()
for $d at $pos in $disneySongs
    let $title := $d//metadata/title
    let $titleCount := $d//title => count()
    let $songStrings := $d//title ! normalize-space() 
    let $songSL := $songStrings ! string-length()
        
    (: where $songSL = $maxSongLength :)
    (:return concat($title ! string(), 'has string-length of: ', $songSL):)
    return 
      <li>{$title} at position {$pos} has a title length of {$songSL} characters</li>
      (:return $title:)

}
 
  </ul>
  </body>
</html>
```
I soon figured out that it may be easier to just start over on a new document. Copying and pasting some familiar commands. 
### 2. Experimenting with what im working with 
```
xquery version "3.1";
<html>
    <head><title>Disney Song Title Lengths</title>
    </head>
<body>
    <h1>Order of Disney Songs by the longest to shortest title lengths and their position in the collection</h1>
<ul>
{
let $disneySongs := collection('/db/disneySongs/')//xml
let $songLengthsAll :=
                 for $d in $disneySongs
                 let $length := $d//title ! string-length()
                 return $length for $d at $pos in $disneySongs
    let $title := $d//metadata/title
    let $titleCount := $d//title => count()
     
   
return $titleCount
}
        </ul>
    </body>
</html>
```