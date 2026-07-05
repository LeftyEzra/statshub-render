# StatsHub — Sports Analytics & Service Marketplace Platform

### **Overview**
StatsHub is a unified sports platform  designed and developed to help basketball teams manage performance data, engage fans, and grow their brand. It combines advanced analytics with an integrated **Elite Store** for merchandise sales, creating a complete ecosystem for players, coaches, and supporters.

### **Problem**
Teams often rely on manual paperwork or scattered tools to track performance and manage fan engagement. This makes it hard to analyze player progress, prepare strategies, and build a professional brand.


### **Solution**
StatsHub provides:
- **Player Profiles**: Season‑long statistics stored and accessible anytime.  
- **Coaching Analytics**: Real‑time team stats, shooting accuracy, efficiency dashboards.  
- **Team Management**: Rosters, standings, and game logs in one hub.  
- **Fan Engagement**: News, galleries, and highlights to connect with supporters.  
- **Elite Store**: Integrated e‑commerce for selling official sports gear.  

---

### **Tech Stack**
- **Backend**: Python, Django, PostgreSQL  
- **Frontend**: JavaScript, Bootstrap, HTML/CSS  
- **Deployment**: Render (cloud hosting)  
- **Extras**: Responsive design, authentication, role‑based access  

### **Impact**
- Coaches can make data‑driven decisions using real‑time analytics.  
- Every player has a personal profile where they can track their game‑by‑game statistics and view detailed performance analysis. All season games are saved in the system,     so coaches and players can go back at any time to review past performances, compare trends, and see how progress has been made over the course of the season. 
- Fans stay connected through highlights and merchandise.  
- Teams gain a professional digital presence that supports performance and revenue.  


### **Link**
[StatsHub Live Demo](https://statshub-app.onrender.com)




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
