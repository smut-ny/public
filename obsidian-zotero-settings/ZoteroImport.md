---
BookTitle: "{{ bookTitle }}"
Title: "{{ title }}"
Author: "{{ authors }}"
Bibliography: "{{ bibliography }}"
Date: "{{ date | format("YYYY-MM-DD")}}"
desktopLink: "{{ desktopURI }}"
tags:
  - zotero
 {% for tag in tags %} - {{tag.tag}}
 {% endfor %}
---


### Custom obsidian notes
![[notes_{{citekey}}]]

### Zotero notes and annotations

{% for annotation in annotations %}
{% if annotation.annotatedText %}
<div style="width: 100%; height: 18px; background-color: {{annotation.color}};"></div>
>📌 {{annotation.annotatedText}} 

[Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})
{% endif %}
{% if annotation.comment %}
>✏️ {{annotation.comment}} 

[Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})
{% endif %}
{% endfor %}