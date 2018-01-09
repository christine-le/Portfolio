---
title: "Learning Python"
categories:
  - Programming
tags:
  - Python
  - Tips
  - Productivity
toc: true
---
As I mentioned in my last post, I recently completed the "Learn Python" module in Code Academy.  This was the first goal for me in learning the basics of Python.  I am now onto my next goal, which is to code various data structures using Python.  This will help me refresh on data structures as well as increase my proficiency in Python.  I will cover some of my data structure exercises in later posts.  

For now, I wanted to cover some of the quirks of Python that stuck out to me, coming most recently from a Javascript and Ruby background.  Python is one of the languages that has been on my list to learn for a couple of years now, especially since my focus has been on data for most of career in the tech field.  It's an in-demand skill for heavy data analysis and manipulation.

As I am learning the fundamentals of Python, there were a few things that gave me a double-take.  I wanted to outline some of those things here in comparison to other languages (primarily Javascript and Ruby, since those are my most recent languages).  Those of you who who are also picking up Python might find this useful.  Aside from minor syntax, this is just a simple list of things that stuck out to me the most in my first week of learning Python.

### Comparisons
|Python                    |Ruby           |Javascript      |Notes           |
|--------------------------|---------------|----------------|----------------|
|True/False                |true/false     |true/false      |Python also uses boolean `True` and `False`.  However, note that these must be capitalized.  This is more of a minor annoyance than anything; I am still getting used to this.  But apparently, all of Python's built-in constants are capitalized.  
|`and` / `or`              |`&&` / `||`    |`&&` / `||`     |Python is a bit more verbose and spells out its logical operator.  Something that I am also still getting used to, as I regularly get syntax errors by using symbols instead. 
|list                      |arrays         |arrays          |Python's built-in sequence data type is a `list`.  This is comparable to arrays in most other languages.  You can, however, use an actual array data type in Python (which is better suited for applying certain operations, such as math operations) with the use of a package, such as NumPy.
|dictionary                |hash           |object          |Nothing fancy here, Python calls its data type to store key/value pairs a _dictionary_ and uses square bracket notation, to access its elements.
|while/else and for/else   |     -----------          |       -----------         |Python has an interesting construct that allows you to apply an if/else-like flow to a while or for loop.  The `else` clause is only met if/when the `while` condition returns false.  Note that the `else` clause would not be executed if a `break` statement is reached at anytime during the loop.
|foo = Foo()               |f = Foo.new()             |f = new Foo()              |Python does not use the `new` keyword when instantiating a class.  With my background in other languages as well, I was surprised that Python does not require the `new` when creating an instance.  After some digging, I realized there is some history behind the `new` keyword and why it was initially implemented in the first place.  I won't go into all the details here, but in a nutshell, this has to do with how objects were created and stored in memory (heap vs stack space).  This convention was carried over from C++.
|`self` parameter in class methods|`this` keyword     |`@` prefix for instance variables         |Interestingly, Python requires the first argument in class methods (including the constructor) to be explicitly defined to reference instances of the class.  Typically, the convention is to define this parameter name as `self`.  This is analogous to the `this` keyword in Javascript or the `@` symbol in Ruby, although the _implementation_ details differs.
|lambda                    |lambda (?)                |anonymous functions (?)    |I am still wrapping my head around lambdas in Python.  From my reading so far, Python lambdas are not the equivalent of anonymous functions in Javascript or lambda.  They do, however, allow for anonymous or unnamed functions to be defined and can only return _expressions_ (no statements).

### Conclusion
The above list is just a simple list I compiled as I go into some deeper learning and programming in Python.  I look forward to diving deeper as I start working on some basic data structures programming and eventually larger data manipulation projects.  Hopefully the above gives helpful insight to those of you learning Python who are coming with a background in other programming languages.  