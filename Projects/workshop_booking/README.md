# FOSSEE Workshop Booking - UI/UX Enhancement

## Project Overview

The FOSSEE Workshop Booking website is the project where we decided to do UI/UX redesign built with Django. The original site was working fine but plain. With this focusing on design style modern aesthetics, mobile responsiveness, accessibility and better user flow. Mainly targeting towards Computer students who will use it much more on mobiles.

---
## DEMO VIDEO

https://drive.google.com/file/d/1f4ZTjkZ1g1iSUsbKdovoxi220tHADERA/view?usp=drive_link

## Before & After Screenshots


### Login Page

| Before | After |
|--------|-------|
| ![Before Login](Images/before_login.png) | ![After Login](Images/after_login.png) |

### Home Page

| Before | After |
|--------|-------|
| ![Before Home](Images/before_home.png) | ![After Home](Images/after_home.png) |

### Logout Page

| Before | After |
|--------|-------|
| ![Before Logout](Images/before_logout.png) | ![After Logout](Images/after_logout.png) |

### Workshop Status

| Before | After |
|--------|-------|
| ![Before Status](Images/before_workshop_status.png) | ![After Status](Images/after_status.png) |

### Workshop Statistics

| Before | After |
|--------|-------|
| ![Before Stats](Images/before_home_stats.png) | ![After Stats](Images/after_stast.png) |

### Workshop Types

| After |
|-------|
| ![After Workshop Types](Images/after_workshop_types.png) |

### Profile Page

| After |
|-------|
| ![After Profile](Images/after_profile.png) |

### Proposed Workshop

| After |
|-------|
| ![After Proposed Workshop](Images/after_proposed_workshp.png) |

### Password Change

| After |
|-------|
| ![After Password Change](Images/after_pass_change.png) |

---

## Setup Instructions

### Requirements
- Python 3.10+
- pip
- Git

### Steps to Run Locally

```bash
# 1. Clone the repository
git clone <your-repo-url>
cd workshop_booking

# 2. Create virtual environment
python -m venv venv

# Windows
venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
pip install django-recurrence

# 4. Setup environment file
cp .sampleenv .env
```

Open `.env` and set:
```
SECRET_KEY=anyrandomsecretkey123
DEBUG=True
DB_ENGINE=sqlite3
DB_NAME=db.sqlite3
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=
```

```bash
# 5. Run migrations
python manage.py migrate
python manage.py migrate --run-syncdb

# 6. Create admin user
python manage.py createsuperuser

# 7. Run the server
python manage.py runserver
```

Visit `http://127.0.0.1:8000`

---

## Design Principles

## Design Principles

There are four main guiding principles that informed every single decision made during the process of designing this project.

 Mobile-First Design

Since the key audience is students who access the portal using their mobile phones, every layout was designed considering a small screen first before scaling it to fit desktop displays. Avoiding fixed-width layouts, the designs incorporate CSS Flexbox and Grid layouts.

Visual Hierarchy

The presence of a consistent hierarchy of typefaces, proper space usage, and good contrast ensures that the user can easily tell which options are available and prioritize the information being conveyed. The sections on the site have been designed with a dark navy background.



---

## Responsiveness

Responsive design was made possible using several methods. Flexbox and grid were used in the website using fluid sizing without the use of any pixel-width measurements on containers. The navbar changes to a hamburger icon that displays a dark overlay when hovered for devices less than 992px in width. The sidebar filter of the statistics page folds vertically for devices with viewports less than 900px wide. Form fields all have at least a minimum font size of 1rem to avoid zooming by iOS Safari on focusing. Cards use an `auto-fill` combined with `minmax()` method in order to dynamically resize according to the viewport size.

---

## Trade-offs

The trade-off that came up first involved enhancing Django templates using new CSS techniques rather than creating an entirely new React SPA. It could have brought about good component reusability and state management for the project. However, it would have meant creating everything related to the frontend, including Django forms, CSRF tokens, session authentication, and API calls — increasing the development effort drastically. On the other hand, the template improvement option offered the same output without changing anything on the backend.

The second trade-off was involving an extra dependency in the form of Google fonts (Inter). It would bring one additional network request at initial loading, yet it will make a positive impact on typography and legibility.

---

## Most Challenging Part
The hardest part of this assignment was the environment setup for development purposes. The original project was created with a PostgreSQL production environment in mind, and the content of the `.sampleenv` file included dummy variables such as `<db_engine>`, making the entire project fall with an error related to importing at launch time. To understand the chain between .env file, local_settings.py and settings.py file was necessary to debug everything. Furthermore, there were several `urls.py` files in the entire project, and all of them were using the `from django.conf.urls import url` command, which is deprecated since Django version 4.x and should be replaced by `from django.urls import re_path as url`.

---

## Files Modified

- `workshop_app/templates/workshop_app/base.html`
- `workshop_app/templates/workshop_app/index.html` (new)
- `workshop_app/templates/workshop_app/login.html`
- `workshop_app/templates/workshop_app/register.html`
- `workshop_app/templates/workshop_app/view_profile.html`
- `workshop_app/templates/workshop_app/edit_profile.html`
- `workshop_app/templates/workshop_app/propose_workshop.html`
- `workshop_app/templates/workshop_app/workshop_detail.html`
- `workshop_app/templates/workshop_app/workshop_status_coordinator.html`
- `workshop_app/templates/workshop_app/workshop_status_instructor.html`
- `workshop_app/templates/workshop_app/workshop_type_list.html`
- `workshop_app/templates/workshop_app/workshop_type_details.html`
- `workshop_app/templates/workshop_app/activation.html`
- `workshop_app/templates/workshop_app/logout.html`
- `statistics_app/templates/statistics_app/workshop_public_stats.html`
- `statistics_app/templates/statistics_app/workshop_stats.html`
- `statistics_app/templates/statistics_app/profile_stats.html`
- `statistics_app/templates/statistics_app/team_stats.html`
- `statistics_app/templates/statistics_app/paginator.html`
- `workshop_app/static/workshop_app/css/base.css`
- `workshop_app/views.py`
- `workshop_portal/urls.py`
- `workshop_app/urls.py`
- `cms/urls.py`

---

## Tech Stack

- **Backend:** Django 3.2, Python 3.12
- **Frontend:** Django Templates, CSS3 (Flexbox/Grid), JavaScript
- **Fonts:** Inter (Google Fonts), Material Icons
- **Charts:** Chart.js, Google GeoChart
- **Database:** SQLite (local development)