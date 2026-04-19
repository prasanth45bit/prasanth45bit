# PROPOSED METHODOLOGY (Flow Chart)

```mermaid
flowchart TD
    classDef orange fill:#fdb761,stroke:#000,stroke-width:1.5px,rx:5px,ry:5px,color:#000;
    classDef purple fill:#9598f8,stroke:#000,stroke-width:1.5px,rx:5px,ry:5px,color:#000;
    classDef pink fill:#ff8aff,stroke:#000,stroke-width:1.5px,color:#000;
    classDef blue fill:#72d6fc,stroke:#000,stroke-width:1.5px,rx:5px,ry:5px,color:#000;
    classDef teal fill:#8de2da,stroke:#000,stroke-width:1.5px,rx:5px,ry:5px,color:#000;

    %% Entry Point
    Ident[User Authentication]:::orange
    
    %% Setup & Discovery
    subgraph Discovery Process
    direction LR
      Profiles[User Profile Setup<br/>(Skills, Portfolio)]:::purple
      Events[Hackathon Discovery]:::purple
    end
    
    Ident --> Profiles
    Ident --> Events

    %% Team Formation
    Team[Team Formation & Join Request]:::purple
    Profiles --> Team
    Events --> Team

    %% Decision Node
    Approve{Join Request<br/>Approved?}:::pink
    Team --> Approve

    %% Rejection Loop
    Reject[Review Feedback]:::blue
    Refine[Update Profile]:::blue
    Browse[Search Other Teams]:::blue
    
    Approve -- NO --> Reject
    Reject --> Refine
    Refine --> Browse
    Browse --> Team

    %% Workspace Setup
    Init[Workspace Initialization]:::teal
    Approve -- YES --> Init

    %% Collaboration Features
    subgraph Active Collaboration
    direction LR
      Chat[Real-Time Chat<br/>(Socket.IO)]:::teal
      Task[Kanban Task Board<br/>(Drag & Drop)]:::teal
      Docs[Resource Sharing]:::teal
    end

    Init --> Chat
    Init --> Task
    Init --> Docs

    %% Final Step
    Finish[Project Submission]:::orange
    Chat --> Finish
    Task --> Finish
    Docs --> Finish
