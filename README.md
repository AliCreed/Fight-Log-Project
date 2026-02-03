# Fight Log Dashboard

## Project Overview
This interactive **Power BI dashboard** was designed to track and analyze personal fight-viewing habits throughout **January 2026**. The project focuses on visualizing combat sports data across multiple sports and eras, providing deep insights into fighter appearances, promotion trends, and total viewing time.

---

## Key Features & Technical Challenges

### 1. Dual-Column Fighter Search
**The Challenge:**  
Fighters are listed in two separate columns (*Fighter 1* and *Fighter 2*). Standard relationships only allow filtering on one column at a time.

**The Solution:**  
Implemented a **Disconnected Table** strategy using a DAX-generated **Fighter Leaderboard**.

**DAX Logic:**  
Created a virtual relationship using a `MATCH` measure that scans both corner columns simultaneously without duplicating fight counts.

---

### 2. Time Duration Analytics
**The Challenge:**  
Power BI does not natively sum `Duration` data types in card visuals.

**The Solution:**  
Developed a custom DAX measure to:
- Convert time values into seconds  
- Perform the aggregation  
- Re-format the result into a readable `Days:HH:MM:SS` string

---

### 3. Era-Based Categorization
**The Challenge:**  
Analyzing fights by the decade they occurred (1990s–2020s).

**The Solution:**  
Applied `FLOOR` logic in a calculated column to bucket years into 10-year intervals, enabling a chronological donut chart for era-based filtering.

---

## Data Model Architecture
- **Fact Table:** `2026` (Main fight log)  
- **Dimension Table:** `Calendar` (1–31 day mapping)  
- **Support Table:** `Fighter Leaderboard` (Disconnected DAX table for multi-column filtering)

---

## How to View
1. Download the `Fight_Dashboard.pbix` file found in this folder.  
2. Open using **Power BI Desktop**.  
3. Alternatively, refer to `Dashboard_Preview.pdf` for a static overview of the design and layout.

---

## Tools Used
- **Power BI Desktop:** Visual design and UI/UX  
- **Power Query:** Data cleaning and index generation  
- **DAX:** Advanced measures for duration summing and cross-column filtering  
- **Gemini (AI Collaborator):** Leveraged as an adaptive AI peer to troubleshoot data model architecture and optimize DAX syntax
