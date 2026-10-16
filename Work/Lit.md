---
tags:
  - reference/paper
  - status/to-read
title: "{{title}}"
authors:
  {%- for author in creators %}
  - "{{author.firstName}} {{author.lastName}}"
  {%- endfor %}
year: {{date | format("YYYY")}}
journal: "{{publicationTitle}}"
doi: "{{DOI}}"
citekey: "{{citekey}}"
pdf: "{% if pdfZoteroUrl %}{{pdfZoteroUrl}}{% else %}{{selectItemZoteroUrl}}{% endif %}"
---

# {{title}}

> [!abstract] Citation
> {{bibliography}}

---

## 💡 Summary & Core Argument
*A 2–3 sentence high-level overview of the work's central thesis or primary contribution.*

## 💭 Critical Evaluation
- **Strengths:**
  - 
- **Limitations:**
  - 

## 🔗 Relevance & Application
- **How it relates to my research:**
  - 
## 📝 Highlights & Annotations

### 🟢 Questions
{% for annotation in annotations -%}
{% if annotation.color == "#5fb236" or annotation.colorCategory == "green" %}
> "{{annotation.annotatedText}}" (p. {{annotation.pageLabel}})
{% if annotation.comment %}  * Comment: {{annotation.comment}}{% endif %}
{% endif %}
{%- endfor %}

### 🔵 Conceptual Understanding
{% for annotation in annotations -%}
{% if annotation.color == "#2ea8e5" or annotation.colorCategory == "blue" %}
> "{{annotation.annotatedText}}" (p. {{annotation.pageLabel}})
{% if annotation.comment %}  * Comment: {{annotation.comment}}{% endif %}
{% endif %}
{%- endfor %}

### 🟡 Key Points
{% for annotation in annotations -%}
{% if annotation.color == "#ffd400" or annotation.colorCategory == "yellow" or not annotation.color %}
> "{{annotation.annotatedText}}" (p. {{annotation.pageLabel}})
{% if annotation.comment %}  * Comment: {{annotation.comment}}{% endif %}
{% endif %}
{%- endfor %}

### 🔴 Methodology
{% for annotation in annotations -%}
{% if annotation.color == "#ff6666" or annotation.colorCategory == "red" %}
> "{{annotation.annotatedText}}" (p. {{annotation.pageLabel}})
{% if annotation.comment %}  * Comment: {{annotation.comment}}{% endif %}
{% endif %}
{%- endfor %}

## 🩶 Figures & Illustrations

{% for annotation in annotations -%}

{% if annotation.type == "image" and annotation.imageRelativePath %}

![[{{annotation.imageRelativePath}}]]

{% if annotation.comment %}

> **Comment:** {{annotation.comment}}

{% endif %}

*Page {{annotation.pageLabel}}*

{% endif %}

{% if annotation.colorCategory == "gray" or annotation.colorCategory == "grey" %}

> {{annotation.annotatedText}}

*Page {{annotation.pageLabel}}*

{% if annotation.comment %}

> **Comment:** {{annotation.comment}}

{% endif %}

{% endif %}

{%- endfor %}

``
``
### 💬 Standalone Notes & Comments
{% for annotation in annotations -%}
{% if annotation.type == "note" or (annotation.comment and not annotation.annotatedText and annotation.type != "image") %}
- Note (p. {{annotation.pageLabel}}): {{annotation.comment}}
{% endif %}
{%- endfor %}