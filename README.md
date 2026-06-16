# StatsHub — Sports Analytics & Service Marketplace Platform

StatsHub is a dynamic, multi-app Django web application built to merge advanced sports analytics with a localized digital marketplace ecosystem. 
The platform provides a customized administrative workspace for organizers alongside secure frontend capabilities for real-time user-driven registration, 
product listing, and service tracking.



## 📂 Core Architecture & Applications

The project is structured into three specialized application modules:
1. **`team` (StatsHub Core):** Manages seasons, team rosters, match statistics, and handles **The Open Source League (OSL)**—a developer-centric tournament showcasing competitive rivalries between core programming languages (Team Python) and structural stack tools (JavaScript, Bootstrap, CSS, C++, HTML).
2. **`store` (Elite Store):** A fully integrated digital marketplace module built to register, track, and showcase products, inventory management, and digital assets.
3. **`services` (Elite Services):** A dedicated service marketplace platform engineered to list, categorize, and schedule trades or professional consultations.



## 🚀 Key Features Built

### 1. Advanced Custom Admin Workspace
* **Jazzmin Dashboard Integration:** Replaced the generic Django admin with a sleek, responsive, modern UI dashboard.
* **Dynamic Quick-Access Menus:** Configured a customized top navigation bar with smart app-specific dropdown entries targeting individual modules (`team`, `store`, and `services`).
* **UI Customizer Implementation:** Implemented dynamic UI builder functionality and robust static theme bypassing via manual backend theme rules (`darkly`/`dark`) to maintain strict branding across the deck.

### 2. Live Deployment Architecture (Render + Cloud Database)
* **Production Deployment Pipeline:** Configured secure application hosting on Render utilizing `gunicorn` for the WSGI application layer.
* **PostgreSQL Cloud Synchronization:** Routed database interactions through an external live PostgreSQL server instance, enabling seamless data entry sharing between local development environments (`127.0.0.1:8000`) and the live production web application.
* **Database Migration Handling:** Resolved deployment-blocking port timeout constraints and optimized database structures for clean updates.

### 3. Structural Database Model Optimization
* **Flexible Relationships:** Tweaked Django relationship variables to handle partial data structures. Modified the `Competition` model's `ManyToManyField` parameters (`opponents`) using `blank=True` rules to let organizers create tournaments cleanly without hard dependencies.
* **Clean Architecture Re-naming:** Standardized naming conventions across choice fields (e.g., `competition_type`) to eliminate typing bugs and maximize codebase scannability.

### 4. Robust Frontend Data Registration Forms
* **Dynamic Competition Registers:** Engineered a standalone view utilizing class-based `View` structures (`CompetitionCreateView`) allowing designated superusers to register active match metadata straight from the frontend layout.
* **User Validation Error Feeds:** Built template loops into the HTML form container (`competition_registration.html`) to display inline validation notices (e.g., *“⚠️ This field is required”*) when fields are omitted, bypassing default browser overrides.
* **Production Redirect Architecture:** Removed brittle query parameters from redirect URLs and replaced them with Django's native `reverse()` path engine to prevent `404 Page Not Found` routing loops on live domains.

---

## 🛠️ Tech Stack & Dependencies

* **Backend Framework:** Django (Python)
* **Database:** PostgreSQL (Hosted via Render)
* **Admin Dashboard Theme:** Django-Jazzmin
* **Frontend UI Library:** Bootstrap & HTML5 Custom Layouts
* **Deployment Server:** Gunicorn

---

## 🔧 Installation & Local Setup

To get a local development instance running and connected to the live database, follow these steps:

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/LeftyEzra/statshub-render.git](https://github.com/LeftyEzra/statshub-render.git)
   cd statshub-render



#Set Up Your Virtual Environment
python -m venv venv
source venv/bin/activate  
# On Windows use: venv\Scripts\activate

## Install Dependencies
pip install -r requirements.txt


## Apply Pending Database Schema Alterations:
python manage.py makemigrations
python manage.py migrate

## Fire Up  The Local Server
python manage.py runserver
Open your browser and navigate to http://127.0.0.1:8000/.


## 📂 System Project Structure Overview

```text
TEAM_WEBSITE/
├── settings.py          # App configurations, Jazzmin themes & DB Routes
└── urls.py              # Global URL patterns and control-deck routers

team/                    # Primary Sports Application Module (StatsHub Core)
├── models.py            # Competition, Season, Team, and Opponent blueprints
├── views.py             # Form validation & reverse redirect methods
└── forms.py             # Form mappings for frontend registration

store/                   # Elite Store Application Module
└── models.py            # Product entries, pricing models, and inventory data

services/                # Elite Services Application Module
└── models.py            # Service trade listings, category tags, and orders

templates/               # Frontend Presentation Components
└── competition_registration.html  # Custom layout with inline error loops
