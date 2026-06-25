# Team Meeting 02 Notes (Sprint 1)

**Date:** 18/06/2026  
**Project:** DataLens Streaming  
**Client:** StreamFlix  
**Meeting purpose:** Sprint 1 kickoff and initial data review

This second team meeting was used to confirm how the team will track work, manage tasks, and review the initial dataset received from the client. The primary focus of Sprint 1 is to build a reliable foundation for the analytics work by identifying and resolving data quality issues early.

## Project workflow summary

The team finalised the internal project coordination structure and agreed to use Jira as the main platform for managing project tasks, sprint progress, and deliverables, rather than using alternatives such as Trello.

The agreed Jira workflow is:
- **Backlog:** Long-term project requirements and incoming tasks.
- **To Do:** Tasks ready to be started during the current sprint.
- **In Progress:** Tasks currently being worked on by team members.
- **Done:** Completed and verified deliverables.

To support consistency across the team, operational how-to guides were shared. These documents explain the agreed processes for using Git for version control, following branch naming conventions, and keeping the Jira board updated.

## Team understanding of the dataset

The team agreed that no dashboarding or deeper analysis should begin until the dataset has been properly reviewed and cleaned. Everyone recognised that the quality of the final dashboard will depend on identifying and correcting irregularities during this early data-cleansing stage.

The team also identified a major limitation in the client-provided dataset: it does not contain the user-level information required to produce audience-segmented insights. Without user demographics, subscription data, user-level watch history, performance metrics, and film availability dates, the analysis will be limited to movie-level trends such as total views and overall genre popularity.

To keep the project accessible and collaborative, the cleaned version of the dataset was uploaded to Jira so all team members can work from the same version.

## Key discussion points

- **Missing values:** The team discovered rows with missing information in critical fields, including empty film titles and missing years for specific movie records.
- **Genre classification issues:** Several titles were found under inconsistent genre categories that do not match standard film classifications.
- **Spelling errors:** The team identified clear text and spelling mistakes within the genre description fields.

The team also noted that the Language and Country fields appear to contain single values for each film, but some entries seem unusual or inconsistent. These fields needed clarification to determine whether they represent original production details or simplified dataset labels.

## Data cleaning actions

Following a collaborative review of the dataset, the team agreed on and completed the following data cleaning actions:
- **Missing titles and years:** Two entries were missing both movie title and year. These were marked as **Unknown** so they can be filtered from the analysis if needed.
- **Genre corrections:** The genre label **Dramatic** appeared three times and was replaced with more appropriate classifications:
  - *Final Destination* was changed to **Horror**.
  - *Schindler’s List* was changed to **War & Drama**.
  - *Gladiator* was changed to **Action & Drama**.
- **Genre adjustment:** *Scary Movie* was labelled as **Comedy-Horror**. This was split into **Comedy** and **Horror**, and the combined **Comedy-Horror** label was removed because it appeared only once in the dataset.
- **Spelling corrections:** The genre value **Dramma** appeared in *Wonder Boys* and *Fargo* and was corrected to **Drama**.

## Clarifications required

The team drafted a follow-up email to the client or product owner to resolve ambiguities in several data fields and to request missing information needed for the project.

### Missing user-level data
The team recommended that the missing user-level data be requested as a priority because it directly affects whether the team can deliver the audience-segmented insights expected by 1 July.

The requested data includes:
- user demographics, including age and location,
- subscription data distinguishing between free and paid users,
- user-level watch history,
- performance metrics such as ratings or completion rates,
- and film availability dates, to understand how long each title has been available for viewing on the service.

### Language column
- Whether this column refers to the original audio language, subtitle language, or another format.
- Whether the values were simplified during data preparation.

### Country column
- Whether this column refers to the country of production or another classification used in the dataset.
- Whether the values were simplified during data preparation.

### Total Views column
- Whether the total views are recorded globally for each movie or are specific to each country listed.

## Immediate actions agreed

The team agreed to:
- verify that all team members have the correct access to update tasks in Jira,
- break large backlog items into smaller and more actionable subtasks,
- review the shared Git and Jira guides to maintain a consistent workflow,
- and send the final clarification email to the client.

## Client follow-up

A clarification email was sent to Bhanu outlining the data limitations, the cleaning summary, and the outstanding questions about the dataset fields.

The email explained that, without the missing user-level data, the analysis would be limited to movie-level trends and would not be able to deliver the more targeted audience insights requested in the project brief. It also requested confirmation about the meaning of the Language, Country, and Total Views fields so the dataset can be interpreted correctly.

## Next steps

The next phase of work depends on the client’s response to the clarification questions. Once the feedback is received and the dataset structure is confirmed, the team will review the final data model and begin the dashboard design phase.