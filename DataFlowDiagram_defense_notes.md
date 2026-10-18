# Data Flow Diagram Defense Notes

## What changed

The revised diagram defines the system boundary more precisely. The Mobile/Web Application and Desktop Application are presentation-layer components developed as part of the capstone, so they are inside the **IoT Flood Forecasting and Alert System**. They are no longer shown as external entities.

The genuine external entities are:

- **Sensor Network**, which supplies sensor readings.
- **Residents / Visitors**, who request monitoring information, maintain account information, receive forecasts and alerts, and may provide distress status and location data.
- **BDRRMC Administrator**, who monitors conditions, manages sites and sensors, receives alerts and distress information, and requests reports.

## Why the rectangles were questioned

A rectangle is not an incorrect DFD symbol. In Yourdon notation, rectangles represent external entities. The issue in the earlier diagram was not simply the number of rectangles; it was that the Mobile/Web and Desktop applications were classified as external entities even though they are parts of the system.

Removing those application rectangles does not remove their functionality. Their functionality appears in Level 1 through processes such as managing accounts, delivering alerts, providing dashboards, and generating reports.

## Why Level 1 was also revised

Level 1 must be balanced with Level 0. After correcting the Level 0 system boundary, the decomposition also had to be updated so that:

- external actors communicate directly with system processes;
- no data flows run from one external entity to another;
- internal applications are represented by system functions rather than external rectangles;
- the full capstone scope includes sensor collection, forecasting, accounts, resident status, alerts, site configuration, dashboards, and reports; and
- every external input and output in Level 0 is accounted for in Level 1.

## Level 0 to Level 1 balancing checklist

| Level 0 boundary flow | Level 1 representation |
|---|---|
| Sensor Readings | Sensor Network → 1.0 Capture and Validate Sensor Readings |
| Resident Account Data | Residents / Visitors → 3.0 Manage Accounts and Resident Status |
| Resident Monitoring Requests | Residents / Visitors → 6.0 Provide Dashboards and Generate Reports |
| Distress Status and Location | Residents / Visitors → 3.0 Manage Accounts and Resident Status |
| Resident Account Status | 3.0 Manage Accounts and Resident Status → Residents / Visitors |
| Current Conditions, Forecasts, and Map Data | 6.0 Provide Dashboards and Generate Reports → Residents / Visitors |
| Alerts and Notifications | 4.0 Manage Alerts and Notifications → Residents / Visitors |
| Administrator Account Data | BDRRMC Administrator → 3.0 Manage Accounts and Resident Status |
| Management Commands | BDRRMC Administrator → 5.0 Manage Sites and Sensor Configuration |
| Dashboard and Report Requests | BDRRMC Administrator → 6.0 Provide Dashboards and Generate Reports |
| Administrator Account Status | 3.0 Manage Accounts and Resident Status → BDRRMC Administrator |
| Monitoring Dashboard and Forecast Data | 6.0 Provide Dashboards and Generate Reports → BDRRMC Administrator |
| Alerts and Reports | Alerts: Process 4.0 → Administrator; reports: Process 6.0 → Administrator |
| Resident Distress and Status Locations | 4.0 Manage Alerts and Notifications → BDRRMC Administrator |

## Suggested oral-defense explanation

> In our previous context diagram, we represented the Mobile/Web and Desktop applications as external entities. After reviewing the system boundary, we recognized that both applications belong to our presentation layer and are developed as parts of the capstone. We therefore retained only the actual external actors: the Sensor Network, Residents or Visitors, and the BDRRMC Administrator. We then revised Level 1 to preserve all Level 0 inputs and outputs and to represent the application functionality as internal processes. Rectangles are still valid for external entities; our correction concerns entity classification and system-boundary consistency.

## How to discuss the advisers' reviews

The previous version was understandable as a high-level architecture-style representation, which may explain why it passed an earlier review. The revised version applies stricter DFD rules after clarifying the system boundary. This should be presented as a refinement based on feedback, not as proof that either adviser was wrong or acting in bad faith.

## Symbol and flow rules used

- Circles represent processes.
- Rectangles represent external entities.
- Parallel/open-ended lines represent data stores.
- Solid arrows represent named data flows.
- Processes use verb phrases; data flows and stores use noun phrases.
- External entities never connect directly to other external entities or data stores.
- Data stores connect only to processes.
