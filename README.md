```mermaid
erDiagram
    Participant {
        int id PK
        datetime createdAt
        datetime updatedAt
        string nickname UNIQUE
    }
    Group {
        int id PK
        datetime createdAt
        datetime updatedAt
        string name
        string? description
        string? photoUrl
        int goalRep
        string? discordWebhookUrl
        string? discordInviteUrl
        int likeCount
        string[] tags
        string[] badges
        int recordCount
    }
    Record {
        int id PK
        datetime createdAt
        datetime updatedAt
        string exerciseType
        string? description
        int time
        float distance
        string[] photos
    }
    Rank {
        int id PK
        int recordCount
        int recordTime
    }
    Like {
        int id PK
    }

    Participant ||--o{ Group : participates in
    Participant ||--o{ Record : creates
    Participant ||--o{ Rank : ranked in
    Group ||--o{ Record : has
    Group ||--o{ Rank : has
    Group ||--o{ Like : has
    Participant ||--o{ Group : owns
```
