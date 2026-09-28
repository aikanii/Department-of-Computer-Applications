<div align="center">

<img src="frontend/src/assets/ccs-logo.png" alt="College of Computer Studies logo" width="96" height="96">

# Department of Computer Applications — Official Website

**Department of Computer Applications · College of Computer Studies · MSU–Iligan Institute of Technology**

A CMS-backed, accreditation-aware department website built with a **Django REST** backend and a **React + TypeScript** frontend.

[![Live Site](https://img.shields.io/badge/Live%20Site-msuiit--comapps.vercel.app-0A7C3F?style=flat-square&logo=vercel&logoColor=white)](https://msuiit-comapps.vercel.app)
[![Last Commit](https://img.shields.io/github/last-commit/paulcastor30/Department-of-Computer-Applications?style=flat-square)](https://github.com/paulcastor30/Department-of-Computer-Applications/commits/main)
[![Issues](https://img.shields.io/github/issues/paulcastor30/Department-of-Computer-Applications?style=flat-square)](https://github.com/paulcastor30/Department-of-Computer-Applications/issues)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](#contributing)
[![License](https://img.shields.io/badge/License-TBD-lightgrey?style=flat-square)](#license)

![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=flat-square&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-6.0-092E20?style=flat-square&logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/Django%20REST%20Framework-A30000?style=flat-square)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-prod-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-3.4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Vitest](https://img.shields.io/badge/Vitest-3-6E9F18?style=flat-square&logo=vitest&logoColor=white)

[Live Demo](https://msuiit-comapps.vercel.app) · [Report a Bug](https://github.com/paulcastor30/Department-of-Computer-Applications/issues/new) · [Request a Feature](https://github.com/paulcastor30/Department-of-Computer-Applications/issues/new) · [Deployment Guide](DEPLOYMENT.md)

</div>

---

## Overview

This repository powers the public website of the **Department of Computer Applications (DCA)** at **MSU–IIT**. It is designed to read like a formal, student-facing academic department site while giving department staff a structured, permission-controlled way to manage content — including evidence artefacts used for accreditation and quality-assurance work.

The project is intentionally developed as an **open-source, contributor-friendly codebase**. The frontend began as a polished static UI and is being migrated, page by page, to Django-backed content. Some pages are already fully dynamic; others remain placeholder-driven until their backend models land. That incremental state is expected.

**Design principles**

| Principle | What it means in practice |
| --- | --- |
| Academic & restrained | Formal tone, no promotional copy, no invented statistics |
| Evidence-aware | First-class support for accreditation evidence (AACCUP, AUN-QA, CHED COPC/COE) |
| Editor-friendly | Content lives in Django admin; non-developers can publish without touching code |
| Accessible & responsive | Semantic markup, labelled controls, mobile-first layouts |
| Maintainable | Small domain apps, typed API contracts, shared hooks — no clever code |

---

## Key Features

- **Headless CMS workflow** — Django admin as the editorial interface, DRF read-only endpoints for the public site.
- **Domain-driven backend** — separate apps for `core`, `academics`, `people`, `communications`, `quality`, `research`, and `extension`.
- **Role-based editorial permissions** — one command provisions `site_admin`, `qa_editor`, `program_editor`, `faculty_editor`, `research_editor`, and `communications_editor` groups.
- **Publishable content model** — every public entity carries `slug`, `is_published`, `featured`, `sort_order`, and audit timestamps out of the box.
- **Faculty directory & profiles** — filterable by classification, programme, and expertise; profiles aggregate education, publications, projects, supervised theses, and more.
- **Programme pages** — BSCA and MSCA content (PEOs, outcomes, tracks, curriculum structure, thesis information, documents) served from the API with graceful placeholder fallback.
- **Accreditation evidence registry** — evidence documents tagged by framework and area code, linkable to programmes and faculty.
- **Site-wide search & SEO helpers** — header search, per-page `<Seo>` metadata, breadcrumbs.
- **Flexible deployment** — split deployment (Vercel + Railway) *or* single-origin, where Django serves the built SPA.
- **Type-safe frontend** — TypeScript API types, TanStack Query hooks, shadcn/ui component library on Radix primitives.

---

## Current architecture

The repository currently has a `backend` folder, a `frontend` folder, and a root `requirements.txt` file, with Django serving as the backend and a Vite based React frontend for the public user interface.

The backend is configured with Django 6.0.3, Django REST framework, and `django-cors-headers`, and is structured around domain apps such as `core`, `academics`, `people`, `research`, `extension`, `communications`, and `quality`.

The frontend uses Vite with React, TypeScript, React Router, React Query, and a Tailwind based component setup, with scripts for development, build, linting, preview, and tests already defined in `package.json`.

## Repository structure

```text
Department-of-Computer-Applications/
├── backend/        # Django project and backend apps
├── frontend/       # React + Vite frontend
└── requirements.txt
```

## Tech stack

### Backend
- Django
- Django REST framework
- django-cors-headers
- SQLite for local development

### Frontend
- React
- TypeScript
- Vite
- React Router
- TanStack Query
- Tailwind CSS
- Radix UI based components
- Vitest

## Development workflow

### 1. Backend

From the project root:

```bash
cd backend
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
pip install -r ../requirements.txt
python manage.py migrate
python manage.py runserver
```

### 2. Frontend

In a second terminal:

```bash
cd frontend
npm install
npm run dev
```

### 3. Production style local test

If you want Django to serve the built frontend:

```bash
cd frontend
npm run build

cd ../backend
python manage.py collectstatic --noinput
python manage.py runserver
```

## Contribution guide

We welcome contributors at all levels.

### Good beginner contributions
- fix typos or improve documentation
- improve placeholder text
- add loading and empty states
- improve accessibility labels and alt text
- refine responsive spacing and layout consistency
- add tests for existing views and serializers

### Intermediate contributions
- connect React pages to existing API endpoints
- improve admin usability
- add filters, search, and pagination
- add reusable UI components
- improve error handling and API hooks
- add contributor friendly setup scripts

### Advanced contributions
- design and implement new backend models
- improve editorial workflow and permissions
- add accreditation evidence structures
- optimize query performance and serializer design
- harden deployment and CI workflows
- improve search architecture and observability

## How to contribute

1. Fork the repository
2. Create a feature branch
3. Make one focused change at a time
4. Test your change locally
5. Open a pull request with a clear summary

Suggested branch naming:

```text
feature/home-api-integration
fix/faculty-admin-filter
docs/update-readme
```

## Contribution principles

- keep changes focused and reviewable
- prefer readable code over clever code
- write for maintainability
- preserve accessibility and responsiveness
- document non obvious decisions
- do not break existing public routes without discussion

## Recommended first issues

A useful issue board for this project would include labels such as:

- `good first issue`
- `frontend`
- `backend`
- `documentation`
- `accessibility`
- `testing`
- `help wanted`

## What contributors should know

This project is moving toward a model where:

- **React** handles the public facing experience
- **Django** handles admin, content, API endpoints, media, permissions, and structured evidence

That means some pages may remain partially static while their backend models and APIs are still being introduced. Incremental improvement is expected and acceptable.

## Suggested next milestones

- finish wiring the first CMS backed pages: Home, About, Programs, Faculty, News
- expand the backend editorial workflow by role
- strengthen documentation for setup and contribution
- add tests for APIs and admin behavior
- improve deployment instructions for contributors

## License

Add a license file before wider community onboarding. For an open source academic web project, a permissive license such as MIT or Apache 2.0 is usually the simplest option.

## Maintainers

This repository is currently maintained by the project owner and open to community contributions. If you want to contribute but are unsure where to start, begin with documentation, accessibility, or UI cleanup.
