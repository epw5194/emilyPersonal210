# Maltese XML Texst
## Emily Wargo 
 I first wanted to ensure all new line spacing was done with only two new lines, to keep the document consistent. I searched for all new instances where there were 2 or more new lines, and replaced it with just two new lines. 
```
Find:\n{2,}
Replace:\n\n
```
* with dot matches all ON so it could grab all content 
 
 ### 1. Testing & following regular expression

#### a. Dot Matches all explanation
When Dot Matches all is on, using the period in the your find expression will match all characters, symbols, spaces, and eveything in between. Using this is very powerful becasue the fin expression output can become extremely greedy and will not know when to stop matching everything, until your expression gives it a place to stop. 
#### b. what \1, \2 represent in the find & replace
`\1` and `\2` represent capturing groups. this means that when an expression is wrapped in parenthesis, and these symbols are presented in the Replace expression line, whatever is within the parenthesis in the FInd expression, will be saved along with the output from the Replace function. 
#### c. Find and Replace for speeches tags 
First, I wanted to wrap all lines and groups of lines by `<sp></sp>` tags.The groups of lines should be speerated by no more than two newlines (`\n\n`)
```
Find:^(.+?)(\n\n)
Replace:<sp>\1</sp>\2
```
* with dot matches all ON so it could grab all content 

### 2. Stage Directions 
Each stage diretion was wrapped in parentheis, so that is what I searched for. 
```
Find:\((.+?)\)
Replace:<stage>\1</stage>
```
* with dot matches all ON so it could grab all content 

Then, I wanted to remove the `<sp></sp>` tags around stand alone `<stage></stage>` tagged lines.
```
Find:<sp><stage>(.+?)</stage></sp>
Replace:<stage>\1</stage>
```
* with dot matches all ON so it could grab all content

### 3. Speakers
Every speaker has a colon after their name. Following that pattern, I wanted to search all characters up until that point. 
```
Find:(<sp>)(.+?):
Replace:\1<speaker>\2</speaker>
```
* with dot matches all NOT ON so it did not grab all instances before the use of the colon.
If i were to use dot matches all, it highlights content from a start `<sp>` tag, through a paragraph of text, and into the next instance it sees a colon. This is not what we want, and only want the `.` or dots selected that are actually the speakers name. 

### 4 Root & Formatting 
The last step was to save the .txt file as an .xml file. Once this was done, I had to add start and end `<xml></xml> ` tags to the document, so that there was a root tag. 
### 5  Stage Directions Inside SP tags 
This step was completed above in step 2!
