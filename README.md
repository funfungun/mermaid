```mermaid
erDiagram
    PARTICIPANT {
        STRING id
        STRING nickname
        STRING password
        DATETIME createdAt
        DATETIME updatedAt
        STRING groupId
    }
    GROUP {
        STRING id
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
        STRING id
        EXERCISETYPE exerciseType
        STRING description
        INT time
        INT distance
        STRING[] photos
        STRING authorId
        STRING groupId
        DATETIME createdAt
        DATETIME updatedAt
    }

    PARTICIPANT ||--o{ RECORD : has
    GROUP ||--o{ PARTICIPANT : contains
    GROUP ||--o{ RECORD : has
    RECORD }|--|| PARTICIPANT : author
    RECORD }|--|| GROUP : belongsTo

    enum BADGETYPE {
        PARTICIPATION_10
        RECORD_100
        LIKE_100
    }

    enum EXERCISETYPE {
        RUN
        BIKE
        SWIM
    }
