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

In life-threatening situations, always call emergency services immediately.

# Code
# HTML CODE:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CareGuide – Your Emergency Medical Support Companion</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <div class="header-container">
            <h1>CareGuide – Your Emergency Medical Support Companion</h1>
            <h3>Quickly understand your symptoms and find the right medical help when every minute matters.</h3>
        </div>
    </header>
    <main>
      <section id="input-section">
    <h2>Enter Patient Details</h2>
<div class="form-group">
    <label for="district">Select District</label>
    <select id="district">
        <option value="">-- Select District --</option>
    </select>
</div>
<div class="form-group">
    <label for="city">Select City</label>
    <select id="city">
        <option value="">-- Select City --</option>
    </select>
</div>
    <div class="form-group">
        <label for="symptom">What is the main concern right now?</label>
        <select id="symptom">
    <option value="">-- Select Main Symptom --</option>
        </select>
    </div>
    <button id="check-btn">Check Emergency Level</button>
</section>
      <section id="alert-section" style="display:none;">
         <h2>⚠ Emergency Alert</h2>
         <div id="alert-box">Emergency level will appear here.</div>
</section>
        <section id="department-section" style="display:none;">
            <h2>Recommended Department</h2>
            <p id="department-result">
                Department suggestion will appear here.
            </p>
        </section>
        <section id="hospital-section" style="display:none;">
            <h2>Nearby Hospitals</h2>
            <div id="hospital-list"></div> 
        </section>
    </main>
    <script src="script.js"></script>
</body>
</html>
# CSS Code
body {
    margin: 0;
    font-family: 'Segoe UI', Tahoma, sans-serif;
    background-color: #fdf6ec;   
    color: #2c2c2c;
}
header {
    text-align: center;
    padding: 60px 20px 40px;
}
header h1 {
    margin: 0;
    font-size: 32px;
    font-weight: 700;
    color: #c62828;   
    letter-spacing: 0.5px;
}
header h3 {
    margin-top: 15px;
    font-size: 20px;
    font-weight: 500;
    color: #3676c4;   
}
section {
    max-width: 720px;
    margin: 30px auto;
    padding: 45px;
    background: #ffffff;
    border-radius: 18px;
    box-shadow: 0 12px 30px rgba(0,0,0,0.06);
    animation: fadeIn 0.4s ease-in;
}
.form-group {
    margin-bottom: 28px;
}
label {
    font-weight: 600;
    font-size: 14px;
    color: #3a3a3a;
    display: block;
    margin-bottom: 6px;
}
select,
textarea,
input {
    width: 100%;
    padding: 14px;
    border-radius: 12px;
    border: 1px solid #e2e2e2;
    font-size: 15px;
    background: #fafafa;
    transition: all 0.2s ease;
}
select:focus,
textarea:focus,
input:focus {
    outline: none;
    border-color: #3676c4; 
    background: #ffffff;
    box-shadow: 0 0 0 3px rgba(54,118,196,0.1);
}
button {
    width: 100%;
    padding: 16px;
    border: none;
    border-radius: 14px;
    background: #c62828;  
    color: white;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.25s ease;
}
button:hover {
    background: #b71c1c;
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(198,40,40,0.25);
}
#alert-box {
    padding: 22px;
    border-radius: 14px;
    font-weight: 600;
    background: #fdecea;
    color: #b71c1c;
    border-left: 5px solid #c62828;
    margin-bottom: 20px;
}
.hospital-card {
    padding: 20px;
    border-radius: 14px;
    margin-bottom: 18px;
    background: #ffffff;
    border: 1px solid #eee;
    border-left: 5px solid #3676c4;  
    transition: all 0.2s ease;
}
.hospital-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.06);
}
.hospital-card hr {
    border: 0;
    border-top: 1px dashed #ddd;
    margin: 15px 0;
}
.map-btn {
    display: block;
    text-align: center;
    margin-top: 15px;
    padding: 12px;
    background: #3676c4;  
    color: white;
    text-decoration: none;
    border-radius: 10px;
    font-weight: 600;
    font-size: 14px;
    transition: 0.2s ease;
}
.map-btn:hover {
    background: #2f66a8;
}
h2 {
    margin-top: 0;
    margin-bottom: 25px;
    font-weight: 700;
    color: #3676c4; 
}
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(15px); }
    to { opacity: 1; transform: translateY(0); }
}
# Javascript Code

