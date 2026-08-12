# DAX Measures

## Total Tasks

```DAX
Total Tasks =
COUNTROWS('Change Project Management')

In Progress =
CALCULATE(
    COUNTROWS('Change Project Management'),
    'Change Project Management'[Task Status] = "In- Progress"
)
