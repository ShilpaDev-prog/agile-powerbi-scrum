# Team Meeting 05 Notes (Sprint 2)

**Date:** 23/06/2026
**Project:** DataLens Streaming
**Client:** StreamFlix
**Meeting purpose:** Sprint 2 review — client demo, database deliverables, and visualisation assignment

This fifth team meeting served as the Sprint 2 review session. The team presented the completed database work to the client, walked through the schema design and ERD, and demonstrated the SQL tables. The session also included a data quality finding in the ratings dataset, the assignment of the agreed visualisations to team members, and a review of an informal client request received during the session.

## Sprint 2 deliverables completed

The team completed and presented three core deliverables during this session: the Entity Relationship Diagram and accompanying database design documentation, the SQL database implementation covering all five tables, and a structured client demo walking through the schema design rationale, ERD, and SQL implementation in client-friendly language.

## ERD and schema design

The finalised ERD defines five tables across the DataLens Streaming database:

- **movies_clean:** `MovieID` (PK), `Movie_Title`, `Year`, `Language`, `Country`, `Total_Views`
- **Users:** `UserID` (PK), `Age`, `Gender`, `Country`, `SubscriptionStatus`, `TotalWatchtime`, `Device`
- **Ratings:** `RatingID` (PK), `UserID` (FK), `MovieID` (FK), `Rating`, `Timestamp`
- **genres:** `GenreID` (PK), `Genre_Name`
- **movie_genres:** `MovieID` (PK, FK1), `GenreID` (PK, FK2)

The schema follows a relational model with One-to-Many relationships between `Users` and `Ratings`, and between `movies_clean` and `Ratings`. A Many-to-Many relationship between `movies_clean` and `genres` is resolved through the `movie_genres` junction table, allowing a single movie to be associated with multiple genres without duplication.

## SQL database implementation

The `DataLensStreaming` database was created and populated, and all five tables were implemented using SQL. Data was imported from the client-provided CSV files using the `LOAD DATA INFILE` command. Foreign key constraints were applied to the `Ratings` and `movie_genres` tables to enforce referential integrity across the schema.

The `Ratings` table links `UserID` and `MovieID` as foreign keys referencing the `Users` and `movies_clean` tables respectively. The `movie_genres` table uses a composite primary key of `(MovieID, GenreID)` to manage the many-to-many relationship between `movies_clean` and `genres` cleanly.

## Data quality finding — duplicate ratings

During the session, the team identified two duplicate entries in the ratings dataset. In both cases, the same user had rated the same movie on two separate occasions, resulting in different rating values, different rating IDs, and different timestamps.

The team discussed the appropriate approach and agreed that the most recent rating should be retained for analysis in each case, as it represents the user's most current view of the film. The earlier entries will be excluded from the analysis. This decision was documented as part of the sprint record.

## Client demo

The team presented the database structure to the client using a structured walkthrough covering the following areas:

- **Session goals:** Restated the project context and outlined what the schema is designed to support — understanding who is watching what, how users rate content, and how behaviour changes over time.
- **Schema design rationale:** Contrasted a single flat table approach with the team's relational design, explaining the benefits of the normalised structure including faster querying, reduced duplication, and scalability for future analysis.
- **ERD walkthrough:** Explained each of the five entities and their relationships in plain terms, connecting specific table attributes to the client's original business questions.
- **Visualisation strategy:** Outlined the types of insights the database is now able to support, including content performance comparisons using `Total_Views` and audience segmentation using demographic and subscription fields.

## Visualisations assigned

The Product Owner confirmed the approach for the next phase of work, with the team required to produce visualisations in Python for review, using the SQL database as the source data. The visualisation areas were then allocated across the team to support this work.

| Visualisation area | Lead |
|---|---|
| Top 10 Movies by Average Ratings | Sabahat Naz |
| Most Popular Genres | Sabahat Naz |
| User Distribution by Age Group | Shanika Kodithuwakku |
| Distribution of Users by Subscription Status | Shilpa Joseph |
| User Distribution by Country | Rakhi Porwad |
| Distribution of Device Usage Among Users | Andrew Chung |

The team noted that this phase would involve preparing the required SQL outputs, shaping the data for analysis in Python, and producing draft visualisations for review and refinement in the next stage.

## Informal client request — ratings by subscription type

During the Sprint Review, the Product Owner relayed an informal message received from the client suggesting it might be useful to see average ratings by movie, segmented by free and premium users.

The Product Owner made clear this was not a formal requirement and no immediate response was required. The team reviewed the request together and agreed it was a valuable analytical direction that aligns well with the existing schema, as the `Ratings` and `Users` tables together support this type of segmentation query directly. The team will document the informal client request and develop the relevant SQL queries this sprint so they can support a future client response if required.

## Key discussion points

- The duplicate ratings finding reinforced the importance of data validation before analysis begins, and the agreed approach of retaining the most recent rating will be applied consistently across the dataset.
- The team confirmed that the completed schema supports the agreed visualisation work and the next phase of analysis.
- The informal client request regarding average ratings by subscription type was recognised as a useful follow-on query that aligns with the available data and the existing schema.

## Immediate actions agreed

The team agreed to:
- apply the duplicate ratings resolution rule across the full dataset before beginning visualisation work,
- begin individual visualisation development based on the assignments confirmed during this session,
- document the SQL approach for the informal client ratings query in preparation for a future response,
- and upload all completed scripts, the ERD, and design documentation to Jira.

## Next steps

With the database structure fully implemented and validated, the team will move into the data analysis and visualisation phase. Each team member will develop their assigned visualisation, with the duplicate-ratings issue resolved first. The informal client request regarding average ratings by subscription type will be explored as a SQL exercise and prepared for a formal response in the future.