---
layout: default
---

<link rel="stylesheet" href="/assets/css/custom.css">

# Enhancement One
# Data Structures & Algorithms

This narrative explains my enhancement to the CS-360 Mobile Application I created called "HopStock".

## Overview

The original artifact was an Android mobile inventory application that allowed users to log in, view warehouse inventory, search and filter stock items, edit item details, update quantities, and receive out-of-stock notifications. It was a useful mobile application, but in its original form, it primarily reflected the current inventory state. A user could see how many units were available at the moment, but the app did not preserve enough historical stock information to help users understand how inventory levels were changing over time.

## Justification & Improvement

I selected this artifact for my ePortfolio because it gave me a strong opportunity to move beyond basic operations and to demonstrate the use of algorithms and data structures that would have real-world value. Inventory management is not only about current information; in an actual warehouse environment, users need to recognize patterns, understand how quickly items are being depleted, and make better restocking decisions before something goes out of stock. That made this artifact a good fit for Category Two because I could enhance it from a simple stock tracker into a lightweight decision-support tool that uses historical data to communicate inventory trends.

The enhanced version adds timestamped stock history for each inventory item. Rather than storing only the latest quantity or storing a simple quantity-change value, the application now records stock history as timestamped quantity snapshots. I added a new Room entity, StockHistoryEntry, along with a StockHistoryDao and an updated Room database schema. Each stock history record is connected to an inventory item and stores the item's quantity at a specific point in time. This gives the application a simple yet extremely useful time-series data structure that can be queried, sorted, converted to chart points, and analyzed for trends.

I also updated the repository layer so that stock history is automatically recorded when inventory items are created or updated. This was an important design choice because it keeps the responsibility for history recording out of the UI layer, simplifying the inclusion of the feature. The Room database version was also updated, and a migration strategy was put in place that creates the new stock history table without dropping existing inventory or user data. Existing inventory rows are backfilled with simulated, realistic-looking stock quantity data for ease of demonstration.

However, the headline algorithmic improvement is the new trend calculation logic. The enhanced application retrieves a selected item's stock history, sorts it chronologically when needed, converts the records into chart data, and calculates a depletion trend using a least-squares linear regression approach. The algorithm estimates the rate of stock change in units per day and uses that slope to project a possible out-of-stock date when the trend is decreasing. If the history is too limited, covers only one day, contains duplicate timestamps, or does not show a meaningful depletion pattern, the app avoids presenting an inaccurate projection. This was important because I did not want the enhancement to imply certainty when the available data did not justify it.

While implementing this enhancement, I needed to account for restocking events, as a simple best-fit line across all raw stock history data would have produced a skewed trend. To address this, the restock offset logic prevents this inaccuracy, keeping the represented trend true to the stock's actual consumption rate.

The enhanced artifact also includes a new stock history graph screen. From the item detail screen, users can tap the graph button in the top-right corner, and the app will navigate to a screen that displays a chart with the item's historical stock levels and projected depletion trend. The graph uses stored snapshots of stock history and derives change markers by comparing each snapshot to the previous one. The chart includes formatted date labels, a "today" marker, pinch-and-zoom support, and shows details about individual snapshots if their markers are tapped on the screen. The overall depletion rate and projected out-of-stock date are clearly displayed numerically at the top of the screen, and the corresponding trend line is overlaid as a bold red dashed line, making it easy to understand the most important information the graph has to offer.

This enhancement also gave me an opportunity to address the code review items from Module Two. In addition to the trend graph itself, I improved the maintainability and professionalism of the application by adding file headers and comments, centralizing shared preference keys in an AppPrefs class, using singleton-style access for shared managers such as the repository and authentication manager, replacing less reliable shared-preference communication patterns with the Fragment Result API, and improving asynchronous UI updates with safer checks. I also strengthened the login workflow by adding password-strength validation and login rate limiting. These changes were not the main focus of the algorithms and data structures enhancement, but they helped refine the artifact and ready it for presentation in the final ePortfolio.

## Course Outcomes

I met the course outcomes I planned to address in Module One. This enhancement supports Outcome 1 because it provides warehouse staff and managers with better information for organizational decision-making, including prioritizing reorders and forecasting, by analyzing stock history. It supports Outcome 2 because the graph and summary text translate raw stock history and regression output into an easy-to-understand visualization for the user. It strongly supports Outcome 3 because the enhancement required data structure design, chronological sorting, time-series transformation, linear regression, edge-case handling, testing, and trade-off evaluation. It also supports Outcome 4 because it applies mobile development, Room persistence, repository design, charting tools, and predictive analysis to an industry-specific inventory problem.

I do not need to change my overall outcome coverage plan. This enhancement still aligns most directly with Outcomes 1, 2, 3, and 4, as planned in Module One. However, the final implementation also gives me additional support for Outcome 5. The password validation, login rate limiting, centralized preference handling, repository encapsulation, and safer lifecycle-aware UI updates show that I continued to think about security, misuse prevention, and maintainable architecture while completing the algorithmic work. I would not describe Outcome 5 as the primary focus of this enhancement, but the completed artifact is stronger because the code review improvements were addressed alongside the spotlight feature.

## Enhancement Process

The biggest learning experience in this enhancement was realizing that an algorithm is only valuable if it is designed around the actual problem context. Linear regression is a fairly straightforward algorithm mathematically, but applying it to inventory data requires careful processing. Real inventory history can be uneven. Items may be restocked suddenly, stock may remain stable for long periods, or there may not be enough data to make a responsible prediction. I had to decide when the app should calculate a projection, when it should avoid one, and how to present the result without overstating its accuracy. That helped me think more deeply about the trade-off between complexity, performance, and usefulness.

One challenge was designing the stock history model to support the enhancement without disrupting the existing app or prior installations. Adding a new Room table required updating the database version, creating a migration, preserving existing records, and backfilling initial stock history for existing inventory items. Another challenge was making the graph readable and useful. Plotting the points was only part of the work; I also had to think about date formatting, axis scaling, interaction, marker details, trend-line rendering, and how to visually separate actual stock history from projected stock behavior. These details made the enhancement feel more complete because the algorithm's output became something a user could quickly and realistically interpret and explore.

Overall, this enhancement gave me a stronger artifact for my ePortfolio because it demonstrates more than just mobile development skills; it shows that I can take an existing application, identify an opportunity for deeper value, design an appropriate data structure, implement and test an algorithm, evaluate trade-offs, and communicate the results clearly to users. HopStock is no longer just a simple inventory-quantity tracker app. It now leverages historical stock data to provide insight, communicate trends, and help facilitate better inventory management decisions.

---

[← Back to Portfolio](/)

