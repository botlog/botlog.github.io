---
layout: page
title: My website
subtitle: This is where I will tell my friends way too much about me
use-site-title: true
---

<div class="posts-list">
<div class="container-fluid" style="margin: 0% 5% 0% 5%">
<div class="col-sm-12 col-sm-offset-0">

  {% for post in paginator.posts %}
  <article class="post-preview">
    <a href="{{ post.url | relative_url }}">
	  <h2 class="post-title">{{ post.title }}</h2>
    </a>

    <p class="post-meta">
      Posted on {{ post.date | date: "%B %-d, %Y" }}
    </p>
    <div class="post-entry-container">
      <div class="post-entry">
        {{ post.excerpt | strip_html | xml_escape | truncatewords: site.excerpt_length }}
        {% assign excerpt_word_count = post.excerpt | number_of_words %}
        {% if post.content != post.excerpt or excerpt_word_count > site.excerpt_length %}
          <a href="{{ post.url | relative_url }}" class="post-read-more">[Read&nbsp;More]</a>
        {% endif %}
      </div>
    </div>
   </article>
  {% endfor %}
</div>
</div>
</div>


{% if paginator.total_pages > 1 %}
  {% if paginator.previous_page %}

        <div class="form-row text-center" style="margin-bottom: 10px;">
        <a href="{{ paginator.previous_page_path | relative_url }}" class="btn btn-primary btn-sm">[Read&nbsp;More]</a>
        </div>


    <a href="{{ paginator.previous_page_path | relative_url }}">&larr;Newer</a>
    <a href="{{ post.url | relative_url }}" class="post-read-more">[Read&nbsp;More]</a>
  {% endif %}
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | relative_url }}">Older&rarr;</a>
    <a href="{{ paginator.next_page_path | relative_url }}" class="post-read-more">[Read&nbsp;More]</a>
  {% endif %}
{% endif %}


{% if paginator.total_pages > 1 %}
<ul class="pager main-pager">
  {% if paginator.previous_page %}
  <li class="previous1">
    <a href="{{ paginator.previous_page_path | relative_url }}">&larr;Newer</a>
    <a href="{{ post.url | relative_url }}" class="post-read-more">[Read&nbsp;More]</a>
  </li>
  {% endif %}
  {% if paginator.next_page %}
  <li class="next1">
    <a href="{{ paginator.next_page_path | relative_url }}">Older&rarr;</a>
    <a href="{{ paginator.next_page_path | relative_url }}" class="post-read-more">[Read&nbsp;More]</a>
  </li>
  {% endif %}
</ul>
{% endif %}
