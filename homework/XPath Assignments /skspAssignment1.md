# XQuery Assignment 1
## Emily Wargo 

Startig with 
```
xquery version "3.1";
declare default element namespace "http://www.tei-c.org/ns/1.0";
(:  :doc('/db/apps/shakespeare/data/tem.xml')//body/div/div :)
collection('/db/apps/shakespeare/data/')
```
### 1. Main titles 
XPath
```
collection('/db/apps/shakespeare/data/')//titleStmt/title
```
**42 results**

### 2. Just the text of titles 
```
collection('/db/apps/shakespeare/data/')//titleStmt/title/text()
```
**42 results**
### 3.Isolate TEI element
```
collection('/db/apps/shakespeare/data/')/TEI
```
**???**
### 4.Locate plays with "Flastaff" as speaker 
boolean logic- looking for conditions
- predicates test boolean conditions


```
collection('/db/apps/shakespeare/data/')//TEI//sp[speaker="Falstaff"]
```
**473 instances**
### 5. Titles of the 4 plays with "Falstaff" as speaker
think of the predicate that answers true
- cannot lead predicate with two forward slashes 
```
collection('/db/apps/shakespeare/data/')//TEI[descendant::sp[speaker="Falstaff"]]//titleStmt/title
```
**or** (but less preferred)
```
collection('/db/apps/shakespeare/data/')//TEI[.//sp[speaker="Falstaff"]]//titleStmt/title
```
### 6. Changes with "text()" and "string()"
text gives us just the text 
```
collection('/db/apps/shakespeare/data/')//TEI[descendant::sp[speaker="Falstaff"]]//titleStmt/title/text()
```
string gives it to us with parenthesis
- it is a function: digging through descendent elements, taking text nodes, and combining them together 
- data is very similar (mostly used for numbers)
```
collection('/db/apps/shakespeare/data/')///TEI[descendant::sp[speaker="Falstaff"]]//titleStmt/title/string()
```
### 7. All speeches written by "Falstaff"
can use count
- meant to take only a single thing  (takes arrow)

```
collection('/db/apps/shakespeare/data/')//TEI//sp[speaker="Falstaff"] => count()
```
"!" makes a calculation over whole sequence (simple map): designed for taking each one at a time & using them 
- visiting each node (takes exclamation point)

```
collection('/db/apps/shakespeare/data/')//TEI//sp[speaker="Falstaff"] ! string()
```
### 8. FLWOR statement or XPath Expression 
FLOWR= For, Let, Order by, Where, Return 
```
let $shakes:= collection('/db/apps/shakespeare/data/')
return $shakes
```
**43 items**

### 9. How often "Falstaff" speaks in each play using XQuery FLOWR Statement  
```
let $shakes:= collection('/db/apps/shakespeare/data/')
let $speeches:= $shakes//sp
let $falstaffs := $speeches [speaker ="Falstaff"]
let $countFals := $falstaffs => count()
let $falPlays := $shakes//TEI[descendant::sp[speaker="Falstaff"]]
return $falPlays
```

4 results of counr per play (copy from zoom recording)
```

```

Strign with count of speeches and title of speech
```

```

## File name:"ebb-xqueryFLOWR1.xql" in 2022 class examples 