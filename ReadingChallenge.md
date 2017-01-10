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
{% for challenge in category.items %}
{{challenge.id}}\. {{ challenge.name }}

{% assign matchingBooks = site.data.books | where_exp:"item","item.Ids contains challenge.id" %}
{% for matchingBook in matchingBooks %}
<ul>
  <li><a href="https://www.goodreads.com/book/show/{{matchingBook.GoodReadsId}}">{{matchingBook.Title}}</a></li>
</ul>
{% endfor %}

{% assign s = matchingBooks | size %}
{% if matchingBooks.size > 0 %}
<!--{% increment complete %}-->
{% endif %}

{% endfor %}
{% endfor %}

Completed {{ complete }} / 52 challenges.