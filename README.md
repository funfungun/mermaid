## erd

```mermaid
erDiagram
  Participant {
    int id PK
    string nickname
    string password
    datetime createdAt
    datetime updatedAt
    int groupId FK
  }

  Group {
    int id PK
    string name
    string description
    string photoUrl
    int goalRep
    string discordWebhookUrl
    string discordInviteUrl
    int likeCount
    string ownerNickname
    string ownerPassword
    BadgeType badges
    int recordCount
    datetime createdAt
    datetime updatedAt
  }

  Record {
    int id PK
    ExerciseType exerciseType
    string description
    int time
    int distance
    string[] photos
    int authorId FK
    int groupId FK
    datetime createdAt
    datetime updatedAt
  }

  Tag {
    int id PK
    string name
    datetime createdAt
    datetime updatedAt
    int groupId FK
  }

  Participant ||--o{ Record : "author"
  Participant }|--|| Group : "group"
  Group ||--o{ Record : "group"
  Group ||--o{ Participant : "participants"
  Group ||--o{ Tag : "GroupTags"
  Record }|--|| Group : "group"
  Record }|--|| Participant : "author"
  Group }|--|| Tag : "GroupTags"

  enum BadgeType {
    PARTICIPATION_10
    RECORD_100
    LIKE_100
  }

  enum ExerciseType {
    RUN
    BIKE
    SWIM
  }
```
