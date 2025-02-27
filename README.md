## Database Schema

```mermaid
erDiagram
    PARTICIPANT {
        INT id
        STRING nickname
        STRING password
        DATETIME createdAt
        DATETIME updatedAt
        INT groupId
    }
    GROUP {
        INT id
        STRING name
        STRING description
        STRING photoUrl
        INT goalRep
        STRING discordWebhookUrl
        STRING discordInviteUrl
        INT likeCount
        STRING[] tags
        STRING ownerNickname
        STRING ownerPassword
        BADGETYPE[] badges
        INT recordCount
        DATETIME createdAt
        DATETIME updatedAt
    }
    RECORD {
        INT id
        EXERCISETYPE exerciseType
        STRING description
        INT time
        INT distance
        STRING[] photos
        INT authorId
        INT groupId
        DATETIME createdAt
        DATETIME updatedAt
    }

    PARTICIPANT ||--o| GROUP : "belongs to"
    PARTICIPANT ||--o{ RECORD : "writes"
    GROUP ||--o{ PARTICIPANT : "has"
    GROUP ||--o{ RECORD : "contains"
    RECORD ||--|{ GROUP : "belongs to"
    RECORD ||--|{ PARTICIPANT : "authored by"

    BADGETYPE {
        STRING PARTICIPATION_10
        STRING RECORD_100
        STRING LIKE_100
    }

    EXERCISETYPE {
        STRING RUN
        STRING BIKE
        STRING SWIM
    }
