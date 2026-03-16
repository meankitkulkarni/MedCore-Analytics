🏥 MedCore Analytics — Hospital Intelligence Dashboard

A browser-based, zero-backend hospital analytics dashboard that transforms patient record data into interactive, real-time visualizations.


📌 Overview
MedCore Analytics is a single-page application (SPA) built with vanilla HTML, CSS, and JavaScript. It ingests structured patient records in JSON format and renders a rich analytics dashboard featuring KPI cards, 10+ interactive charts, and a fully searchable, sortable patient registry — all without any server, framework, or database.

🗂️ Project Structure
Hospital_Data_Analytics/
├── index.html        # Full SPA — UI layout, styles, and all JS logic
├── app.js            # (reserved / entry point placeholder)
├── style.css         # (reserved / additional styles placeholder)
└── records.json      # Sample dataset — 20 patient records

🧱 Architecture Block Diagram
┌─────────────────────────────────────────────────────────────────┐
│                        BROWSER (Client-Side SPA)                │
│                                                                 │
│  ┌──────────────┐    ┌───────────────────────────────────────┐  │
│  │  DATA INPUT  │    │           CORE LOGIC (app.js)         │  │
│  │              │    │                                       │  │
│  │ ┌──────────┐ │    │  ┌─────────────┐  ┌───────────────┐   │  │
│  │ │ Upload   │─┼────┼─▶│  filterTable│  │  renderKPIs  │   │  │
│  │ │ JSON     │ │    │  │  sortTable  │  │  buildCharts  │   │  │
│  │ └──────────┘ │    │  │  goPage     │  │  updateCharts │   │  │
│  │              │    │  └──────┬──────┘  └──────┬────────┘   │  │
│  │ ┌──────────┐ │    │         │                │            │  │
│  │ │ Sample   │─┼────┼─────────┴────────────────┘            │  │
│  │ │ Data     │ │    │                  │                    │  │
│  │ └──────────┘ │    │         ┌────────▼────────┐           │  │
│  └──────────────┘    │         │  allData / filteredData     │  │
│                      │         │  (in-memory state)          │  │
│  ┌──────────────┐    │         └────────┬────────┘           │  │
│  │   FILTERS    │    │                  │                    │  │
│  │              │    └──────────────────┼────────────────────┘  │
│  │ 🔍 Search    │                       │                       │
│  │ 🏥 Dept.    ├───────────────────────┤                        │
│  │ ⚠️  Severity │                       │                       │
│  └──────────────┘                       ▼                       │
│                      ┌─────────────────────────────────────┐    │
│                      │           RENDER LAYER              │    │
│                      │                                     │    │
│          ┌───────────┴──────────┐   ┌─────────────────┐    │    │
│          │    KPI CARDS         │   │  Chart.js v4     │   │    │
│          │  • Total Patients    │   │  • Bar / Doughnut│   │    │
│          │  • Avg Length of Stay│   │  • Line / Radar  │   │    │
│          │  • Total Cost        │   │  • Scatter / Hist│   │    │
│          │  • Readmission Rate  │   └─────────────────┘    │    │
│          └──────────────────────┘                          │    │
│                      │                                     │    │
│          ┌───────────┴──────────┐                          │    │
│          │   PATIENT TABLE      │                          │    │
│          │  Search │ Sort │ Page│                          │    │
│          │  Export │ Delete     │                          │    │
│          └──────────────────────┘                          │    │
│                      └─────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────┘

✨ Features
📊 KPI Summary Cards
Displays at-a-glance metrics computed from the active dataset:

Total Patients
Average Length of Stay
Total Treatment Cost
Insurance Coverage Rate
Readmission Rate
Severity Breakdown