const keralaHospitals = [
{
  district: "Thiruvananthapuram",
  city: "Pattom",
  name: "SUT Hospital",
  address: "Pattom, Thiruvananthapuram",
  emergency: true,
  map: "https://maps.google.com/?q=SUT+Hospital+Pattom",
  mainContact: "0471-4077777",
  departments: {
   "Cardiology": "0471-4077000",
    "Neurology": "0471-4077111",
    "Orthopedics": "0471-4077222",
    "Ophthalmology": "0471-4077666",
    "Psychiatry": "0471-4077333",
    "Dermatology": "0471-4077444",
    "General Medicine": "0471-4077555",
    "Emergency": "0471-4077999"
  }
},
{
  district: "Thiruvananthapuram",
  city: "Neyyattinkara",
  name: "NIMS Medicity",
  address: "Aralumoodu, Neyyattinkara",
  emergency: true,
  map: "https://maps.google.com/?q=NIMS+Hospital+Neyyattinkara",
  mainContact: "0471-2223545",
  departments: {
    "General Medicine": "0471-2223500",
    "Emergency": "0471-2223999"
  }
},
{
  district: "Thiruvananthapuram",
  city: "Kazhakoottam",
  name: "SP Medifort Hospital",
  address: "Eanchakkal, Thiruvananthapuram",
  emergency: true,
  map: "https://maps.google.com/?q=SP+Medifort+Hospital+Trivandrum",
  mainContact: "0471-3577777",
  departments: {
    "Cardiology": "0471-3577111",
    "Emergency": "0471-3577999"
  }
},
{
  district: "Thiruvananthapuram",
  city: "Attingal",
  name: "Mother Hospital",
  address: "Attingal, Kerala",
  emergency: true,
  map: "https://maps.google.com/?q=Mother+Hospital+Attingal",
  mainContact: "0470-2623000",
  departments: {
    "General Medicine": "0470-2623111",
    "Emergency": "0470-2623999"
  }
},
{
  district: "Thiruvananthapuram",
  city: "Varkala",
  name: "Gokulam Medical College Hospital",
  address: "Venjaramoodu, Thiruvananthapuram",
  emergency: true,
  map: "https://maps.google.com/?q=Gokulam+Medical+College+Trivandrum",
  mainContact: "0472-3041000",
  departments: {
    "Cardiology": "0472-3041111",
    "Emergency": "0472-3041999"
  }
},
{
  district: "Kollam",
  city: "Kottiyam",
  name: "ESIC Medical College",
  address: "Parippally, Kollam",
  emergency: true,
  map: "https://maps.google.com/?q=ESIC+Medical+College+Parippally",
  mainContact: "0474-2573000",
  departments: {
     "Cardiology": "0474-2751000",
    "Neurology": "0474-2751111",
    "Orthopedics": "0474-2751222",
    "Psychiatry": "0474-2751333",
    "Dermatology": "0474-2751444",
    "General Medicine": "0474-2751555",
    "Emergency": "0474-2751999"
  }
},
{
  district: "Kollam",
  city: "Chinnakada",
  name: "Upasana Hospital",
  address: "Kollam, Kerala",
  emergency: true,
  map: "https://maps.google.com/?q=Upasana+Hospital+Kollam",
  mainContact: "0474-2762888",
  departments: {
    "Cardiology": "0474-2762111",
    "Emergency": "0474-2762999"
  }
},
{
  district: "Kollam",
  city: "Karunagappally",
  name: "Al Shifa Hospital",
  address: "Karunagappally, Kollam",
  emergency: true,
  map: "https://maps.google.com/?q=Al+Shifa+Hospital+Karunagappally",
  mainContact: "0476-2622000",
  departments: {
    "General Medicine": "0476-2622111",
    "Emergency": "0476-2622999"
  }
},
{
  district: "Kollam",
  city: "Punalur",
  name: "St. Joseph's Hospital",
  address: "Punalur, Kollam",
  emergency: true,
  map: "https://maps.google.com/?q=St+Josephs+Hospital+Punalur",
  mainContact: "0475-2222222",
  departments: {
    "General Medicine": "0475-2222111",
    "Emergency": "0475-2222999"
  }
},
{
  district: "Kollam",
  city: "Kundara",
  name: "Holy Cross Hospital",
  address: "Kundara, Kollam",
  emergency: true,
  map: "https://maps.google.com/?q=Holy+Cross+Hospital+Kundara",
  mainContact: "0474-2523333",
  departments: {
    "General Medicine": "0474-2523111",
    "Emergency": "0474-2523999"
  }
},
{
  district: "Pathanamthitta",
  city: "Adoor",
  name: "Mount Zion Medical College",
  address: "Adoor, Pathanamthitta",
  emergency: true,
  map: "https://maps.google.com/?q=Mount+Zion+Medical+College+Adoor",
  mainContact: "0473-4222000",
  departments: {
    "Cardiology": "0473-4221000",
    "Neurology": "0473-4221111",
    "Orthopedics": "0473-4221222",
    "Psychiatry": "0473-4221333",
    "Dermatology": "0473-4221444",
    "General Medicine": "0473-4221555",
    "Emergency": "0473-4221999"
  }
},
{
  district: "Pathanamthitta",
  city: "Kozhencherry",
  name: "Muthoot Medical Centre",
  address: "Kozhencherry, Kerala",
  emergency: true,
  map: "https://maps.google.com/?q=Muthoot+Medical+Centre+Kozhencherry",
  mainContact: "0468-2314000",
  departments: {
    "General Medicine": "0468-2314111",
    "Emergency": "0468-2314999"
  }
},
{
  district: "Pathanamthitta",
  city: "Ranni",
  name: "Mar Gregorios Memorial Hospital",
  address: "Ranni, Kerala",
  emergency: true,
  map: "https://maps.google.com/?q=Mar+Gregorios+Memorial+Hospital+Ranni",
  mainContact: "0473-5222222",
  departments: {
    "General Medicine": "0473-5222111",
    "Emergency": "0473-5222999"
  }
},
{
  district: "Pathanamthitta",
  city: "Pandalam",
  name: "St. Mary's Hospital",
  address: "Pandalam, Pathanamthitta",
  emergency: true,
  map: "https://maps.google.com/?q=St+Marys+Hospital+Pandalam",
  mainContact: "0473-4255000",
  departments: {
    "General Medicine": "0473-4255111",
    "Emergency": "0473-4255999"
  }
},
{
  district: "Pathanamthitta",
  city: "Konni",
  name: "Community Health Centre Konni",
  address: "Konni, Pathanamthitta",
  emergency: true,
  map: "https://maps.google.com/?q=CHC+Konni",
  mainContact: "0468-2244444",
  departments: {
    "General Medicine": "0468-2244111",
    "Emergency": "0468-2244999"
  }
},
{
  district: "Alappuzha",
  city: "Cherthala",
  name: "KVM Hospital",
  address: "Cherthala, Alappuzha",
  emergency: true,
  map: "https://maps.google.com/?q=KVM+Hospital+Cherthala",
  mainContact: "0478-2812211",
  departments: {
    "Cardiology": "0478-2811000",
    "Neurology": "0478-2811111",
    "Orthopedics": "0478-2811222",
    "Psychiatry": "0478-2811333",
    "Dermatology": "0478-2811444",
    "General Medicine": "0478-2811555",
    "Emergency": "0478-2811999"
  }
},
{
  district: "Alappuzha",
  city: "Kayamkulam",
  name: "M.S.M Hospital",
  address: "Kayamkulam, Kerala",
  emergency: true,
  map: "https://maps.google.com/?q=MSM+Hospital+Kayamkulam",
  mainContact: "0479-2442141",
  departments: {
    "General Medicine": "0479-2442111",
    "Emergency": "0479-2442999"
  }
},
{
  district: "Alappuzha",
  city: "Haripad",
  name: "Sree Narayana Medical Mission Hospital",
  address: "Haripad, Alappuzha",
  emergency: true,
  map: "https://maps.google.com/?q=SNMM+Hospital+Haripad",
  mainContact: "0479-2412345",
  departments: {
    "General Medicine": "0479-2412111",
    "Emergency": "0479-2412999"
  }
},
{
  district: "Alappuzha",
  city: "Mavelikkara",
  name: "Bishop Benziger Hospital",
  address: "Mavelikkara, Kerala",
  emergency: true,
  map: "https://maps.google.com/?q=Bishop+Benziger+Hospital+Mavelikkara",
  mainContact: "0479-2302345",
  departments: {
    "General Medicine": "0479-2302111",
    "Emergency": "0479-2302999"
  }
},
{
  district: "Alappuzha",
  city: "Chengannur",
  name: "District Hospital Chengannur",
  address: "Chengannur, Alappuzha",
  emergency: true,
  map: "https://maps.google.com/?q=District+Hospital+Chengannur",
  mainContact: "0479-2450000",
  departments: {
    "General Medicine": "0479-2450111",
    "Emergency": "0479-2450999"
  }
},
{
  district: "Kottayam",
  city: "Ettumanoor",
  name: "Holy Ghost Mission Hospital",
  address: "Ettumanoor, Kottayam",
  emergency: true,
  map: "https://maps.google.com/?q=Holy+Ghost+Mission+Hospital+Ettumanoor",
  mainContact: "0481-2537000",
  departments: {
    "General Medicine": "0481-2537111",
    "Emergency": "0481-2537999"
  }
},
{
  district: "Kottayam",
  city: "Changanassery",
  name: "Believers Church Medical College Hospital",
  address: "Kuttapuzha, Thiruvalla",
  emergency: true,
  map: "https://maps.google.com/?q=Believers+Church+Medical+College+Hospital",
  mainContact: "0469-3027000",
  departments: {
    "Cardiology": "0469-2701000",
    "Neurology": "0469-2701111",
    "Orthopedics": "0469-2701222",
    "Psychiatry": "0469-2701333",
    "Dermatology": "0469-2701444",
    "General Medicine": "0469-2701555",
    "Emergency": "0469-2701999"
  }
},
{
  district: "Kottayam",
  city: "Pala",
  name: "Mar Sleeva Medicity",
  address: "Pala, Kottayam",
  emergency: true,
  map: "https://maps.google.com/?q=Mar+Sleeva+Medicity+Pala",
  mainContact: "0482-2200000",
  departments: {
    "Cardiology": "0482-2200111",
    "Emergency": "0482-2200999"
  }
},
{
  district: "Kottayam",
  city: "Vaikom",
  name: "Taluk Headquarters Hospital Vaikom",
  address: "Vaikom, Kottayam",
  emergency: true,
  map: "https://maps.google.com/?q=THQ+Hospital+Vaikom",
  mainContact: "04829-221500",
  departments: {
    "General Medicine": "04829-221511",
    "Emergency": "04829-221599"
  }
},
{
  district: "Kottayam",
  city: "Kanjirappally",
  name: "St. Dominic's Hospital",
  address: "Kanjirappally, Kottayam",
  emergency: true,
  map: "https://maps.google.com/?q=St+Dominics+Hospital+Kanjirappally",
  mainContact: "04828-202345",
  departments: {
    "General Medicine": "04828-202311",
    "Emergency": "04828-202399"
  }
},
{
  district: "Idukki",
  city: "Kattappana",
  name: "St. John's Hospital",
  address: "Kattappana, Idukki",
  emergency: true,
  map: "https://maps.google.com/?q=St+Johns+Hospital+Kattappana",
  mainContact: "04868-250555",
  departments: {
   "Cardiology": "0486-8251000",
    "Neurology": "0486-8251111",
    "Orthopedics": "0486-8251222",
    "Psychiatry": "0486-8251333",
    "Dermatology": "0486-8251444",
    "General Medicine": "0486-8251555",
    "Emergency": "0486-8251999"
  }
},
{
  district: "Idukki",
  city: "Munnar",
  name: "Tata General Hospital",
  address: "Munnar, Idukki",
  emergency: true,
  map: "https://maps.google.com/?q=Tata+General+Hospital+Munnar",
  mainContact: "04865-230101",
  departments: {
    "General Medicine": "04865-230111",
    "Emergency": "04865-230199"
  }
},
{
  district: "Idukki",
  city: "Adimali",
  name: "Taluk Hospital Adimali",
  address: "Adimali, Idukki",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Adimali",
  mainContact: "04864-223500",
  departments: {
    "General Medicine": "04864-223511",
    "Emergency": "04864-223599"
  }
},
{
  district: "Idukki",
  city: "Nedumkandam",
  name: "District Hospital Nedumkandam",
  address: "Nedumkandam, Idukki",
  emergency: true,
  map: "https://maps.google.com/?q=District+Hospital+Nedumkandam",
  mainContact: "04868-234000",
  departments: {
    "General Medicine": "04868-234111",
    "Emergency": "04868-234199"
  }
},
{
  district: "Idukki",
  city: "Peerumedu",
  name: "Taluk Hospital Peerumedu",
  address: "Peerumedu, Idukki",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Peerumedu",
  mainContact: "04869-232300",
  departments: {
    "General Medicine": "04869-232311",
    "Emergency": "04869-232399"
  }
},
{
  district: "Ernakulam",
  city: "Edappally",
  name: "Amrita Institute of Medical Sciences",
  address: "Edappally, Kochi",
  emergency: true,
  map: "https://maps.google.com/?q=Amrita+Institute+of+Medical+Sciences+Kochi",
  mainContact: "0484-2851234",
  departments: {
    "Cardiology": "0484-2855000",
    "Neurology": "0484-2855111",
    "Orthopedics": "0484-2855222",
    "Psychiatry": "0484-2855333",
    "Dermatology": "0484-2855444",
    "General Medicine": "0484-2855555",
    "Emergency": "0484-2855999"
  }
},
{
  district: "Ernakulam",
  city: "Vennala",
  name: "Medical Trust Hospital",
  address: "MG Road, Kochi",
  emergency: true,
  map: "https://maps.google.com/?q=Medical+Trust+Hospital+Kochi",
  mainContact: "0484-2358001",
  departments: {
    "Cardiology": "0484-2358111",
    "Emergency": "0484-2358999"
  }
},
{
  district: "Ernakulam",
  city: "Chittor",
  name: "Aster Medcity",
  address: "Cheranalloor, Kochi",
  emergency: true,
  map: "https://maps.google.com/?q=Aster+Medcity+Kochi",
  mainContact: "0484-6699999",
  departments: {
    "Cardiology": "0484-6699000",
    "Neurology": "0484-6699111",
    "Orthopedics": "0484-6699222",
    "Psychiatry": "0484-6699333",
    "Dermatology": "0484-6699444",
    "General Medicine": "0484-6699555",
    "Emergency": "0484-6699999"
  }
},
{
  district: "Ernakulam",
  city: "Aluva",
  name: "Rajagiri Hospital",
  address: "Chunangamvely, Aluva",
  emergency: true,
  map: "https://maps.google.com/?q=Rajagiri+Hospital+Aluva",
  mainContact: "0484-2905000",
  departments: {
    "Cardiology": "0484-2905000",
    "Neurology": "0484-2905111",
    "Orthopedics": "0484-2905222",
    "Psychiatry": "0484-2905333",
    "Dermatology": "0484-2905444",
    "General Medicine": "0484-2905555",
    "Emergency": "0484-2905999"
  }
},
{
  district: "Ernakulam",
  city: "Kolenchery",
  name: "MOSC Medical College Hospital",
  address: "Kolenchery, Ernakulam",
  emergency: true,
  map: "https://maps.google.com/?q=MOSC+Medical+College+Kolenchery",
  mainContact: "0484-3055555",
  departments: {
    "General Medicine": "0484-3055111",
    "Emergency": "0484-3055999"
  }
},
{
  district: "Thrissur",
  city: "Ollur",
  name: "Amala Institute of Medical Sciences",
  address: "Amalanagar, Thrissur",
  emergency: true,
  map: "https://maps.google.com/?q=Amala+Institute+Thrissur",
  mainContact: "0487-2304000",
  departments: {
    "Cardiology": "0487-2304000",
    "Neurology": "0487-2304111",
    "Orthopedics": "0487-2304222",
    "Psychiatry": "0487-2304333",
    "Dermatology": "0487-2304444",
    "General Medicine": "0487-2304555",
    "Emergency": "0487-2304999"
  }
},
{
  district: "Thrissur",
  city: "Punkunnam",
  name: "Elite Mission Hospital",
  address: "Koorkenchery, Thrissur",
  emergency: true,
  map: "https://maps.google.com/?q=Elite+Mission+Hospital+Thrissur",
  mainContact: "0487-2436100",
  departments: {
    "General Medicine": "0487-2436111",
    "Emergency": "0487-2436999"
  }
},
{
  district: "Thrissur",
  city: "Kodungallur",
  name: "Modern Hospital",
  address: "Kodungallur, Thrissur",
  emergency: true,
  map: "https://maps.google.com/?q=Modern+Hospital+Kodungallur",
  mainContact: "0480-2809090",
  departments: {
    "General Medicine": "0480-2809111",
    "Emergency": "0480-2809999"
  }
},
{
  district: "Thrissur",
  city: "Chalakudy",
  name: "St. James Hospital",
  address: "Chalakudy, Thrissur",
  emergency: true,
  map: "https://maps.google.com/?q=St+James+Hospital+Chalakudy",
  mainContact: "0480-2706720",
  departments: {
    "General Medicine": "0480-2706711",
    "Emergency": "0480-2706799"
  }
},
{
  district: "Thrissur",
  city: "Guruvayur",
  name: "Little Flower Hospital",
  address: "Guruvayur, Thrissur",
  emergency: true,
  map: "https://maps.google.com/?q=Little+Flower+Hospital+Guruvayur",
  mainContact: "0487-2558111",
  departments: {
    "General Medicine": "0487-2558222",
    "Emergency": "0487-2558999"
  }
},
{
  district: "Palakkad",
  city: "Ottapalam",
  name: "Sevana Hospital",
  address: "Ottapalam, Palakkad",
  emergency: true,
  map: "https://maps.google.com/?q=Sevana+Hospital+Ottapalam",
  mainContact: "0466-2245000",
  departments: {
    "General Medicine": "0466-2245111",
    "Emergency": "0466-2245999"
  }
},
{
  district: "Palakkad",
  city: "Chittur",
  name: "Taluk Hospital Chittur",
  address: "Chittur, Palakkad",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Chittur",
  mainContact: "04923-222500",
  departments: {
    "General Medicine": "04923-222511",
    "Emergency": "04923-222599"
  }
},
{
  district: "Palakkad",
  city: "Mannarkkad",
  name: "KIMS Al Shifa Hospital",
  address: "Perinthalmanna Road, Mannarkkad",
  emergency: true,
  map: "https://maps.google.com/?q=KIMS+Al+Shifa+Mannarkkad",
  mainContact: "04924-223000",
  departments: {
    "Cardiology": "0492-4251000",
    "Neurology": "0492-4251111",
    "Orthopedics": "0492-4251222",
    "Psychiatry": "0492-4251333",
    "Dermatology": "0492-4251444",
    "General Medicine": "0492-4251555",
    "Emergency": "0492-4251999"
  }
},
{
  district: "Palakkad",
  city: "Shoranur",
  name: "Kulappully Medical Centre",
  address: "Shoranur, Palakkad",
  emergency: true,
  map: "https://maps.google.com/?q=Kulappully+Medical+Centre",
  mainContact: "0466-2221234",
  departments: {
    "General Medicine": "0466-2221111",
    "Emergency": "0466-2221999"
  }
},
{
  district: "Palakkad",
  city: "Alathur",
  name: "Taluk Headquarters Hospital Alathur",
  address: "Alathur, Palakkad",
  emergency: true,
  map: "https://maps.google.com/?q=THQ+Hospital+Alathur",
  mainContact: "04922-222400",
  departments: {
    "General Medicine": "04922-222411",
    "Emergency": "04922-222499"
  }
},
{
  district: "Malappuram",
  city: "Perinthalmanna",
  name: "KIMS Al Shifa Hospital",
  address: "Perinthalmanna, Malappuram",
  emergency: true,
  map: "https://maps.google.com/?q=KIMS+Al+Shifa+Hospital+Perinthalmanna",
  mainContact: "04933-300000",
  departments: {
    "Cardiology": "04933-300111",
    "Emergency": "04933-300999"
  }
},
{
  district: "Malappuram",
  city: "Kottakkal",
  name: "MIMS Hospital",
  address: "Kottakkal, Malappuram",
  emergency: true,
  map: "https://maps.google.com/?q=MIMS+Hospital+Kottakkal",
  mainContact: "0483-2809100",
  departments: {
    "Cardiology": "0483-2809000",
    "Neurology": "0483-2809111",
    "Orthopedics": "0483-2809222",
    "Psychiatry": "0483-2809333",
    "Dermatology": "0483-2809444",
    "General Medicine": "0483-2809555",
    "Emergency": "0483-2809999"
  }
},
{
  district: "Malappuram",
  city: "Tirur",
  name: "City Hospital Tirur",
  address: "Tirur, Malappuram",
  emergency: true,
  map: "https://maps.google.com/?q=City+Hospital+Tirur",
  mainContact: "0494-2424000",
  departments: {
    "General Medicine": "0494-2424111",
    "Emergency": "0494-2424999"
  }
},
{
  district: "Malappuram",
  city: "Nilambur",
  name: "District Hospital Nilambur",
  address: "Nilambur, Malappuram",
  emergency: true,
  map: "https://maps.google.com/?q=District+Hospital+Nilambur",
  mainContact: "04931-220500",
  departments: {
    "General Medicine": "04931-220511",
    "Emergency": "04931-220599"
  }
},
{
  district: "Malappuram",
  city: "Ponnani",
  name: "Taluk Hospital Ponnani",
  address: "Ponnani, Malappuram",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Ponnani",
  mainContact: "0494-2665000",
  departments: {
    "General Medicine": "0494-2665111",
    "Emergency": "0494-2665999"
  }
},
{
  district: "Kozhikode",
  city: "Mavoor Road",
  name: "IQRAA International Hospital",
  address: "Malaparamba, Kozhikode",
  emergency: true,
  map: "https://maps.google.com/?q=IQRAA+Hospital+Kozhikode",
  mainContact: "0495-2379100",
  departments: {
    "Cardiology": "0495-2371000",
    "Neurology": "0495-2371111",
    "Orthopedics": "0495-2371222",
    "Psychiatry": "0495-2371333",
    "Dermatology": "0495-2371444",
    "General Medicine": "0495-2371555",
    "Emergency": "0495-2371999"
  }
},
{
  district: "Kozhikode",
  city: "West Hill",
  name: "Malabar Hospital",
  address: "West Hill, Kozhikode",
  emergency: true,
  map: "https://maps.google.com/?q=Malabar+Hospital+Kozhikode",
  mainContact: "0495-2767777",
  departments: {
    "General Medicine": "0495-2767111",
    "Emergency": "0495-2767999"
  }
},
{
  district: "Kozhikode",
  city: "Feroke",
  name: "KMCT Medical College Hospital",
  address: "Mukkam, Kozhikode",
  emergency: true,
  map: "https://maps.google.com/?q=KMCT+Medical+College+Kozhikode",
  mainContact: "0495-2295087",
  departments: {
    "Cardiology": "0495-2295111",
    "Emergency": "0495-2295999"
  }
},
{
  district: "Kozhikode",
  city: "Vadakara",
  name: "Co-operative Hospital Vadakara",
  address: "Vadakara, Kozhikode",
  emergency: true,
  map: "https://maps.google.com/?q=Cooperative+Hospital+Vadakara",
  mainContact: "0496-2521111",
  departments: {
    "General Medicine": "0496-2521222",
    "Emergency": "0496-2521999"
  }
},
{
  district: "Kozhikode",
  city: "Ramanattukara",
  name: "CHC Ramanattukara",
  address: "Ramanattukara, Kozhikode",
  emergency: true,
  map: "https://maps.google.com/?q=CHC+Ramanattukara",
  mainContact: "0495-2444000",
  departments: {
    "General Medicine": "0495-2444111",
    "Emergency": "0495-2444999"
  }
},
{
  district: "Wayanad",
  city: "Mananthavady",
  name: "District Hospital Mananthavady",
  address: "Mananthavady, Wayanad",
  emergency: true,
  map: "https://maps.google.com/?q=District+Hospital+Mananthavady",
  mainContact: "04935-240200",
  departments: {
    "General Medicine": "04935-240211",
    "Emergency": "04935-240299"
  }
},
{
  district: "Wayanad",
  city: "Sulthan Bathery",
  name: "Taluk Hospital Sulthan Bathery",
  address: "Sulthan Bathery, Wayanad",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Sulthan+Bathery",
  mainContact: "04936-222500",
  departments: {
    "General Medicine": "04936-222511",
    "Emergency": "04936-222599"
  }
},
{
  district: "Wayanad",
  city: "Kalpetta",
  name: "Leo Hospital",
  address: "Kalpetta, Wayanad",
  emergency: true,
  map: "https://maps.google.com/?q=Leo+Hospital+Kalpetta",
  mainContact: "04936-202222",
  departments: {
    "Cardiology": "0493-6201000",
    "Neurology": "0493-6201111",
    "Orthopedics": "0493-6201222",
    "Psychiatry": "0493-6201333",
    "Dermatology": "0493-6201444",
    "General Medicine": "0493-6201555",
    "Emergency": "0493-6201999"
  }
},
{
  district: "Wayanad",
  city: "Meppadi",
  name: "Community Health Centre Meppadi",
  address: "Meppadi, Wayanad",
  emergency: true,
  map: "https://maps.google.com/?q=CHC+Meppadi",
  mainContact: "04936-282300",
  departments: {
    "General Medicine": "04936-282311",
    "Emergency": "04936-282399"
  }
},
{
  district: "Wayanad",
  city: "Panamaram",
  name: "Taluk Hospital Panamaram",
  address: "Panamaram, Wayanad",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Panamaram",
  mainContact: "04935-221400",
  departments: {
    "General Medicine": "04935-221411",
    "Emergency": "04935-221499"
  }
},
{
  district: "Kannur",
  city: "Thalassery",
  name: "Indira Gandhi Co-operative Hospital",
  address: "Thalassery, Kannur",
  emergency: true,
  map: "https://maps.google.com/?q=IG+Cooperative+Hospital+Thalassery",
  mainContact: "0490-2345000",
  departments: {
    "Cardiology": "0490-2321000",
    "Neurology": "0490-2321111",
    "Orthopedics": "0490-2321222",
    "Psychiatry": "0490-2321333",
    "Dermatology": "0490-2321444",
    "General Medicine": "0490-2321555",
    "Emergency": "0490-2321999"
  }
},
{
  district: "Kannur",
  city: "Payyannur",
  name: "Payyannur Co-operative Hospital",
  address: "Payyannur, Kannur",
  emergency: true,
  map: "https://maps.google.com/?q=Payyannur+Cooperative+Hospital",
  mainContact: "04985-203000",
  departments: {
    "General Medicine": "04985-203111",
    "Emergency": "04985-203999"
  }
},
{
  district: "Kannur",
  city: "Taliparamba",
  name: "Taluk Hospital Taliparamba",
  address: "Taliparamba, Kannur",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Taliparamba",
  mainContact: "0460-2202000",
  departments: {
    "General Medicine": "0460-2202111",
    "Emergency": "0460-2202999"
  }
},
{
  district: "Kannur",
  city: "Iritty",
  name: "THQ Hospital Iritty",
  address: "Iritty, Kannur",
  emergency: true,
  map: "https://maps.google.com/?q=THQ+Hospital+Iritty",
  mainContact: "0490-2494000",
  departments: {
    "General Medicine": "0490-2494111",
    "Emergency": "0490-2494999"
  }
},
{
  district: "Kannur",
  city: "Mattannur",
  name: "Mattannur Co-operative Hospital",
  address: "Mattannur, Kannur",
  emergency: true,
  map: "https://maps.google.com/?q=Mattannur+Cooperative+Hospital",
  mainContact: "0490-2473000",
  departments: {
    "General Medicine": "0490-2473111",
    "Emergency": "0490-2473999"
  }
},
{
  district: "Kasaragod",
  city: "Kanhangad",
  name: "District Hospital Kanhangad",
  address: "Kanhangad, Kasaragod",
  emergency: true,
  map: "https://maps.google.com/?q=District+Hospital+Kanhangad",
  mainContact: "0467-2204000",
  departments: {
    "Cardiology": "0467-2201000",
    "Neurology": "0467-2201111",
    "Orthopedics": "0467-2201222",
    "Psychiatry": "0467-2201333",
    "Dermatology": "0467-2201444",
    "General Medicine": "0467-2201555",
    "Emergency": "0467-2201999"
  }
},
{
  district: "Kasaragod",
  city: "Uppala",
  name: "Taluk Hospital Uppala",
  address: "Uppala, Kasaragod",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Uppala",
  mainContact: "04998-241200",
  departments: {
    "General Medicine": "04998-241211",
    "Emergency": "04998-241299"
  }
},
{
  district: "Kasaragod",
  city: "Cheruvathur",
  name: "CHC Cheruvathur",
  address: "Cheruvathur, Kasaragod",
  emergency: true,
  map: "https://maps.google.com/?q=CHC+Cheruvathur",
  mainContact: "0467-2265000",
  departments: {
    "General Medicine": "0467-2265111",
    "Emergency": "0467-2265999"
  }
},
{
  district: "Kasaragod",
  city: "Badiadka",
  name: "Taluk Hospital Badiadka",
  address: "Badiadka, Kasaragod",
  emergency: true,
  map: "https://maps.google.com/?q=Taluk+Hospital+Badiadka",
  mainContact: "04998-284400",
  departments: {
    "General Medicine": "04998-284411",
    "Emergency": "04998-284499"
  }
},
{
  district: "Kasaragod",
  city: "Periya",
  name: "Central University Health Centre",
  address: "Periya, Kasaragod",
  emergency: true,
  map: "https://maps.google.com/?q=Central+University+Health+Centre+Periya",
  mainContact: "0467-2309000",
  departments: {
    "General Medicine": "0467-2309111",
    "Emergency": "0467-2309999"
  }
}
];
const districtSelect = document.getElementById("district");
const citySelect = document.getElementById("city");
const symptomSelect = document.getElementById("symptom");
const checkBtn = document.getElementById("check-btn");
const symptomConfig = {
  chest_pain: {
    label: "Chest Pain",
    severity: "high",
    departments: ["Cardiology"],
    message: "Chest pain may be heart related. Immediate evaluation is recommended."
  },
  breathing_difficulty: {
    label: "Breathing Difficulty",
    severity: "high",
    departments: ["Emergency"],
    message: "Breathing difficulty requires urgent medical care."
  },
  severe_bleeding: {
    label: "Severe Bleeding",
    severity: "high",
    departments: ["Emergency"],
    message: "Apply pressure and go to nearest hospital immediately."
  },
  eye_injury: {
    label: "Eye Injury",
    severity: "medium",
    departments: ["Ophthalmology"],
    message: "Consult an eye specialist as soon as possible."
  },
  high_fever: {
    label: "High Fever",
    severity: "low",
    departments: ["General Medicine"],
    message: "Consult a general physician."
  },
  severe_headache: {
    label: "Severe Headache",
    severity: "medium",
    departments: ["Neurology"],
    message: "Persistent severe headache should be evaluated."
  },
  sudden_weakness: {
    label: "Sudden Weakness",
    severity: "high",
    departments: ["Emergency", "Neurology"],
    message: "Sudden weakness may indicate stroke. Seek emergency care immediately."
  },
  abdominal_pain_severe: {
    label: "Severe Abdominal Pain",
    severity: "medium",
    departments: ["General Medicine"],
    message: "Severe abdominal pain requires medical evaluation."
  },
  fractures_or_broken_bone: {
    label: "Fracture / Broken Bone",
    severity: "medium",
    departments: ["Orthopedics"],
    message: "Immobilize the area and visit an orthopedic specialist."
  },
  burns_major: {
    label: "Major Burns",
    severity: "high",
    departments: ["Emergency"],
    message: "Major burns require immediate emergency treatment."
  },
  vomiting_persistent: {
    label: "Persistent Vomiting",
    severity: "low",
    departments: ["General Medicine"],
    message: "Persistent vomiting should be checked by a physician."
  },
  mental_health_crisis: {
    label: "Mental Health Crisis",
    severity: "high",
    departments: ["Psychiatry"],
    message: "Seek immediate psychiatric support."
  },
  skin_rash_severe: {
    label: "Severe Skin Rash",
    severity: "low",
    departments: ["Dermatology"],
    message: "Consult a dermatologist."
  }
};
Object.entries(symptomConfig).forEach(([key, value]) => {
  const option = document.createElement("option");
  option.value = key;
  option.textContent = value.label;
  symptomSelect.appendChild(option);
});
const districts = [...new Set(keralaHospitals.map(h => h.district))].sort();

