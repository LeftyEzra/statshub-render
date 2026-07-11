# StatsHub — Sports Analytics & Service Marketplace Platform

### **Overview**
StatsHub is a unified sports platform  designed and developed to help basketball teams manage performance data, engage fans, and grow their brand. It combines advanced analytics with an integrated **Elite Store** for merchandise sales, creating a complete ecosystem for players, coaches, and supporters.

### **Problem**
Teams often rely on manual paperwork or scattered tools to track performance and manage fan engagement. This makes it hard to analyze player progress, prepare strategies, and build a professional brand.


### **Solution**
StatsHub provides:
- **Player Profiles**: Season‑long statistics stored and accessible anytime.  
- **Coaching Analytics**: Real‑time team stats, shooting accuracy, efficiency dashboards.
- **Overall Performance Dashboard**: Summarizes team and player efficiency across the season.
- **Shot Charts**: Visual tracking of shot locations and accuracy for each game.
- **Team Management**: Rosters, standings(Displays team rankings, wins/losses, and points per game), and game logs in one hub.  
- **Fan Engagement**: News, galleries, and highlights to connect with supporters.  
- **Elite Store**: Integrated e‑commerce for selling official sports gear.  

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




# Email Setup & SMTP Documentation (Brevo)

This document explains how to configure the email backend for the password reset functionality once a custom domain name is purchased.

---

## 1. Django Settings Configuration (`settings.py`)

Add or update the following lines in your `settings.py` file to handle SMTP traffic securely:

```python
# settings.py

EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp-relay.brevo.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True

# Credentials pulled from the .env file
EMAIL_HOST_USER = config('EMAIL_HOST_USER')
EMAIL_HOST_PASSWORD = config('EMAIL_HOST_PASSWORD')
DEFAULT_FROM_EMAIL = config('DEFAULT_FROM_EMAIL')

```

---

## 2. Environment Variables (`.env`)

Create or update your `.env` file in the root directory. Replace the placeholder values with your actual Brevo credentials once your domain is ready:

```text
EMAIL_HOST_USER=b19f4d001@smtp-brevo.com
EMAIL_HOST_PASSWORD=your_newly_generated_smtp_key_here
DEFAULT_FROM_EMAIL=noreply@yourdomain.com

```

---

## 3. Steps to Complete After Buying a Domain

Once you purchase your domain name, follow these steps to ensure your emails actually reach your users' inboxes:

### Step 1: Add and Verify Your Domain in Brevo

1. Log in to the **Brevo Dashboard**.
2. Go to **Settings** (left menu) > **Senders, domains, IPs** > **Domains**.
3. Click **Add a domain** and enter your new domain (e.g., `yourdomain.com`).
4. Brevo will provide specific **DNS records** (SPF, DKIM, and DMARC).

### Step 2: Configure Your DNS Settings

1. Log in to the platform where you bought your domain (e.g., Namecheap, GoDaddy, Hostinger).
2. Open the **DNS Management / Advanced DNS** settings for your domain.
3. Copy the TXT records provided by Brevo and paste them into your domain's DNS settings.
4. Wait a few minutes, then click **Verify & Authenticate** in Brevo. Look for the green checkmarks.

### Step 3: Add Your Sender Email

1. In Brevo, go to the **Senders** tab.
2. Click **Add a sender**.
3. Enter your custom email address (e.g., `noreply@yourdomain.com`).
4. Update the `DEFAULT_FROM_EMAIL` line in your `.env` file to match this exact address.

---

## 4. Important Python Code Reminders

When writing code to send emails in your views, remember the **tuple comma trap**:

* **Incorrect Code (Will Crash):**
```python
# Do NOT put a comma at the end of the string
email_body = f'Reset your password using the link below:\n\n{url}', 

```


* **Correct Code (Works Perfectly):**
```python
# The text must remain a pure string
email_body = f'Reset your password using the link below:\n\n{url}' 

```
