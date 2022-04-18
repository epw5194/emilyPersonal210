# Class Example 
## getting artists and listing the song titles
### "ebb-xquery5-toHTML.xql"
- global variables are used so information can be avaialble wherever you want to use it 
    - must end file in a semi colon (indicated where the variable's usage ends)
- dont have to return gloabl variable, just type in the global variable 

## What goes inside the FLWOR statement and what doesn't 
- gives repeating elements (where you will put it) - at what part needs to repeat 
    - crank out table (wrap in {})
- multiple songs for each artist (see what they are)
```
for $a at $pos in $artist 
```
- for loop inside a for loop (gear inside another gear)
```
for $t at $p in $titles
```
```
return 
    <tr>
        <td> {$pos}: {$p} </td> 
        <td> {$a}</td>
        <td> {$t}</td>
    </tr>
```
- REMEMBER:
    - semicolons
    - square brackets (for inner for loop inside outer for loop)
    - curly brackets 

### List of Songs 
```
return 
    <tr>
        <td> {$pos} </td> 
        <td> {$a}</td>
        <td>
            <ol>{let $titles := $blues[descendant::artist ! normalize-space() = $a]//metadata/title ! normalize-space() => sort()
    for $t at $p in $titles 
            </ol>
        </td>
    </tr>
```    
- $a is an index variable( key to this to get to each individual thing to pull info from)
- XML gives is cleaner data analysis 