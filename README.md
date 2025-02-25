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
        int owner_id FK "REFERENCES USER(id)"
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
        int group_id FK "REFERENCES GROUP(id)"
        int user_id FK "REFERENCES USER(id)"
        datetime joinedAt "DEFAULT NOW()"
        UNIQUE(group_id, user_id)
    }

    GROUP ||--o{ GROUP_PARTICIPANT : "has many participants"
    USER ||--o{ GROUP_PARTICIPANT : "can join many groups"
    GROUP ||--|{ USER : "has an owner"

    EXERCISE_RECORD {
        int id PK
        int group_id FK "REFERENCES GROUP(id)"
        int user_id FK "REFERENCES USER(id)"
        string exerciseType "ENUM('running', 'cycling', 'swimming')"
        string description
        int duration "time"
        float distance "in km"
        string[] photos
        datetime createdAt "DEFAULT NOW()"
    }

    GROUP ||--o{ EXERCISE_RECORD : "contains"
    USER ||--o{ EXERCISE_RECORD : "writes"

    BADGE {
        int id PK
        int group_id FK "REFERENCES GROUP(id)"
        string type "ENUM('participants_10', 'records_100', 'recommendations_100')"
        datetime awardedAt "DEFAULT NOW()"
    }

    GROUP ||--o{ BADGE : "can have multiple"
