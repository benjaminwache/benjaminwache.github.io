<h2 id="papers" style="margin: 2px 0px 15px;">Working Papers</h2>

<div class="papers">
  <ol class="bibliography">
    {% for link in site.data.papers.main %}
    <li>
      <div class="pub-row">
        <div class="col-sm-3 abbr" style="position: relative;padding-right: 15px;padding-left: 15px;">
          {% if link.image %}
            <img src="{{ link.image }}" class="teaser img-fluid z-depth-1 custom-image-size" style="object-fit: cover;">
          {% else %}
            <div style="width:300px; height:200px;"></div> 
          {% endif %}
          {% if link.conference_short %} 
            <abbr class="badge">{{ link.conference_short }}</abbr>
          {% endif %}
        </div>
        <div class="col-sm-9" style="position: relative;padding-right: 15px;padding-left: 20px; width: 600px;">
          <div class="title" style="font-weight: bold;">{{ link.title }}</div>
          <div class="author">
            {% assign coauthors = "" %}
            {% assign solo_author = true %}
            {% assign coauthor_count = 0 %}
            {% for author in link.authors %}
              {% if author.name != "Benjamin Wache" %}
                {% assign solo_author = false %}
                {% assign coauthor_count = coauthor_count | plus: 1 %}
                {% if coauthors != "" %}
                  {% if coauthor_count > 2 %}
                    {% assign coauthors = coauthors | append: ", and " %}
                  {% else %}
                    {% assign coauthors = coauthors | append: " and " %}
                  {% endif %}
                {% else %}
                  {% assign coauthors = " (with " %}
                {% endif %}
                {% if author.url %}
                  {% assign coauthors = coauthors | append: "<a href='" | append: author.url | append: "'>" | append: author.name | append: "</a>" %}
                {% else %}
                  {% assign coauthors = coauthors | append: author.name %}
                {% endif %}
              {% endif %}
            {% endfor %}
            {% if solo_author == false %}
              {% assign coauthors = coauthors | append: ")" %}
              {{ coauthors }}
            {% endif %}
          </div>
          <div class="periodical"><em>{{ link.conference }}</em>
            {% if link.date %}
              <div class="date"><em>Updated:</em> {{ link.date | date: "%B %d, %Y" }}</div>
            {% endif %}
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
  </ol>
</div>