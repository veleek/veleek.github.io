---
layout: default
title: Reading Challenge 2017
description: Tracking my progress against the 2017 Reading Challenge
done: Nope
---

# What Challenge
I started reading a bunch more towards the end of 2016 and have been 'forcing' myself to take the bus to work more often and using that time to read a bit more (instead of wasting time with Reddit or random mobile games).  I stumbled across [this reading challenge on Reddit](https://www.reddit.com/r/books/comments/5iqd7j/a_2017_reading_challenge_to_keep_you_well_rounded/) and thought that it would be fun to participate in.

I'm just doing Easy Mode (each title read can check off any number of items), but going to try and back-fill after I finish to minimize the number of titles that fill more than one category.

# Progress

{% assign categories = site.data.challenges | group_by:"category" %}
{% for category in categories %}
## {{ category.name }}

<ol start="{{category.items[0].id}}">
{% for challenge in category.items %}
<li>
{% assign matchingBooks = site.data.books | where_exp:"item","item.Ids contains challenge.id" %}
{% assign s = matchingBooks | size > 0 %}

{% if matchingBooks.size > 0 %}
<!--{% increment complete %}-->
<input type="checkbox" checked="" disabled=""> {{ challenge.name }}
{% else %}
<input type="checkbox" disabled=""> {{ challenge.name }}
{% endif %}

<ul>
{% for matchingBook in matchingBooks %}
  <li><a href="https://www.goodreads.com/book/show/{{matchingBook.GoodReadsId}}">{{matchingBook.Title}}</a></li>
{% endfor %}
{% if challenge.id == 52 %}
  {% assign letters= "A B C D E F G H I J K L M N O P Q R S T U V W X Y Z" | split:" " %}
  {% assign completedBooks = site.data.books | where:"Completed","true" %}
  
  <li>
  {% for letter in letters %}
    {% assign hasLetter = false %}
    {% for book in completedBooks %}
      {% assign title = book.Title | upcase %}
      {% if title contains letter %}
        {% assign hasLetter = true %}  
        {% break %}
      {% endif %}
    {% endfor %}
    {%if hasLetter%}<span style="color:lightgray">{% endif %}{{ letter }}{% if hasLetter %}</span>{%endif %}
  {% endfor %}
  </li>
{% endif %}
</ul>
</li>
{% endfor %}
</ol>
{% endfor %}



Completed {{ complete }} / 52 challenges.