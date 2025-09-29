# profiler_documents_templates

Welcome to the **Profiler Templates** repository: a collection of flexible templates for automatically generating CVs and cover letters. These templates are designed for use with a conversational agent capable of creating professional PDF documents from JSON input.

---

## Repository Structure

### Folders

- `CV_templates/`  
  Contains 5 HTML/CSS CV templates ready for PDF generation via **WeasyPrint**:  
  1. `cv_classic.html.jinja2` – Classic, single column.  
  2. `cv_modern_two_column.html.jinja2` – Modern, two columns, compact layout.  
  3. `cv_left_bar.html.jinja2` – Left sidebar for skills and certifications.  
  4. `cv_minimal.html.jinja2` – Minimalist, clean and simple.  
  5. `cv_creative.html.jinja2` – Creative, colorful, visually appealing.

- `cover_letter_templates/`  
  Contains 3 HTML/CSS cover letter templates:  
  1. `cover_letter_classic.html.jinja2` – Classic and straightforward.  
  2. `cover_letter_modern.html.jinja2` – Modern with clear blocks and colored headings.  
  3. `cover_letter_creative.html.jinja2` – Creative and visual, ideal for creative industries.

---

## Features

- **All possible sections included**: skills, experience, education, projects, certifications, languages, hobbies, and additional sections.  
- **Optional sections**: automatically hidden if empty.  
- **PDF-ready**: easily converted using [WeasyPrint](https://weasyprint.org/).  
- **Configurable via JSON**:  
  - Colors (`primary`, `secondary`, `highlight`, `background`)  
  - Font and size (`font_size`)  
  - Additional sections (`additional_sections`)  

---

## Example JSON Input

```json
{
  "name": "Alice Dupont",
  "title": "Full-Stack Developer",
  "email": "alice.dupont@example.com",
  "phone": "+33 6 12 34 56 78",
  "linkedin": "alice-dupont",
  "github": "alice-dupont",
  "website": "https://alice.dev",
  "skills": {
    "Languages": ["Python", "JavaScript"],
    "Frameworks": ["React", "FastAPI"]
  },
  "education": [
    {"degree": "Master in Computer Science", "institution": "University of Paris", "year": "2022"},
    {"degree": "Bachelor in Computer Science", "institution": "University of Lyon", "year": "2020"}
  ],
  "experience": [
    {
      "position": "Full-Stack Developer",
      "company": "TechCorp",
      "start_date": "2022-09",
      "end_date": "Present",
      "description": "Web development using Python/React, CI/CD with Docker."
    }
  ],
  "projects": [
    {"name": "Portfolio Website", "description": "Website to showcase projects and skills."}
  ],
  "certifications": [
    {"name": "AWS Certified Developer", "year": "2023"}
  ],
  "languages": [
    {"language": "French", "level": "Native"},
    {"language": "English", "level": "Fluent"}
  ],
  "hobbies": ["Photography", "Hiking"],
  "additional_sections": [
    {"title": "Volunteering", "content": "Contributed to open-source projects and hackathons."}
  ]
}

```

## Usage

1. **Install WeasyPrint** for PDF generation from HTML/CSS.  
2. **Install Jinja2** for template rendering.  

```python
from jinja2 import Template
import json
from weasyprint import HTML

# Load JSON
with open('cv_data.json', 'r') as f:
    cv_data = json.load(f)

# Load a template
with open('CV_templates/cv_modern_two_column.html.jinja2', 'r', encoding='utf-8') as f:
    template = Template(f.read())

# Render HTML
rendered_html = template.render(**cv_data)

# Generate PDF
HTML(string=rendered_html).write_pdf("cv.pdf")

## Purpose

This repository supports **Profiler**, a SaaS platform that automatically generates personalized, professional CVs and cover letters. The conversational agent built for Profiler can:  

- Dynamically add, remove, or modify sections.  
- Select the appropriate template based on style preferences.  
- Generate ready-to-send PDF documents.  

## License

This project is licensed under the **MIT License**.
