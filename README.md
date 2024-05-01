# Day Planner Markup Language (DPML)

DPML is a lightweight, human-readable syntax for scheduling daily tasks and events.

## Description

The Day Planner Markup Language (DPML) brings structure and clarity to your daily scheduling, transforming chaotic agendas into well-organized plans.
DPML uses symbols to define tasks. For example, set `* Team Meeting | 10:00 - 11:00` for a fixed time slot, or use `- Review Emails | p2` to fit email reviews flexibly into two pomodoros.

# Format

```markdown
# Day X | Start Time - End Time

## Tasks
- Task Description | Time or Duration
! Reminder | Time
* Fixed Task | Time or Interval
& Recurrent Task | Interval
```

# Example

## Input
```markdown
# Day 1 | 08:00 - 18:00

## Tasks
! Drin Water | 7am                              // Reminder to drink water once af 7am
- Review Emails | p2                            // Allocates 2 pomodoros
- Finish the Pull Request | 1h                  // Allocates 1h
- Do the FreeCAD course | p2
- Read Moby-Dick | 1h
- Work on DOML | p4
- Finish Puzzle | ai                            // Uses AI to estimate time for completing a 100-piece puzzle
    It's a a 100 pieces puzzle                  // You can add extra context to any task, it will not be Printed but some helpers may use it
* Team Meeting | 10:00 - 11:00                  // Fixed time for a team meeting
! Take a Break | 14:30                          // Reminder to take a break at 14:30
& Go for a Walk | every 6h starting at 09:00    // Recurrent task to walk every 6 hours
```

## Output
```markdown
08:00 to 08:50  - Review Emails
09:00 to 09:05  - Go for a Walk
09:00 to 09:30  - Finish the Pull Request
09:30 to 11:00  - Do the FreeCAD course
10:00 to 11:00  - Team Meeting
11:00 to 12:00  - Work on DOML
12:00 to 13:00  - Read Moby-Dick
13:00 to 15:00  - Continue work on DOML
14:30           - Take a Break
15:00           - Finish Puzzle
15:00 to 15:05  - Go for a Walk
```

# Syntax

## Definitions
- `-` **Flexible Task**: Automatically fits into the open slots of your schedule. Specify duration using Pomodoros (`p`) or explicit timing.
- `*` **Fixed Task**: Occurs at a specific time. Provide exact start and optional end times. Defaults to one Pomodoro if end time is omitted.
- `!` **Reminder**: Triggers notifications at specified times. No duration.
- `&` **Recurrent Task**: Repeats at defined intervals. Starts based on the schedule's start time or specified starting point.

## Helpers

Tasks are defined with a description followed by a `|` symbol, which is used to separate the task description from its parameters. Parameters can be given to helpers that take the subsequent parameter and parses it

- **Pomodoro (`p`)**: Indicates the number of pomodoros a task should take. E.g., `p3`.
- **Ai (`ai`)**: You can add this to let the ai choose for you, or add a long description bellow you taks

## Contribution
Contributions are welcome. Please fork the repository, make changes, and submit a pull request.

## License
DPML is released under the MIT license. Details can be found in the LICENSE file.

This README provides all the necessary information to understand and start using DPML efficiently in your daily planning.