# Team Meeting 04 Notes (Sprint 2)

**Date:** 22/06/2026
**Project:** DataLens Streaming
**Client:** StreamFlix
**Meeting purpose:** Sprint 2 kickoff — database schema design and SQL implementation

This fourth team meeting marked the transition from Sprint 1 into Sprint 2. The session was used to review the Product Owner's sprint communication, confirm the tasks assigned for Sprint 2, and address a peer support request received via the team channel. The focus of Sprint 2 is to move from data exploration into physical database implementation.

## Sprint 2 launch communication

The Product Owner, Bhanu Prakash, issued a message to the team on the morning of 22 June 2026, acknowledging the successful completion of Sprint 1. The communication recognised the team's collaboration and effort across the sprint and outlined the next phase of work focused on database schema design and SQL table implementation.

The team reviewed the sprint communication during the meeting and confirmed a shared understanding of the expected deliverables before beginning task assignment.

## Sprint 2 tasks assigned

The following tasks were assigned to the team for Sprint 2, covering schema design, physical database implementation, and early data exploration.

### Define the database structure
The team was assigned the task of designing the database schema by identifying the necessary tables, fields, and relationships based on the client requirements established during Sprint 1.

The team agreed on the following conceptual schema structure:

- **Movies table:** movie identifier, title, year, language, country, and total views
- **Users table:** user identifier, age, gender, country, subscription status, total watch time, and device
- **Ratings table:** rating identifier, linked user, linked movie, rating value, and timestamp
- **Genres table:** genre identifier and genre name
- **Movie_Genres table:** linked movie and linked genre, resolving the many-to-many relationship between movies and genres

The relationships were confirmed as One-to-Many between Users and Ratings, and One-to-Many between Movies and Ratings. Movies and Genres share a Many-to-Many relationship, resolved through the Movie_Genres junction table, allowing a single film to belong to multiple genres without duplication. This is consistent with the Star Schema design recommended at the end of Sprint 1, with `Ratings` as the Fact Table and `Users`, `Movies`, and `Genres` as Dimension Tables.

The team will use SQL and an ERD tool to complete this task. Deliverables include an ERD diagram and a schema design documentation file uploaded to Jira.

### Implement tables in SQL
The team was also assigned the task of creating the Movies, Users, Ratings, Genres, and Movie_Genres tables in the SQL database and validating the relationships between them.

The team discussed and agreed on the following implementation approach:

1. Set up the database connection and identify the appropriate method for importing data from CSV files
2. Write `CREATE TABLE` SQL statements with appropriate data types and primary keys for all tables
3. Create the Ratings and Movie_Genres tables with foreign key references to the relevant parent tables
4. Validate foreign key relationships by inserting sample data and running test queries
5. Save and document all SQL scripts on Jira

Deliverables for this task include SQL scripts for all tables, test queries, and validation screenshots or logs.

### Data exploration for future visualisation
To prepare for the upcoming visualisation and dashboard work, the team took the initiative to think through how the dataset could be explored and structured for future analysis. The focus was on identifying useful measures and considering how different dimension categories, such as age groups and movie decades, might affect the way the data could later be visualised.

## Peer support — ad hoc request

The team received an ad hoc request from a colleague seeking guidance on creating a world choropleth map to visualise the happiness index across multiple years using Python.

In response, the team suggested using `pandas` for data loading and merging, `plotly.express` as the main visualisation library for interactive animated maps, and `geopandas` as an optional tool for more advanced geographic control.

The team also noted that column naming inconsistencies across the 2015–2019 CSV files would need to be resolved before merging, and outlined a step-by-step workflow to help get started without building the full solution.

## Key discussion points

The team confirmed that the schema structure agreed during Sprint 1 remained appropriate for the current sprint and continued to align with the available data.

The team also noted that some user performance metrics were available, but not in the full form originally hoped for, and no internal success benchmarks were provided. The product owner clarified that the team would need to establish its own thresholds for analysis and focus on building the strongest possible outcome from the data that was available. Film availability dates were not supplied, and clarification on the movie-level Language and Country fields was not provided, making those dimensions difficult to use reliably in the analysis.

The earlier planning items around priority regions, rights acquisition costs, promotional spend, and dashboard stakeholder detail were not progressed, so those aspects were no longer in scope for the current phase.

The timestamp field was also treated as a date-level value for analysis purposes, which supported cleaner processing and more consistent reporting across the dataset.

## Immediate actions agreed

The team agreed to:
- begin ERD diagramming based on the confirmed five-table schema,
- write `CREATE TABLE` SQL statements for all tables,
- validate the schema by importing sample data from the provided CSV files and testing query relationships,
- resolve the outstanding unmatched `UserID` referential integrity issue before finalising the schema,
- consider future measures and dimension categories to support later visualisation work, share any relevant insights or observations with the team,
- and upload all completed SQL scripts, ERD diagrams, and documentation to Jira before the Sprint 2 review session.

## Next steps

The next phase of work will focus on physical database implementation and early data exploration. The team will proceed using the confirmed data structure, with all deliverables to be completed and documented on Jira by the Sprint 2 review.