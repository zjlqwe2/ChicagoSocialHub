

# Chicago Social Hub

**Chicago Social Hub** is a web application that integrates real-time and historical data from Chicago’s Divvy bike-sharing system and Yelp’s business review platform. The goal is to provide users with:

1. Real-time information about Divvy bike stations in the Chicago area (including line charts and heatmaps).  
2. Historical Divvy trip data visualization for the 4th Quarter of 2018.  
3. Yelp-based search functionality (e.g., searching for “pizza” in ZIP code “60602”).  
4. Easy data storage and retrieval with PostgreSQL and Elasticsearch.

### Tools & Technologies Used

1. **Node.js (Backend)**: Handles API routing and integration with databases.  
2. **Python (Data Collection & Processing)**: For scraping, transforming, and storing Divvy and Yelp data.  
3. **PostgreSQL**: Stores structured data like Divvy trip records and real-time docking station statuses.  
4. **Elasticsearch**: Indexes and logs real-time Divvy data and Yelp business/review data for fast search.  
5. **Angular**: Provides an interactive web frontend with charts and data visualizations.



## Overview

In **Chicago Social Hub**, we combine Divvy bike-sharing data with Yelp business information for a unified Chicago city experience:

- **Divvy**: A bike-share system in Chicago  
  - Access real-time docking station statuses  
  - Explore historical trip data (2018 Q4)  
- **Yelp**: A leading platform for restaurant and business reviews  
  - Search for businesses and reviews by keyword and ZIP code  

**Storage & Retrieval**  
- **PostgreSQL**: Storing Divvy trip data and real-time statuses  
- **Elasticsearch**: Logging every real-time Divvy status heartbeat and indexing Yelp data for fast search  

**Frontend**  
- **Angular**: Providing intuitive visualizations (line charts, heatmaps, bar charts) and search functionalities  

---

## Project Features

1. **Real-time Divvy Station Status (Line Charts & Heatmaps)**  
   - Automatically refreshed every 2 minutes  
   - Time range selection: past hour, past 24 hours, or past 7 days  

2. **Historical Divvy Trip Data**  
   - Analyzes usage patterns for weekdays (morning/evening rush) vs. weekends/holidays  
   - Bar-chart visualizations for daily/weekly/hourly trends  

3. **Yelp Business & Reviews Search**  
   - Keyword and ZIP code search (e.g., “pizza” in “60602”)  
   - Helps visitors quickly find popular Chicago-style food spots  

4. **Backend Integration**  
   - Node.js + Express REST APIs for both Divvy and Yelp data retrieval  
   - PostgreSQL for structured data  
   - Elasticsearch for logging and indexing  

5. **Frontend (Angular)**  
   - Interactive charts and data visualizations  
   - Responsive design for the real-time station status and user-friendly data display  

---

## Directory Structure

A simplified view of the core directories and files:

```
HW5_SOURCECODE_ChicagoSocialHub/
├── backend
│   ├── node_modules/
│   ├── package-lock.json
│   ├── package.json
│   ├── server.js
│   └── testJsCode.js
├── backend-build-divvy-quarter-trips
│   ├── .ipynb_checkpoints/
│   ├── Divvy_Trips_2018_Q4.csv
│   └── divvy_trips.ipynb
├── backend-build-divvy-status
│   ├── .ipynb_checkpoints/
│   ├── divvy_real-time_status.ipynb
│   └── divvy_stations_status.csv
├── backend-build-yelp-reviews
│   ├── .ipynb_checkpoints/
│   ├── chicago_yelp_reviews.json
│   └── ChicagpSocialHub-Yelp.ipynb
├── frontend
│   ├── .angular/
│   ├── node_modules/
│   ├── src/
│   ├── angular.json
│   ├── debug.log
│   ├── package-lock.json
│   ├── package.json
│   ├── README.md
│   ├── tsconfig.json
│   └── tslint.json
└── ...
```

---

## Modules & Descriptions

### 1. Backend (Node.js)

- **Directory**: `backend/`
- **Purpose**:  
  - Host a Node.js + Express server to provide RESTful APIs for Divvy and Yelp data.  
  - Integrate with PostgreSQL (for storing Divvy data) and Elasticsearch (for logging data).  
- **Key Files**:  
  - `server.js` — The main entry point for the Express server.  
  - `testJsCode.js` — Example/test JS file for debugging or demonstration.  
- **Dependencies**:  
  - `express`, `pg` (or `pg-promise`) for PostgreSQL, `elasticsearch` (optional if used here), etc.

### 2. backend-build-divvy-quarter-trips

- **Directory**: `backend-build-divvy-quarter-trips/`
- **Purpose**:  
  - Import historical Divvy Q4 2018 trip data from `Divvy_Trips_2018_Q4.csv` into PostgreSQL.  
  - Analyze or preprocess trip data (e.g., daily, hourly usage).  
