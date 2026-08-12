# DAX Measures

This document contains the key DAX measures used in the Change Project Management Dashboard.

## 1. Total Tasks

Counts the total number of project tasks.

```DAX
Total Tasks =
COUNTROWS('Change Project Management')

2. In Progress

Counts tasks whose status is recorded as "In- Progress".

In Progress =
CALCULATE(
    COUNTROWS('Change Project Management'),
    'Change Project Management'[Task Status] = "In- Progress"
)

3. Overdue Tasks

Counts tasks that have passed their due date and have not been completed.

Overdue Tasks =
CALCULATE(
    COUNTROWS('Change Project Management'),
    FILTER(
        'Change Project Management',
        NOT ISBLANK('Change Project Management'[Due date]) &&
        'Change Project Management'[Due date] < TODAY() &&
        ISBLANK('Change Project Management'[Date completed])
    )
)

4. Awaiting Approval

Counts tasks in the Awaiting Approval project bucket.

Awaiting Approval =
CALCULATE(
    COUNTROWS('Change Project Management'),
    'Change Project Management'[Bucket] = "1- Awaiting Approval"
)

5. Core IT Projects

Counts tasks associated with Core IT projects.

Core IT Projects =
CALCULATE(
    COUNTROWS('Change Project Management'),
    'Change Project Management'[Bucket] = "CORE IT PROJECT"
)

DAX Techniques Used
COUNTROWS() for task counting
CALCULATE() for filtered calculations
FILTER() for conditional row evaluation
ISBLANK() for identifying incomplete records
TODAY() for dynamic overdue-task calculations
Column-based filtering for project status and buckets
