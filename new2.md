# PROPOSED METHODOLOGY (Flow Chart)

```mermaid
flowchart TD
    classDef orange fill:#fdb761,stroke:#000,stroke-width:1.5px,color:#000;
    classDef purple fill:#9598f8,stroke:#000,stroke-width:1.5px,color:#000;
    classDef pink fill:#ff8aff,stroke:#000,stroke-width:1.5px,color:#000;
    classDef blue fill:#72d6fc,stroke:#000,stroke-width:1.5px,color:#000;
    classDef teal fill:#8de2da,stroke:#000,stroke-width:1.5px,color:#000;

    %% Start
    Start["Start"]:::orange

    %% User Flow
    Auth["User Authentication"]:::purple
    Profile["Profile Setup - Skills & Portfolio"]:::purple
    Discover["Hackathon Discovery"]:::purple
    Team["Team Formation & Join Request"]:::purple

    Start --> Auth
    Auth --> Profile
    Auth --> Discover
    Profile --> Team
    Discover --> Team

    %% Decision
    Approve{"Join Request Approved?"}:::pink
    Team --> Approve

    %% Rejection Flow
    Feedback["Review Feedback"]:::blue
    Update["Update Profile"]:::blue
    Browse["Search Other Teams"]:::blue

    Approve -- NO --> Feedback
    Feedback --> Update
    Update --> Browse
    Browse --> Team

    %% Approval Flow
    Workspace["Workspace Initialization"]:::teal
    Approve -- YES --> Workspace

    %% Collaboration
    Chat["Real-Time Chat - Socket.IO"]:::teal
    Task["Kanban Task Board"]:::teal
    Resource["Resource Sharing"]:::teal

    Workspace --> Chat
    Workspace --> Task
    Workspace --> Resource

    %% End
    Submit["Project Submission"]:::orange
    End["End"]:::orange

    Chat --> Submit
    Task --> Submit
    Resource --> Submit
    Submit --> End
