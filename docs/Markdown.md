# Markdown

```
It's very easy to make some words **bold** 
and other words *italic* with Markdown. 
You can even [link to Google!](http://google.com)
```
It's very easy to make some words **bold** 
and other words *italic* with Markdown. 
You can even [link to Google!](http://google.com)

***

### Headers
```
# This is an \<h1> tag
## This is an \<h2> tag
###### This is an \<h6> tag
this is normal text
```
# This is an \<h1> tag
## This is an \<h2> tag
###### This is an \<h6> tag
this is normal text

***

### Lists
#### Unordered
```
* Item 1
* Item 2
  * Item 2a
  * Item 2b
```
* Item 1
* Item 2
  * Item 2a
  * Item 2b
#### Ordered
```
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
```
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b

***

### Images
```
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)

***

### Links
```
http://github.com - automatic!
[GitHub](http://github.com)
```
http://github.com - automatic!
[GitHub](http://github.com)

***

### Blockquotes
```
As Kanye West said:
> We're living the future so
> the present is our past.
```
As Kanye West said:
> We're living the future so
> the present is our past.

***

### Inline code
```
I think you should use an
`<addr>` element here instead.
```
I think you should use an
`<addr>` element here instead.

***

## Github Markdown Features

### Syntax Highlighting

```
```python
def foo():
    if not bar:
        return True
'''
```
###### (but that last line is actually ```)
```python
def foo():
    if not bar:
        return True
```

### Tables
Tables are super super handy!!
```
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Data | More Data
```
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Data | More Data

### Task Lists
```
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
```
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item

### Strikethrough
Strikethrough
Any word wrapped with two tildes (like `~~this~~`) will appear crossed out.
```
I want to go ~~home~~ to the park.
```
I want to go ~~home~~ to the park.

***

## Useful Stuff I've learned:

### Link to another header on your page
```
You should look at the section on [lists](#lists). 
It is super helpful. 
Or just start over from the [top](#markdown).
```
You should look at the section on [lists](#lists).
It is super helpful. 
Or just start over from the [top](#markdown).

This works for any header size. Only use one # when referencing it regardless of header size.

When using this, remember to keep the (#link) part lowercase and separate words using - instead of a space:

```
[Right here](#useful-stuff-i've-learned)
```
[Right here](#useful-stuff-i've-learned)

***

### Images
Images are similar to links to other pages, but with an `!` in front.

```
![FunTimes](https://github.com/ryancj14/LinkToTheNow/wiki/LifeImages/LakePowell.jpeg)
```
![FunTimes](https://github.com/ryancj14/LinkToTheNow/wiki/LifeImages/LakePowell.jpeg)

***

To work with Markdown from within VS Code, download the `Github Markdown Preview` Extension. 

Then you can click the `Open Preview to the Side` Icon on the top right of the editing window to open the preview of the Markdown you have open.

----------------------------------
Initially created by Ryan Johnson, June 2020.