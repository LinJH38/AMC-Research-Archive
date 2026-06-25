---
type: literature_note
citekey: {{citekey}}
tags: [AMC, paper]
---
# {{title}}

## 📑 논문 개요 (Overview)
> [!abstract] 초록
> {{abstractNote}}

- **저자:** {{authors}}
- **발표 연도:** {{date | format("YYYY")}}
- **Zotero 바로가기:** [로컬 앱에서 열기]({{desktopURI}})
- **PDF 원문 보기:** [옵시디언에서 열기]({{pdfRelativePath}})

---
## 🧠 AMC 연구 적용 포인트


---
## 📝 내 요약 노트 (Zotero Notes)
{% if notes.length > 0 -%}
{% for note in notes %}
{{note.note}}
{% endfor %}
{%- else -%}
작성된 요약 노트가 없습니다.
{%- endif %}

---
## 🖋️ 조테로 하이라이트 & 캡처
{% for annotation in annotations -%}
{%- if annotation.annotatedText -%}
> [!quote]{% if annotation.color %}|{{annotation.color}}{% endif %}
> {{annotation.annotatedText}} ([p.{{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}))
{%- if annotation.comment %}
> **메모:** {{annotation.comment}}
{%- endif %}
{%- endif %}
{%- if annotation.imageRelativePath -%}
![[{{annotation.imageRelativePath}}]]
{%- endif %}
{% endfor %}