districts.forEach(district => {
  const option = document.createElement("option");
  option.value = district;
  option.textContent = district;
  districtSelect.appendChild(option);
});
districtSelect.addEventListener("change", function () {
  const selectedDistrict = this.value;
  citySelect.innerHTML = '<option value="">-- Select City --</option>';
  const cities = keralaHospitals
    .filter(h => h.district === selectedDistrict)
    .map(h => h.city);
  const uniqueCities = [...new Set(cities)].sort();
  uniqueCities.forEach(city => {
    const option = document.createElement("option");
    option.value = city;
    option.textContent = city;
    citySelect.appendChild(option);
  });
});
checkBtn.addEventListener("click", function () {
  const symptomKey = symptomSelect.value;
  const district = districtSelect.value;
  const city = citySelect.value;
  if (!symptomKey || !district) {
    alert("Please select district and symptom.");
    return;
  }
  const config = symptomConfig[symptomKey];
  document.getElementById("alert-section").style.display = "block";
  document.getElementById("department-section").style.display = "block";
  document.getElementById("hospital-section").style.display = "block";
  const alertBox = document.getElementById("alert-box");
  alertBox.innerHTML = config.message;
  if (config.severity === "high") {
    alertBox.innerHTML += `
      <br><br>
      <a href="tel:108" style="color:red;font-weight:bold;">
      🚨 Call Ambulance 108 Immediately</a>
    `;
  }
  document.getElementById("department-result").innerHTML =
    config.departments.map(d => `<strong>${d}</strong>`).join(" , ");
  let filtered = keralaHospitals.filter(h => {
    const districtMatch = h.district === district;
    const cityMatch = city ? h.city === city : true;
    const departmentMatch = config.departments.some(
      dept => h.departments[dept]
    );
    return districtMatch && cityMatch && departmentMatch;
  });
  if (config.severity === "high") {
    filtered.sort((a, b) => b.emergency - a.emergency);
  }
  displayHospitals(filtered, config.departments);
});
function displayHospitals(hospitals, departments) {
  const hospitalList = document.getElementById("hospital-list");
hospitalList.innerHTML = "";
  if (hospitals.length === 0) {
    hospitalList.innerHTML = `
      <p style="color:red;font-weight:bold;">
      No matching hospitals found. Please call 108 immediately.</p>
    `;
    return;
  }
  let html = "";
  hospitals.forEach(h => {
    const deptMatches = departments
      .filter(d => h.departments[d])
      .map(d => `
        <p>☎️ <strong>${d}:</strong>
        <a href="tel:${h.departments[d]}">${h.departments[d]}</a></p>
      `).join("");
    html += `
      <div class="hospital-card">
        <h3>${h.name}</h3>
        <p> ${h.address}</p>
        ${h.emergency ? "<p style='color:red;font-weight:bold;'>🚑 24x7 Emergency Available</p>" : ""}
        <hr>
        <p>📞 <strong>Main:</strong>
        <a href="tel:${h.mainContact}">${h.mainContact}</a></p>
        ${deptMatches}
        <a href="${h.map}" target="_blank" class="map-btn">
        Open in Google Maps</a>
      </div>
    `;
  });
  hospitalList.innerHTML = html;
}

# Commits
AI tools used- ChatGPT , Gemini


