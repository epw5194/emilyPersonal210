# Maltese XML Texst
## Emily Wargo 
 I first wanted to ensure all new line spacing was done with only two new lines, to keep the document consistent. searched for all new instances where there were 2 or more new lines, and replaced it with just two new lines. 
```
Find:\n{2,}
Replace:\n\n
```
* with dot matches all ON so it could grab all content 
 
 ### 1. Testing & following regular expression
```
Find ^(.+?)(\n\n)
Replace <sp>\1</sp>\2
```
* with dot matches all ON so it could grab all content 

#### a. Dot Matches all explanation 
#### b. what \1, \2 represent in the find & replace
#### c. decide best option of Find and Replace

 ### 2. Stage Directions 
 ### 3. Speakers 
 ### 4 Root & Formatting 
 ### 5  Stage Directions Inside SP tags 
