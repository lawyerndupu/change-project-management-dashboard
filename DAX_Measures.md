# DAX Measures

This document contains the key DAX measures used in the Change Project Management Dashboard.

## 1. Total Tasks

Counts the total number of project tasks.

```DAX
Total Tasks =
COUNTROWS('Change Project Management')

## 2. In Progress

Counts tasks whose status is recorded as "In- Progress"

```DAX
In Progress =
CALCULATE(
    COUNTROWS('Change Project Management'),
    'Change Project Management'[Task Status] = "In- Progress"
)
