# Progress

{% assign categories = site.data.challenges | group_by:"category" %}
{% for category in categories %}
## {{ category.name }}

<ol start="{{category.items[0].id}}">
{% for challenge in category.items %}
<li>
{% assign books = include.books %}
{% assign matchingBooks = books | where_exp:"item","item.Ids contains challenge.id" %}
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
  {% assign completedBooks = books | where:"Completed","true" %}
  
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