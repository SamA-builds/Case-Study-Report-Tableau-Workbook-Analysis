# Hotel Management Analytics (Tableau)

An interactive Tableau workbook for monitoring hotel operations, occupancy, guest demographics, and service performance. The dashboards combine reservation, room, customer, and ticket data into a single analytical model designed for both real-time operational monitoring and year-over-year performance review.

## Overview

This project models a hotel's operational data into a star schema and builds a set of connected dashboards that answer questions across several areas of the business:

- How full is the hotel today, and how does that compare to the same date last year?
- How is occupancy trending across the year?
- Who are the hotel's guests, by country, age, and gender?
- What kinds of service tickets are being raised, and how are they resolved?
- How do reservation activities flow from request to confirmation?

A key feature is a **simulated "today" parameter**, which lets users pick any date within the data range and drive every dashboard as if that were the current day. This supports daily operational decisions as well as scenario exploration.

## Data Model

The workbook connects to the Excel source `HotelManagement_V2.xlsx` and integrates six tables using the Reservations table as the central fact table in a star schema.

| Table | Rows (approx.) | Role | Join Key |
| --- | --- | --- | --- |
| Reservations | 2,286 | Central fact table | (fact) |
| Room Data | 16 | Room attributes and pricing | Room Number |
| Customers | 900 | Guest demographics | Customer Number |
| Reservation Activities | 13,596 | Booking lifecycle events | Reservation ID |
| Tickets | 457 | Service and maintenance requests | Reservation ID |
| Ticket Activities | 1,371 | Ticket lifecycle events | Ticket ID |

Joins are implemented as logical left joins, allowing analysis across bookings, demographics, and service resolution from a single model.

## Dashboards and Analysis

### Utilization and Occupancy
- Line chart of reservation trend by month to visualize occupancy over time.
- Horizontal bar chart of today's occupancy segmented by room category (Single, Double, Suite).
- KPIs for rooms occupied today, total rooms, and occupancy on the same day last year.

### Simulated "Today" Parameter
- A `Sim Today` parameter (dated range across the dataset) implemented as a slider.
- Drives current-day occupancy, category filtering, and year-over-year comparisons.
- Enables operational teams to explore any specific date within range.

### Year-over-Year Comparison
- Side-by-side metrics comparing the simulated date to the same date one year prior.
- Occupancy count this year vs. last year, total rooms, and YoY percentage change.
- Difference expressed in basis points (bps) for financial-style reporting, with conditional formatting to highlight improvement or decline.

### Tickets and Service Performance
- Bubble chart of tickets by category (Housekeeping, Security & Safety, Technical Issues) to assess department workload.
- Response and resolution time fields support service-level analysis.

### Reservation Activities
- Bar chart of activity frequency across the booking lifecycle (Requested, Confirmed, Deposit Received, and others).
- Stacked monthly trend chart to reveal seasonal workflow and peak operations.

### Customer Analysis
- Gender distribution.
- Treemap of customer count by country.
- Age distribution across defined age bins for demographic and marketing insight.

## Tools and Techniques

- **Tableau** for data modeling, dashboard design, and interactivity.
- **Star schema modeling** with logical left joins across six tables.
- **Parameters and calculated fields** to power the simulated-date logic and offset "last year" values by 365 days.
- **KPI design** including YoY percentage and basis-point calculations with conditional formatting.
- **Multiple chart types** including line, bar, bubble, treemap, and stacked visuals.

Dashboard screenshots (`Today reservation.png`, `w1.png` through `w4.png`) are included for a quick look. See `Report.docx` for the full case study write-up.
