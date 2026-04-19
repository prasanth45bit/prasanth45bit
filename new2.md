# PROPOSED METHODOLOGY (Flow Chart)

```mermaid
flowchart TD
    Start([Start])

    Auth[User Authentication]
    Discover[Hackathon Discovery]
    Team[Team Formation]

    Decision{Join Approved?}

    Workspace[Workspace Initialization]
    Collab[Chat + Kanban + Resources]

    Feedback[Update Profile & Retry]

    Submit[Project Submission]
    End([End])

    Start --> Auth --> Discover --> Team --> Decision

    Decision -- Yes --> Workspace --> Collab --> Submit --> End
    Decision -- No --> Feedback --> Team
