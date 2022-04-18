# Movie Data  Markdown
## cont. from Dr.B markdown 

After selecting each line so they are tagged with `<movie>`, as the outermost tag, I then found all of the content that were titles of movies and tagged them with `<title>`.  The find and replace steps for both of these tags were documented on the starter markdown  from Dr. B. 

### Date
Next, I tagged all of the date text by using find and replace. The expressions I used were:

```
Find:(/title>)(.+?)\t
Replace:\1<date>\2</date>
```

### Location
Next I used the find and replace to tag all location text items.
```
Find: (/date>)(.+?)\t
Replace: \1<location>\2</location>
```

### Time
Lastly, I wanted to tag for time information by using the find and replace epression window: 

```
Find: (</location>)(.+?)(</movie>)
Replace: \1<time unit="min">\2</time>\3
```
I used question marks within all three expression to avoid greedy matches. 