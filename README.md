```mermaid
graph TD
    %% Define Data Centers
    PrimaryDC[Riyadh Data Center] --> BranchRiyadh[Branch LAN - Riyadh]
    PrimaryDC --> BranchJeddah[Branch LAN - Jeddah]
    SecondaryDC[Jeddah Data Center] --> BranchDammam[Branch LAN - Dammam]
    PrimaryDC --> SecondaryDC

    %% Define Workstations and ATMs in Riyadh Branch
    subgraph BranchRiyadh
        ATM1[ATM 1] --> RouterRiyadh[Router - Riyadh]
        Workstation1[Workstation 1] --> RouterRiyadh
        RouterRiyadh --> PrimaryDC
    end

    %% Define Workstations and ATMs in Jeddah Branch
    subgraph BranchJeddah
        ATM2[ATM 2] --> RouterJeddah[Router - Jeddah]
        Workstation2[Workstation 2] --> RouterJeddah
        RouterJeddah --> PrimaryDC
    end

    %% Define Internet and Customer Packets
    Internet[Internet Gateway] --> PrimaryDC
    Internet --> SecondaryDC
