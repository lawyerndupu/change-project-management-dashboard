# DAX Measures

## Total Tasks
Counts the total number of project tasks.

```DAX
Total Tasks =
COUNTROWS('Change Project Management')
```

## In Progress
Counts tasks whose status is recorded as "In- Progress".

```DAX
In Progress =
CALCULATE(
    COUNTROWS('Change Project Management'),
    'Change Project Management'[Task Status] = "In- Progress"
)
```

## Overdue Tasks
Counts tasks that have passed their due date and have not been completed.

```DAX
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
```

## Awaiting Approval
Counts tasks in the Awaiting Approval project bucket.

```DAX
Awaiting Approval =
CALCULATE(
    COUNTROWS('Change Project Management'),
    'Change Project Management'[Bucket] = "1- Awaiting Approval"
)
```

## Core IT Projects
Counts tasks associated with Core IT projects.

```DAX
Core IT Projects =
CALCULATE(
    COUNTROWS('Change Project Management'),
    'Change Project Management'[Bucket] = "CORE IT PROJECT"
)
```

