<h2 id="papers" style="margin: 2px 0px -15px;">Working Papers</h2>

<div class="papers">
<ol class="bibliography">

{% for link in site.data.papers.main %}

<li>
<div class="pub-row">
  <div class="col-sm-3 abbr" style="position: relative;padding-right: 15px;padding-left: 15px;">
    {% if link.image %}
      <img src="{{ link.image }}" class="teaser img-fluid z-depth-1" style="width:300px; object-fit: cover;">
    {% else %}
      <div style="width:300px;"></div>
    {% endif %}
    {% if link.conference_short %} 
      <abbr class="badge">{{ link.conference_short }}</abbr>
    {% endif %}
  </div>
  <div class="col-sm-9" style="position: relative;padding-right: 15px;padding-left: 20px;">
      <div class="title" style="font-weight: bold;">{{ link.title }}</div>
      <div class="author">
        {% assign only_benjamin = true %}
        {% for author in link.authors %}
          {% if author.name != "Benjamin Wache" %}
            {% assign only_benjamin = false %}
          {% endif %}
        {% endfor %}        
        {% if only_benjamin == false %}
          (with 
          {% for author in link.authors %}
            {% if author.name != "Benjamin Wache" %}
              {% if author.url %}
                <a href="{{ author.url }}">{{ author.name }}</a>
              {% else %}
                {{ author.name }}
              {% endif %}
              {% if forloop.last == false %} 
                {% if forloop.index == forloop.length | minus: 1 %} 
                  and 
                {% else %}
                  , 
                {% endif %}
              {% endif %}
            {% endif %}
          {% endfor %}
          )
        {% endif %}
      </div>
      <div class="periodical"><em>{{ link.conference }}</em>
      <div class="date">{{ link.date | date: "%B %d, %Y" }}</div>
      </div>
    <div class="links">
      {% if link.pdf %} 
      <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">PDF</a>
      {% endif %}
      {% if link.code %} 
      <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Code</a>
      {% endif %}
      {% if link.page %} 
      <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Project Page</a>
      {% endif %}
      {% if link.bibtex %} 
      <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">BibTex</a>
      {% endif %}
      {% if link.notes %} 
      <strong> <i style="color:#e74d3c">{{ link.notes }}</i></strong>
      {% endif %}
      {% if link.others %} 
      {{ link.others }}
      {% endif %}
    </div>
  </div>
</div>
</li>

<br>

{% endfor %}

</ol>
</div>

