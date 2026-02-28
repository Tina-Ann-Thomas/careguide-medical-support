# careguide-medical-support
CareGuide – A smart emergency support web application that evaluates symptom severity and suggests the appropriate medical department and nearby hospitals with direct contact and Google Maps integration.When every minute matters, CareGuide provides structured guidance and fast emergency recommendations.
# Installation 
Clone the repository:
```bash
git clone https://github.com/tina-ann-thomas/careguide-medical-support.git
Run commands: 
cd careguide-medical-support
# Folder Structure
careguide-medical-support/
│
├── index.html        
├── script.js
├── style.css             
└── README.md
# Architecture Diagram
[User] 
   |
   v
[Frontend UI]
   |  -- District Selection --> Populate City Dropdown
   |  -- Symptom Selection
   v
[Logic Layer: JS]
   |  -- Validate input (district + symptom required)
   |  -- Filter Hospitals (district + optional city + dept)
   |  -- Sort emergency if high severity
   v
[Data Layer: keralaHospitals + symptomConfig]
   |
   v
[Display Layer]
   |  -- Alert Message
   |  -- Department Info
   |  -- Hospital Cards (Contacts + Google Maps)
   
[User]
# Individual Participant - Tina Ann Thomas

# Project Overview

CareGuide helps users:
* Select their District
* Select their City
* Choose their Main Health Concern
* Click "Check Emergency Level"

The system then:
*Evaluates the emergency severity (Low / Medium / High)
* Displays an emergency alert message
* Recommends the correct medical department
* Shows nearby hospitals
* Provides contact numbers
* Offers direct Google Maps navigation
* Shows 24×7 emergency availability (if applicable)
* Displays  Ambulance 108 call option for high-risk cases

Example Use Case
Input:
District: Ernakulam
City: Chittor
Main Concern: Breathing Difficulty
Output:
Emergency Alert
Breathing difficulty requires urgent medical care.
Call Ambulance 108 Immediately
Recommended Department:
Emergency
Nearby Hospital Example:
Aster Medcity
Cheranalloor, Kochi
24×7 Emergency Available
Main: 0484-6699999
Emergency: 0484-6699999
Open in Google Maps (redirects to hospital location)

 # How It Works
1. Symptom Configuration System

Each symptom is mapped to:

Severity level (Low / Medium / High)

Required medical department

Emergency message

Example:

Breathing Difficulty → High Severity → Emergency Department

2. Hospital Filtering Logic

The system filters hospitals based on:

Selected district

Selected city

Required department availability

If severity is High, hospitals with 24×7 emergency services are prioritized.

3️. Emergency Handling

For high severity cases:

Displays urgent alert

Shows "Call Ambulance 108 Immediately"

Highlights emergency-ready hospitals

Hospital Database

The system includes structured hospital data across multiple districts in Kerala, including:

District

City

Hospital Name

Address

Emergency Availability

Main Contact Number

Department-wise Contact Numbers

Google Maps Link

# Tech Stack

HTML5

CSS3

JavaScript

No external frameworks used.

# Key Features

Symptom-based emergency level detection

Department recommendation system

District and city-based hospital filtering

24×7 emergency identification

Click-to-call integration

Direct Google Maps redirection

Clean and responsive UI

# Project Goal

To reduce decision-making delay during medical emergencies by providing:

Immediate severity evaluation

Clear department guidance

Quick hospital access
# Disclaimer
CareGuide is an emergency guidance tool and does not replace professional medical diagnosis.

# Code


In life-threatening situations, always call emergency services immediately.

