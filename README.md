# EventFlow AI — Intelligent Crowd Detection & Mega-Event Management

## 1. Project Overview

EventFlow AI is an AI-powered mega-event management and crowd orchestration system designed to monitor stadium entry, detect vehicles, manage visitor information, and support centralized crowd management.

The system consists of two computer vision models and three interconnected applications:

- **Face Detection System:** Detects faces from stadium-entry video feeds and supports visitor counting and unique-visitor tracking.
- **Vehicle Number Plate Recognition System:** Detects vehicles and extracts registration numbers using computer vision and Optical Character Recognition (OCR).
- **Crew Application:** Provides on-ground personnel with relevant crowd information to assist with entry management and crowd monitoring.
- **Visitor Application:** Provides attendees with event information, transport routes, hotel recommendations, parking options, and management notifications.
- **Manager Dashboard:** Provides centralized monitoring, time-based crowd simulation, capacity analysis, risk alerts, recommendations, and what-if scenario analysis.

The prototype uses trained computer vision models and simulated event data to demonstrate how different event-management operations can work together.

## 2. System Components

### A. AI-Based Face Detection

**Purpose:** Monitor incoming visitors at stadium entry points.

**Core functionality:**
- Detect faces in video frames using a trained YOLOv8-based model.
- Process entry footage and generate annotated video outputs.
- Record detection results for analysis.
- Support visitor counting and unique-visitor tracking, subject to the configured tracking or face-matching logic.
- Provide crowd-related information to the event-management system.

**Technology:** Python, YOLOv8, computer vision, video processing, CSV and database-based result storage.

**Output:** Annotated video, detection records, and crowd-count information.

*Technical note: Face detection identifies visible faces; it does not, by itself, establish whether two detections belong to the same person. Reliable unique-visitor counting requires an additional tracking or re-identification mechanism.*

### B. Vehicle Detection and Number Plate Recognition

**Purpose:** Support vehicle monitoring and parking management around the event venue.

**Core functionality:**
- Detect vehicles in images or video.
- Locate vehicle number plates.
- Extract registration text using OCR.
- Store detection and recognition results.
- Support vehicle verification and parking-related workflows.

**Technology:** Python, YOLOv8, OCR, SQL-based database operations, and a web application structure using templates and static assets.

**Output:** Detected vehicles, recognized number plates, and associated records.

*Technical note: Number plate recognition accuracy depends on image quality, lighting, plate visibility, and the OCR implementation.*

### C. Crew Application

**Purpose:** Give on-ground event crew access to operational crowd information.

**Core functionality:**
- Display crowd and entry-related information.
- Help crew members monitor visitor movement and congestion.
- Provide information needed for entry management and operational coordination.

The crew interface acts as an operational information layer between the centralized manager dashboard and personnel working at the venue.

### D. Visitor Application

**Purpose:** Provide event attendees with personalized information and guidance.

**Core functionality:**
- Display event information and recommendations.
- Present available transport routes and simulated congestion.
- Show hotel options and room availability.
- Display stadium and nearby community parking options.
- Deliver notifications and manager-issued recommendations.
- Allow users to respond to recommendations where supported.

The visitor application helps attendees make informed decisions while allowing their simulated choices to influence resource demand within the Digital Twin.

### E. Central Manager Dashboard

**Purpose:** Provide a unified command center for event monitoring and decision-making.

**Core functionality:**
- Monitor crowd distribution across event zones.
- Visualize crowd density, routes, transport, hotels, and parking.
- Track stadium occupancy, gate conditions, and resource utilization.
- Switch between simulated time intervals to inspect changing conditions.
- Generate alerts for capacity pressure and potential bottlenecks.
- Run what-if scenarios involving visitor surges, route closures, weather changes, and transport disruptions.
- Provide recommendations for redistributing visitors and managing resources.
- Use an AI Event Copilot to answer operational questions and explain potential responses.

The dashboard combines operational visualization, synthetic simulation, and AI-assisted decision support in one interface.

## 3. Technology Stack

| Technology | Purpose |
|---|---|
| Python | Computer vision, detection pipelines, and application logic |
| YOLOv8n | Lightweight object detection model used in the project |
| OCR | Extracting text from detected vehicle number plates |
| SQL | Database schema and structured data operations |
| SQLite-compatible database files | Local storage of detection results, as suggested by the `.db` files |
| CSV | Exporting and analysing detection results |
| HTML templates and static assets | Web interface structure in the vehicle-detection application |
| `requirements.txt` | Python dependency specification |
| MP4 video processing | Testing detection pipelines and reviewing annotated results |

The exact OCR engine, web framework, database configuration, and frontend framework should be documented after checking the implementation and dependency files.

## 4. Data Processing Workflow

### Face Detection

Entry video → Frame processing → Face detection → Detection/tracking logic → Result storage → Crowd monitoring

### Number Plate Recognition

Vehicle footage → Vehicle detection → Number plate localization → OCR text extraction → Database storage → Vehicle/parking workflow

### Event Management

Synthetic event data → Digital Twin state → Crowd and resource monitoring → Prediction and risk analysis → What-if simulation and optimization → Manager recommendations → Visitor response → Updated simulation state

## 5. Project Objectives

- Improve visibility into crowd movement and entry conditions.
- Support vehicle and number plate monitoring.
- Connect visitor-facing guidance with centralized event management.
- Identify potential capacity bottlenecks before they become critical.
- Simulate how changes in visitor demand affect transport, hotels, parking, and stadium operations.
- Support data-informed decisions through AI-assisted analysis and recommendations.

## 6. Prototype Scope

The current project combines computer vision components with a synthetic event-management environment. The trained detection models process visual inputs, while the manager and visitor applications demonstrate the broader operational workflow.

Synthetic crowd counts, resource availability, user responses, and future predictions should be clearly distinguished from measurements obtained from real deployed cameras, ticketing systems, transport operators, hotels, or parking providers.

EventFlow AI is intended as a decision-support prototype; operational deployment would require validated models, integrated data sources, security controls, performance testing, and appropriate privacy safeguards.
