## ERD

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
        STRING ownerNickname
        STRING ownerPassword
        INT recordCount
        DATETIME createdAt
        DATETIME updatedAt
    }

    RECORD {
        INT id
        ENUM exerciseType
        STRING description
        INT time
        INT distance
        STRING[] photos
        INT authorId
        INT groupId
        DATETIME createdAt
        DATETIME updatedAt
    }

    TAG {
        INT id
        STRING name
        DATETIME createdAt
        DATETIME updatedAt
        INT groupId
    }

    BADGETYPE {
        ENUM PARTICIPATION_10
        ENUM RECORD_100
        ENUM LIKE_100
    }

    EXERCISETYPE {
        ENUM RUN
        ENUM BIKE
        ENUM SWIM
    }

    PARTICIPANT }o--|| GROUP : "belongs to"
    GROUP ||--o{ PARTICIPANT : "has many"
    
    RECORD }o--|| PARTICIPANT : "written by"
    PARTICIPANT ||--o{ RECORD : "has many"

    RECORD }o--|| GROUP : "belongs to"
    GROUP ||--o{ RECORD : "has many"

    TAG }o--|| GROUP : "belongs to"
    GROUP ||--o{ TAG : "has many"

    GROUP }o--o{ BADGETYPE : "awards"
    RECORD }o--|| EXERCISETYPE : "uses"
