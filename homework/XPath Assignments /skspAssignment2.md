# X Query Assignment 2
## Emily Wargo 

START WITH:
```
xquery version "3.1";
declare default element namespace "http://www.tei-c.org/ns/1.0";
(:  :doc('/db/apps/shakespeare/data/tem.xml')//body/div/div :)
collection('/db/apps/shakespeare/data/')
```

### 1. 7 Plays with Distincy speakers 
#### a. Start a FLWOR Expression
#### b. Define speaker Variable & count results
```
let $plays := collection('/db/apps/shakespeare/data/')
let $speeches := $plays//sp
let $speaker := $speeches//speaker
let $countSpeaker := $speaker => count() 
return $countSpeaker
```
**31054** results
- the colon is used t escape an equal sign when assigning a variable and using Xpath


#### c. Distinct Values 
```
let $plays := collection('/db/apps/shakespeare/data/')
let $speeches := $plays//sp
let $speaker := $speeches//speaker
let $countSpeaker := $speaker => distinct-values() 
return $countSpeaker
```
Distinct values gives no duplicates of the speaker's names. I want to say it did a perfect job and I did not see any mistakes when scrolling thorugh. But, Im sure there is another function we have to add to make sure it is working properly. 
- removes duplicate values 

#### d. Count Distinct Values 
```
let $plays := collection('/db/apps/shakespeare/data/')
let $speeches := $plays//sp
let $speaker := $speeches//speaker
let $distinctSpeaker := $speaker => distinct-values() 
let $countSpeaker := $distinctSpeaker => count()
return $countSpeaker
```
**966** results 

This count shows that the distinct values did work! 

#### e. Count of more than 50 speakers 
##### a. FOR Loops
```
let $plays := collection('/db/apps/shakespeare/data/')
let $speeches := $plays//sp
let $speaker := $speeches//speaker
let $distinctSpeaker := $speaker => distinct-values() 
let $countSpeaker := $distinctSpeaker => count()

for $p in $plays
for $p at $pos in $plays 
```
- assigning new variable, 
break this whole series of things into 42 differnt pieces, for every play we will work with them one by one
- `$pos`: taking the plays one at a time, and assigning htem numbers
- the syntax around p, defines p

##### b. Number of Speakers in each play 
```
let $plays := collection('/db/apps/shakespeare/data/')
let $speeches := $plays//sp
let $speaker := $speeches//speaker
let $distinctSpeaker := $speaker => distinct-values() 
let $countSpeaker := $distinctSpeaker => count()

for $p at $pos in $plays 
let $countSpeaker := $p//speaker => distinct-values() => count()
return $countSpeaker
```
**43** results 

##### c. Title of Each play 
```
let $plays := collection('/db/apps/shakespeare/data/')
let $speeches := $plays//sp
let $speaker := $speeches//speaker
let $distinctSpeaker := $speaker => distinct-values() 
let $countSpeaker := $distinctSpeaker => count()

for $p at $pos in $plays 
    let $countSpeaker := $p//speaker => distinct-values() => count()
    let $title := $p//titleStmt/title ! string()
    return $title
```    

##### d. Put titles of plays together (text strings-CONCATENATE)
```
for $p at $pos in $plays 
    let $countSpeaker := $p//speaker => distinct-values() => count()
    let $title := $p//titleStmt/title ! string()
    return concat($title, ":", $countSpeaker)
```
##### e. Count of plays with more than 50 speakers
```
for $p at $pos in $plays 
    let $countSpeaker := $p//speaker => distinct-values() => count()
    let $title := $p//titleStmt/title ! string()
    where $countSpeaker >50
    return concat($title, ":", $countSpeaker)
```    
#### Other Steps Demonstrated in Class 
##### String Functions 
- Tokenize: takes 2 arguments (1st- needle in haystack) 
- self, you can use dot 
- (2nd: character you want to cut it on, cutting character) 
```
! tokenize (.,'/')[last()]
```

