```mermaid
erDiagram
    GROUP {
        int id PK
        string name "UNIQUE"
        string description
        string photoUrl
        int goalRep "DEFAULT 0"
        string discordWebhookUrl
        string discordInviteUrl
        int likeCount "DEFAULT 0"
        string[] tags
        int owner_id FK
        datetime createdAt "DEFAULT NOW()"
        datetime updatedAt "DEFAULT NOW()"
    }

    USER {
        int id PK
        string nickname "UNIQUE"
        string password
        datetime createdAt "DEFAULT NOW()"
        datetime updatedAt "DEFAULT NOW()"
    }

    GROUP_PARTICIPANT {
        int id PK
        int group_id FK
        int user_id FK
        datetime joinedAt "DEFAULT NOW()"
    }

    GROUP ||--o{ GROUP_PARTICIPANT : "has many participants"
    USER ||--o{ GROUP_PARTICIPANT : "can join many groups"
    GROUP ||--|| USER : "has an owner"
    USER ||--o| EXERCISE_RECORD : "writes"

    EXERCISE_RECORD {
        int id PK
        int group_id FK
        int user_id FK
        string exerciseType "ENUM('running', 'cycling', 'swimming')"
        string description
        int duration "time"
        float distance "in km"
        string[] photos
        datetime createdAt "DEFAULT NOW()"
    }
    EXERCISE_RECORD }|--|| GROUP : "belongs to"

    BADGE {
        int id PK
        int group_id FK
        string type "ENUM('participants_10', 'records_100', 'recommendations_100')"
        datetime awardedAt "DEFAULT NOW()"
    }
    BADGE }|--|| GROUP : "awarded to"

    GROUP ||--o| BADGE : "can have multiple"
```
