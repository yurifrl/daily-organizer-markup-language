# DayOrganizer Markup Language (DOML)

DayOrganizer Markup Language (DOML) is a Markdown-inspired language designed specifically for creating and organizing daily schedules in an efficient and intuitive way. It combines the simplicity of Markdown's syntax with specific features that cater to daily planning, making it an ideal choice for anyone looking to streamline their day-to-day tasks.

## Example

Below is an example DOML schedule that illustrates how to use DOML to organize a day:

<!-- TODO: Find how to fit https://github.com/tj/go-naturaldate here-->

```markdown

# Day 1 | 14:00 - 23:00

## Tasks 1
- Organize notion | p2
- Go to Gym | 07am
- Watch Freecad videos | pomodoro 3
* Team Meeting | range 15:30 to 16:30
- Practice crimping SN-* Connectors | duration 1h
! Take medicine | time 14:05
! Eat a snack | 17:05
& Standup | duration 30min, every 30 minutes

## Tasks 2
! Feed the dog | time 08:00
! Feed the dog | time 12:00
! Feed the dog | time 20:00


```

```markdown
# Day 1 | 08:00 - 18:00

## Tasks
- Organize office | p2
- Review project proposals | pomodoro 4
- Draft report | pomodoro 3
* Client Meeting | range 10:00 to 11:00
* Team Sync | range 15:00 to 16:00
! Take vitamins | time 08:05
- Lunch break | 13:00 - 14:00
- Overlapping | 17:00
- Overlapping | 17:25

! Coffee break | t15
& Go for a Walk | 6h 

## Tasks 2
- Go to Gym | p2
! Morning Meds | 7am
```

### Output

```
```

## Logic
- Tasks with no end default to 1 pomodoro

## Syntax

DOML employs a straightforward syntax that utilizes various symbols to denote different types of tasks and events within your schedule. Each task type is prefixed by a specific symbol, making it easy to identify and categorize tasks at a glance. Here's a breakdown of the syntax and task types:

### Task Definition Symbols

- **`-` Regular Task**: This is the default task type, which typically requires a duration or count of pomodoros. If no specific time is given, it defaults to a pre-configured pomodoro setting.

- **`*` Fixed Time Task**: For tasks that need to occur at a specific time or within a specific time range. You must provide a time range for these tasks.

- **`!` Reminder**: These are time-specific alerts with no duration. They serve as reminders for fixed-time necessities throughout the day.

- **`&` Recurrent Task**: Tasks that recur at a set interval throughout the designated schedule period. These usually default to a standard duration unless specified otherwise.

### Task Parameters

After the task symbol, tasks are defined with a description followed by a `|` symbol, which is used to separate the task description from its parameters. Parameters are then specified to dictate the timing and duration of tasks. Here are the key functions and formats you can use:

- **Pomodoro (`p`, `pomodoro`)**: Indicates the number of pomodoros (typically 25-minute blocks) a task should take. E.g., `pomodoro 3`.

- **Duration (`d`, `duration`)**: Specifies the duration of the task. E.g., `duration 1h`.

- **Range (`r`, `range`)**: Used for fixed time tasks to define a specific time range during which the task should occur. E.g., `range 15:30 to 16:30`.

- **Time (`t`, `time`)**: Sets a specific time for reminders or fixed-time tasks. E.g., `time 14:05`.

Parameters can be combined or used singularly based on the requirements of the task. The parser is designed to interpret these inputs based on the specified or default functions.


## Available Configuration Options

-- 
pomodoro_long_break: 20m   # Duration of long breaks after a set of pomodoros
pomodoro_session_size: 30m # Default duration of a pomodoro session
pomodoro_set: 4            # Number of pomodoros before a long break
pomodoro_short_break: 5m   # Duration of short breaks between pomodoros
task_separator: ", "       # Separator for task parameters
time_format: 24h           # Time format for displaying tasks
--
