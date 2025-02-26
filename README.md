```mermaid
erDiagram
    Participant {
        Int id PK
        DateTime createdAt
        DateTime updatedAt
        String nickname UNIQUE
    }
    Group {
        Int id PK
        DateTime createdAt
        DateTime updatedAt
        String name
        String? description
        String? photoUrl
        Int goalRep
        String? discordWebhookUrl
        String? discordInviteUrl
        Int likeCount
        String[] tags
        String[] badges
        Int recordCount
    }
    Record {
        Int id PK
        DateTime createdAt
        DateTime updatedAt
        String exerciseType
        String? description
        Int time
        Float distance
        String[] photos
    }
    Rank {
        Int id PK
        Int recordCount
        Int recordTime
    }
    Like {
        Int id PK
    }

    Participant ||--o{ Group : participates in
    Participant ||--o{ Record : creates
    Participant ||--o{ Rank : ranked in
    Group ||--o{ Record : has
    Group ||--o{ Rank : has
    Group ||--o{ Like : has
    Participant ||--o{ Group : owns

    Participant {
        Int id PK
        DateTime createdAt
        DateTime updatedAt
        String nickname UNIQUE
    }
    Group {
        Int id PK
        DateTime createdAt
        DateTime updatedAt
        String name
        String? description
        String? photoUrl
        Int goalRep
        String? discordWebhookUrl
        String? discordInviteUrl
        Int likeCount
        String[] tags
        String[] badges
        Int recordCount
    }
    Record {
        Int id PK
        DateTime createdAt
        DateTime updatedAt
        String exerciseType
        String? description
        Int time
        Float distance
        String[] photos
    }
    Rank {
        Int id PK
        Int recordCount
        Int recordTime
    }
    Like {
        Int id PK
    }

    Participant ||--o{ Group : participates in
    Participant ||--o{ Record : creates
    Participant ||--o{ Rank : ranked in
    Group ||--o{ Record : has
    Group ||--o{ Rank : has
    Group ||--o{ Like : has
    Participant ||--o{ Group : owns
```