📈 Charts & Visualizations (Powered by Chart.js v4)
SectionChartTypePatient AnalyticsAdmissions by DepartmentBarPatient AnalyticsSeverity DistributionDoughnutFinancial & ClinicalCost vs CoverageGrouped BarFinancial & ClinicalGender DistributionPieFinancial & ClinicalRoom Type UsageDoughnutTrend & DistributionMonthly Admissions TrendLineTrend & DistributionAge Distribution HistogramBarTrend & DistributionLength of Stay by DepartmentBox/BarTrend & DistributionCost vs Length of StayScatterTrend & DistributionReadmission by DepartmentRadar
🗃️ Patient Records Table

Full-text search across patient name and ID
Sort by any column (ID, Name, Age, Department, Severity, Cost, LOS)
Pagination with configurable rows-per-page
Per-row delete functionality
Export filtered results as JSON

🎛️ Filters

Filter by Department (Cardiology, Neurology, Oncology, etc.)
Filter by Severity (Critical, High, Medium, Low)
All charts and KPIs update reactively on filter change

🔧 Data Management

Upload a custom .json dataset
Load sample data (built-in 20 patient demo dataset)
Clear all data to reset the dashboard
Live clock display
Toast notifications for user actions


📦 Data Schema
The dashboard expects a JSON file in the following format:
json{
  "hospital": {
    "name": "MedCore General Hospital",
    "location": "New York, NY",
    "established": 1987,
    "beds": 850,
    "departments": 24
  },
  "metadata": {
    "totalRecords": 20,
    "exportDate": "2024-04-30",
    "version": "2.1.0",
    "dataSource": "Hospital Management Information System"
  },
  "records": [
    {
      "id": "P-001",
      "name": "James Thornton",
      "age": 54,
      "gender": "Male",
      "bloodType": "A+",
      "department": "Cardiology",
      "admissionDate": "2024-01-05",
      "dischargeDate": "2024-01-12",
      "diagnosis": "Acute Myocardial Infarction",
      "severity": "Critical",
      "status": "Discharged",
      "doctor": "Dr. Sarah Chen",
      "treatmentCost": 24500,
      "insuranceCovered": 20000,
      "roomType": "ICU",
      "readmission": false,
      "lengthOfStay": 7,
      "labResults": {
        "hemoglobin": 11.2,
        "whiteBloodCells": 9800,
        "platelets": 210000,
        "glucose": 145,
        "cholesterol": 238
      },
      "vitals": {
        "heartRate": 95,
        "bloodPressure": "148/92",
        "temperature": 98.9,
        "oxygenSaturation": 94
      },
      "medications": ["Aspirin", "Atorvastatin", "Metoprolol", "Lisinopril"]
    }
  ]
}

🚀 Getting Started
No installation or build step required.
bash# Clone or download the project
git clone https://github.com/your-username/hospital-data-analytics.git
cd hospital-data-analytics

# Open directly in browser
open index.html
Or simply double-click index.html to launch in your default browser.

Tip: For the best experience, use a modern browser (Chrome, Firefox, Edge).


🛠️ Tech Stack
TechnologyPurposeHTML5 / CSS3Layout and stylingVanilla JavaScript (ES6+)All data logic and interactivityChart.js v4.4.1Chart renderingGoogle Fonts (DM Sans, DM Serif, JetBrains Mono)TypographyJSONData format
No frameworks. No build tools. No backend. No dependencies to install.

🎨 Design

Dark-themed UI (#080c14 base) with blue/teal accent palette
Glassmorphism card styling with backdrop-filter
Smooth CSS animations on load (animate-in)
Fully responsive layout (grid adapts to screen size)
Color-coded severity levels: Critical (red), High (orange), Medium (yellow), Low (green)


📁 Sample Dataset
records.json ships with 20 anonymized patient records from MedCore General Hospital (demo data), spanning departments including Cardiology, Neurology, Oncology, Orthopedics, and Pediatrics.

🔮 Future Improvements

 Add date-range filter for admissions
 Support CSV import in addition to JSON
 Add print / PDF export for reports
 Persist data across sessions using localStorage
 Expand dataset with 100+ synthetic records

Built with ❤️ for healthcare data transparency by Ankit Kulkarni.
