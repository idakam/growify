# Entity Relationship Diagram

![image](https://github.com/user-attachments/assets/8d9f2721-2340-48ac-96bc-bd7c11941abd)

## Create the List of Tables

### 1. Users
### 2. Skill Paths
### 3. Tasks
### 4. User Tasks
### 5. Achievements
### 6. User Achievements
### 7. Reminders
### 8. Progress

## Add the Entity Relationship Diagram

### 1. Users Table
| Column Name     | Type        | Description                           |
|-----------------|-------------|---------------------------------------|
| user_id         | integer     | primary key                           |
| name            | varchar     | name of the user                      |
| email           | varchar     | unique email address of the user      |
| password        | varchar     | hashed password                       |
| profile_picture | varchar     | URL for the user's profile picture    |
| date_of_birth   | date        | birth date of the user                |
| created_at      | timestamp   | timestamp of when the user was created |

### 2. Skill Paths Table
| Column Name     | Type        | Description                           |
|-----------------|-------------|---------------------------------------|
| skill_path_id   | integer     | primary key                           |
| name            | varchar     | name of the skill path                |
| description     | text        | detailed description of the skill path|
| difficulty_level| varchar     | difficulty level (e.g., Beginner)     |
| category        | varchar     | category of the skill (e.g., Technology) |

### 3. Tasks Table
| Column Name     | Type        | Description                           |
|-----------------|-------------|---------------------------------------|
| task_id         | integer     | primary key                           |
| skill_path_id   | integer     | foreign key referencing skill_paths   |
| name            | varchar     | name of the task                      |
| description     | text        | details of the task                   |
| points          | integer     | points awarded for task completion    |
| required        | boolean     | whether the task is mandatory         |

### 4. User Tasks Table
| Column Name     | Type        | Description                           |
|-----------------|-------------|---------------------------------------|
| user_task_id    | integer     | primary key                           |
| user_id         | integer     | foreign key referencing users         |
| task_id         | integer     | foreign key referencing tasks         |
| completion_status | boolean   | task completion status                |
| completed_at    | timestamp   | timestamp of task completion          |

### 5. Achievements Table
| Column Name     | Type        | Description                           |
|-----------------|-------------|---------------------------------------|
| achievement_id  | integer     | primary key                           |
| name            | varchar     | name of the achievement               |
| description     | text        | details of the achievement            |
| badge_icon      | varchar     | URL of the badge icon                 |
| criteria        | text        | conditions to earn the achievement    |

### 6. User Achievements Table
| Column Name     | Type        | Description                           |
|-----------------|-------------|---------------------------------------|
| user_achievement_id | integer | primary key                           |
| user_id         | integer     | foreign key referencing users         |
| achievement_id  | integer     | foreign key referencing achievements  |
| earned_at       | timestamp   | timestamp when the achievement was earned |

### 7. Reminders Table
| Column Name     | Type        | Description                           |
|-----------------|-------------|---------------------------------------|
| reminder_id     | integer     | primary key                           |
| user_id         | integer     | foreign key referencing users         |
| task_id         | integer     | foreign key referencing tasks         |
| reminder_time   | timestamp   | time for the reminder                 |

### 8. Progress Table
| Column Name     | Type        | Description                           |
|-----------------|-------------|---------------------------------------|
| progress_id     | integer     | primary key                           |
| user_id         | integer     | foreign key referencing users         |
| skill_path_id   | integer     | foreign key referencing skill_paths   |
| progress_percentage | decimal | progress percentage of the skill path |
| last_updated    | timestamp   | timestamp of last progress update     |
