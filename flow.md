# Hackathon Workflow

```mermaid
flowchart TD

%% Styles
classDef orange fill:#fdb761,stroke:#000,stroke-width:1.5px,rx:15px,ry:15px,color:#000;
classDef purple fill:#c6b6ff,stroke:#000,stroke-width:1.5px,rx:5px,ry:5px,color:#000;
classDef pink fill:#f7a6a6,stroke:#000,stroke-width:1.5px,color:#000;
classDef blue fill:#9fd3ff,stroke:#000,stroke-width:1.5px,rx:5px,ry:5px,color:#000;
classDef teal fill:#a8e6e1,stroke:#000,stroke-width:1.5px,rx:5px,ry:5px,color:#000;

%% Nodes
Start([Start]):::orange
Auth[User Authentication]:::orange
Discover[Hackathon Discovery]:::purple
TeamCreate[Team Creation]:::purple

Decision{Join Request Approved?}:::pink

Review[Review Feedback]:::blue
Update[Update Profile & Retry]:::blue

Workspace[Workspace Initialization]:::teal
Task[Task Assignment]:::teal
Resource[Resource Sharing]:::teal

End([End]):::orange

%% Flow
Start --> Auth --> Discover --> TeamCreate --> Decision

%% YES → Workspace Flow
Decision -- Yes --> Workspace
Workspace --> Task --> Resource --> End

%% NO → Retry Loop
Decision -- No --> Review
Review --> Update --> TeamCreate
