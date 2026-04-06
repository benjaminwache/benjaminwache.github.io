<h2 id="publications" style="margin: 2px 0px 15px;">Publications</h2>

<div class="publications">
  <ol class="bibliography">
    {% for link in site.data.publications.main %}
    <li>
      <div class="pub-row">
        <div class="col-sm-3 pub-row-image">
          {% if link.image %}
            <img src="{{ link.image }}" class="teaser img-fluid z-depth-1 custom-image-size" style="object-fit: cover;">
          {% else %}
            <div style="width:300px;"></div>
          {% endif %}
          {% if link.conference_short %}
            <abbr class="badge">{{ link.conference_short }}</abbr>
          {% endif %}
        </div>
        <div class="col-sm-9 pub-row-text">
          <div class="title" style="font-weight: bold;">{{ link.title }}</div>
          <div class="author">
            {% assign coauthors = "" %}
            {% assign coauthor_count = 0 %}
            {% assign total_coauthors = 0 %}
            {% for author in link.authors %}
              {% if author.name != "Benjamin Wache" %}
                {% assign total_coauthors = total_coauthors | plus: 1 %}
              {% endif %}
            {% endfor %}
            {% for author in link.authors %}
              {% if author.name != "Benjamin Wache" %}
                {% assign coauthor_count = coauthor_count | plus: 1 %}
                {% if coauthors != "" %}
                  {% if coauthor_count == total_coauthors %}
                    {% assign coauthors = coauthors | append: ", and " %}
                  {% else %}
                    {% assign coauthors = coauthors | append: ", " %}
                  {% endif %}
                {% else %}
                  {% assign coauthors = "with " %}
                {% endif %}
                {% if author.url %}
                  {% assign coauthors = coauthors | append: "<a href='" | append: author.url | append: "'>" | append: author.name | append: "</a>" %}
                {% else %}
                  {% assign coauthors = coauthors | append: author.name %}
                {% endif %}
              {% endif %}
            {% endfor %}
            {% if total_coauthors > 0 %}
              {{ coauthors }}
            {% endif %}
          </div>
          <div class="periodical"><em>{{ link.conference }}</em>
          </div>
          <div class="links">
            {% if link.pdf %}
              <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">PDF</a>
            {% endif %}
            {% if link.code %}
              <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Code</a>
            {% endif %}
            {% if link.page %}
              <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Paper</a>
            {% endif %}
            {% if link.bibtex %}
              <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">BibTex</a>
            {% endif %}
            {% if link.abstract %}
              <a class="btn btn-sm z-depth-0" role="button" style="font-size:12px; cursor:pointer;" onclick="this.parentNode.parentNode.querySelector('.abstract').classList.toggle('open')">Abstract</a>
            {% endif %}
            {% if link.notes %}
              <strong> <i style="color:#e74d3c">{{ link.notes }}</i></strong>
            {% endif %}
            {% if link.others %}
              {{ link.others }}
            {% endif %}
          </div>
          {% if link.abstract %}
          <div class="abstract hidden" style="margin-top: 10px; font-size: 14px; text-align: justify;">
            <p>{{ link.abstract }}</p>
          </div>
          {% endif %}
        </div>
      </div>
    </li>
    <br>
    {% endfor %}
  </ol>
</div>
