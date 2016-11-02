Title: Common Regex Patterns  
Date: 2016-10-23 09:10   
Category: Coding  
Tags: tutorial, regex  
Slug: regex_patterns  
Authors: Ned  
Summary: 


Here are some common regular expression patterns that I seem to use regularly, but can never remember how they're written: 

## Lookbehinds and Lookaheads

Lookbehind (where `xyz` is the pattern you're looking for):

`(?<=xyz)this_will_be_matched`