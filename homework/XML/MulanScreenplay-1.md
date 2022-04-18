# Regex Assignment 4
## Mulan Screenplay-Emily Wargo 
### to start
First, I searched for all `&`, `<`, and `>` in the text to prevent any XML errors. 

### new line spacing 
I first wanted to ensure all new line spacing was done with only two new lines, to keep the document consistent. searched for all new instances where there were 2 or more new lines, and replaced it with just two new lines. 
```
Find:\n{2,}
Replace:\n\n
```
* with dot matches all ON so it could grab everything 

### speeches (sp)
I started from the outside-in. I wanted to ensure that all lines were wrapped in an `<sp>` tag:
```
Find:(.+?)(\n{2})
Replace:<sp>\1</sp>\2
```
* with dot matches all ON so it could grab everything

### stage
Next, I wanted to find left and right brackets and all of the content spanning in between. 
I did this with the "dot matches all" turned on to be able to indentify the content between the brackets that span over new lines.
```
Find:\[(.+?)\]
Replace:<stage>\1</stage> 
```
* with dot matches all ON so it could grab everything

### stage & sp
Then, I filtered out  prargraphs that only included stage notes, so they didnt include the speaking tag wrap around them
```
Find:<sp><stage>(.+?)</stage></sp>
Replace:<stage>\1</stage>
```

### speaker 
Next, I went to find my characters by using a `:`
```
Find:(<sp>)(.+?):
Replace:\1<speaker>\2</speaker>
```
* with dot matches all OFF so it didnt grab every instance in between tags 
