Title: Python and Regex  
Date: 2016-10-11 11:30   
Category: Coding  
Tags: tutorial, python, regex  
Slug: python_and_regex   
Authors: Ned  
Summary: 


Python and regular expressions play very nicely together - indeed the `re` package ships with the Python Standard Library. I find the documentation, however, to be more than a little dense, and it always takes me an age to wade through and find what I want in there. 

This post is intended to be a quick reference for typical use cases. It will probably be updated as I come across more "standard" jobs.

## Finding All Occurrences of a Pattern

This would find all the capital letters:

```python
string = 'Why hello fine Sir, don\'t You look Lovely today!'
pattern = re.compile('[A-Z]') 
results = re.findall(pattern, string)
```
Printing the results then returns:

```python
['W', 'S', 'Y', 'L']
```
## Replacing All Occurrences of a Pattern

This would find and replace all repeated letters:

```python
string = u'aa b c dd'
pattern = re.compile(ur'(\w)(\1)', re.UNICODE)
match = pattern.search(string)
while match:
    string = string.replace(match.group(0), 'HERE')
    match = pattern.search(string)
```

String then contains:

```python
u'HERE b c HERE'
```

Alternatively you can use `re.sub` or `re.subn`:

```python
substituted = re.sub(pattern, 'HERE', string)
```
A couple of things to note here:

* When using unicode strings (generally a good idea), you need to remember the `re.UNICODE` flag.
* It's also a good idea to use raw strings when comiling the expression (so that backslashes aren't interpreted as escape characters).