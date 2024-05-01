# DayOrganizer Markup Language (DOML)

DayOrganizer Markup Language (DOML) is a Markdown-inspired language designed specifically for creating and organizing daily schedules in an efficient and intuitive way. It combines the simplicity of Markdown's syntax with specific features that cater to daily planning, making it an ideal choice for anyone looking to streamline their day-to-day tasks.

## Example

Below is an example DOML schedule that illustrates how to use DOML to organize a day:

### Input

```markdown
# Day 1 | 08:00 - 18:00

## Tasks 1
- Organize office | p2                              // Uses 'p' to denote the number of Pomodoros
- Review project proposals | p4
- Draft report | p3
* Client Meeting | 10:00 - 11:00                    // Fixed time task with explicit start and end times -->
* Team Sync | 15:00                                 // Fixed time task with a start time only, defaults to one Pomodoro duration (30 minutes total) -->
! Take vitamins | 08:05                             // Reminder at a specific time, no duration -->
- Lunch break | 1 hour at 13:00                     // Task with a specified duration starting at a specific time -->
- Overlapping task | 30 min at 17:00                // Task with a specified short duration starting at a specific time -->
- Overlapping task | 30 min at 17:25                // Another short duration task, starting shortly after the previous -->
! Coffee break | 15:15                              // Reminder at a specific time, no duration -->
& Go for a Walk | every 6 hours starting at 08:00   // Recurrent task, starts at 08:00 and repeats every 6 hours -->
& Feed the birds | every 6 hours                    // Recurrent task, starts based on the day start (08:00) and repeats every 6 hours -->

## Tasks 2
* Go to Gym | 08:00 - 09:00                         // Fixed time task with explicit start and end times -->
! Morning Meds | 07:00                              // Reminder at a specific time, no duration -->
```

### Output

```
07:00           - Morning Meds
08:00 to 08:30  - Go for a Walk
08:00 to 08:30  - Feed the birds
08:00 to 09:00  - Go to Gym
08:05           - Take vitamins
09:00 to 10:30  - Organize office
10:00 to 11:00  - Client Meeting
11:00 to 13:00  - Review project proposals
13:00 to 14:00  - Lunch break
14:00 to 14:30  - Go for a Walk
14:00 to 14:30  - Feed the birds
14:00 to 15:30  - Draft report
15:00 to 15:30  - Team Sync
15:15           - Coffee break
17:00 to 17:30  - Overlapping task 1
17:25 to 17:55  - Overlapping task 2
20:00 to 20:30  - Go for a Walk
20:00 to 20:30  - Feed the birds
```

##  Syntax

- **Flexible Tasks (`-`)**: Tasks that need to be fitted into the schedule. They can specify a duration or a desired number of Pomodoros. If no time is specified, the system should assume a default duration (e.g., 30 minutes).
- **Fixed Tasks (`*`)**: Tasks with a specific start and end time. These are non-movable within the schedule.
- **Reminders (`!`)**: Time-specific alerts that do not necessarily block out time but remind you at the specified moment.
- **Recurrent Tasks (`&`)**: Tasks that occur repeatedly throughout the designated schedule. These are set to recur based on a start time and frequency.

### Task Parameters

After the task symbol, tasks are defined with a description followed by a `|` symbol, which is used to separate the task description from its parameters. Parameters are then specified to dictate the timing and duration of tasks. Here are the key functions and formats you can use:

- **Pomodoro (`p`)**: Indicates the number of pomodoros (typically 25-minute blocks) a task should take. E.g., `p3`.