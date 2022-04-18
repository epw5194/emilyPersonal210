# Regex Assignment 4
## Mulan Screenplay
### Emily Wargo 
* First, I searched for all `&`, `<`, and `>` in the text to prevent any XML errors. 
* Next, I started from the outside-in. I wanted to ensure that all lines were wrapped in an `<sp>` tag:
```
Find:.+?$
Replace:<sp>\0</sp>
```
* Then, I looked for all left brackets:
```
Find (<sp>)(.*)[\[]
Replace\1\2<stage>
```
* Then, right brackets:
```
Find [\]](.*)(</sp>)
Replace</stage>\1\2
```
I did this becasue some stage notes carry to the next line. So, if i identified them together, it wouldnt be able to recognie that al of the content in between then, belong ot them.
However, the brackets did not come out to equal value items (there were more right brackets than left).
* Next, I went to find my characters, but saw that my `<sp></sp>` and `<stage></stage>` tags were tangled. 
```
Find: <stage>.+?</stage> only 406 items 
```
I think that it was only able to recognize about half of the `<stage></stage>` tags becasue it was tabgled with the `<sp></sp>` tags. 


* Then, I filtered out only stage prargraphs, so they didnt include the speaking tag 
```
Find:<sp><stage>(.+?)</stage></sp>
Replace:<stage>\1</stage>
```
This is where I started over to replicate what you had shared in class with us. Everything I did was exactly according to the instractions shared on GitHub, in terms of Find and Replace. 
This  
* For this last step, I have been getting really stuck on the proper find command and thi was the best i could come up with:
```
Find:(<sp>)(.+?)([^<]):
Replace:\1<speaker>\2</speaker>\3
```
With this search & replace, the `<stage>` tags are still placed within the `<speaker>`tags. 