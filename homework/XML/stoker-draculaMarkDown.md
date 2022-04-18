# Regex Assignment 3
## Stoker's Dracula .txt file
### Emily Wargo

* First, I looked for all ampersand and bracket elements already in the text file so they don’t affect the XML code:  
```
Find:&
Replace:&amp;
```
I also looked for `<` and `>` brackets to ensure they care replaced for when I later use tags, buut, there were none. 

* Then, I wanted to divide the text file into paragraphs by using a `<p>` tag: 
```
Find:^.+?$
Replace:<p>\0</p>
```
* Next, I wanted to work from the inside out, so I started with finding chapter headers and tag them with `<heading>`:
```
Find:<p>\n?(CHAPTER.+?)</p>
Replace:<heading> \1</heading>
```
* I then wanted to wrap the chapters in their own `<chapter>` tag and decided to change the structure with clopen `<chapter>` tags 
```
Find:(<heading>)
Replace:
</chapter>
<chapter>\1
```
After this step, I saved my .txt document progress as a .xml document and switched over to it to use for the rest of the steps. 
* Before "pretty printing" the XML document, I wanted to be able to find all the text's quotes, so that they were in th same line, and tag them with `<q>` tags:
```
Find:"(.+?)"
Replace:<q>\1</q>
```
At this point, I "pretty printed: my document.
* Next, I wanted to tag the dates within each chapter's first paragraph. I chose to start with the number `<day>` of the date becasue it was easily indentiifable, being considered a digit:
```
Find:(<p>)(\d+\s)
Replace:\1<day>\2</day>
```
* The next element of the chapter's date to find is the month:
```
Find:(</day>)(\w+)[.]
Replace:\1<month>\2</month>
```
* Now that I have the date's `<day>` and `<month>` tags, I want to group them to be tagged under one final tag `<date>`:
```
Find:<day>.+?</month>
Replace:<date>\0</date>