- **Key Files**:  
  - `divvy_trips.ipynb` — Jupyter Notebook to load the CSV data, transform it, and store it in PostgreSQL.  
  - `Divvy_Trips_2018_Q4.csv` — Official Divvy data for 2018 Q4.  
- **Dependencies**:  
  - `psycopg2` for PostgreSQL connectivity, `pandas` for CSV reading, etc.

### 3. backend-build-divvy-status

- **Directory**: `backend-build-divvy-status/`
- **Purpose**:  
  - Collect real-time Divvy station status every 2 minutes (heartbeat).  
  - Store each real-time record into PostgreSQL and log to Elasticsearch.  
  - Potential for generating real-time line charts and heatmaps on the frontend.  
- **Key Files**:  
  - `divvy_real-time_status.ipynb` — Jupyter Notebook to schedule or perform the 2-minute heartbeat retrieval.  
  - `divvy_stations_status.csv` — Example or initial dataset for station references.  
- **Dependencies**:  
  - `requests` or another HTTP library for calling Divvy API  
  - `psycopg2` for PostgreSQL  
  - `elasticsearch` for logging

### 4. backend-build-yelp-reviews

- **Directory**: `backend-build-yelp-reviews/`
- **Purpose**:  
  - Fetch Yelp business listings and reviews for the Chicago downtown area.  
  - Store the results in Elasticsearch for fast indexing and searching.  
- **Key Files**:  
  - `ChicagpSocialHub-Yelp.ipynb` — Contains the logic to call the Yelp API and process responses.  
  - `chicago_yelp_reviews.json` — Example output containing Yelp business or review data.  
- **Dependencies**:  
  - `yelpapi` (or official Yelp Fusion API), `requests`, `elasticsearch`

### 5. Frontend (Angular)

- **Directory**: `frontend/`
- **Purpose**:  
  - Provide the user interface, including interactive charts and search forms.  
  - Allow the user to query Divvy station statuses, heatmaps, historical data, and Yelp businesses.  
- **Key Files**:  
  - `angular.json` — Angular CLI configuration  
  - `src/` — The main Angular application source code  
  - `package.json` — Lists dependencies for the frontend  
  - `README.md` — Angular CLI–generated usage instructions  
- **Dependencies**:  
  - `@angular/core`, `@angular/cli`, plus various chart or map libraries (e.g., `ngx-charts`, `leaflet`, etc.)  

---

## Data Collection & Processing

1. **Divvy Realtime**  
   - `divvy_real-time_status.ipynb` fetches station statuses from Divvy API every 2 minutes.  
   - Stores the data in PostgreSQL and logs each status in Elasticsearch.

2. **Divvy Historical Trips**  
   - `divvy_trips.ipynb` loads the CSV (`Divvy_Trips_2018_Q4.csv`) and populates a PostgreSQL table.  
   - Allows analysis on weekly or hourly trip patterns.

3. **Yelp Reviews**  
   - `ChicagpSocialHub-Yelp.ipynb` calls the Yelp API to fetch relevant business data for Chicago downtown.  
   - Stores or indexes results into Elasticsearch for searching.

---

## How to Run

1. **Clone or Download**  
   ```bash
   git clone https://github.com/YourAccount/ChicagoSocialHub.git
   cd ChicagoSocialHub
   ```

2. **Backend Setup**  
   ```bash
   cd backend
   npm install
   npm start
   # or node server.js
   ```
   - By default, the backend will run on `http://localhost:3000/`.

3. **Python Scripts for Data**  
   - Install necessary Python packages (`pip install psycopg2 elasticsearch yelpapi ...`).  
   - For each Jupyter Notebook (e.g., `divvy_real-time_status.ipynb`), configure PostgreSQL and Elasticsearch connections as needed, then run it to start collecting data.  

4. **Frontend Setup**  
   ```bash
   cd ../frontend
   npm install
   ng serve
   ```
   - The Angular app will be accessible at `http://localhost:4200/`.  

*Tip:* For production, you might run `ng build --prod` and deploy the `dist/` folder on a production server.

---

## Dependencies & Environment

- **Node.js** >= 12 (LTS recommended)  
- **Angular CLI** 7.1.4 (compatible with Angular 7.x)  
- **Python** 3.x (3.7+ recommended)  
  - `psycopg2` (PostgreSQL)  
  - `elasticsearch` (Elasticsearch client)  
  - `yelpapi` or Yelp Fusion API  
- **PostgreSQL** 10 or 13  
- **Elasticsearch** 7.14.0 (or a compatible version)

---

## Future Work

- **Containerization**: Use Docker to containerize the entire environment (PostgreSQL, Elasticsearch, Node.js, Angular).  
- **User Authentication**: Implement login/registration and enable CRUD operations for advanced features.  
- **Additional Visualization**: Expand analytics on Divvy data—e.g., trip duration, distance, correlation with weather data.  

--- 
![image](https://github.com/user-attachments/assets/303daf27-d3c4-4bed-a353-f205a782f5ba)
