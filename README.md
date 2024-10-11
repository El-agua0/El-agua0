```mermaid
graph TD
    %% Define Data Centers
    PrimaryDC[Riyadh Data Center] -->|Physical Link| BranchRiyadh[Branch LAN - Riyadh]
    PrimaryDC -->|Physical Link| BranchJeddah[Branch LAN - Jeddah]
    SecondaryDC[Jeddah Data Center] -->|Physical Link| BranchDammam[Branch LAN - Dammam]
    PrimaryDC -->|Redundant Link| SecondaryDC

    %% Define Workstations and ATMs in Riyadh Branch
    subgraph BranchRiyadh
        ATM1[ATM 1] -->|Data Link| RouterRiyadh[Router - Riyadh]
        Workstation1[Workstation 1] -->|Data Link| RouterRiyadh
        RouterRiyadh -->|Data Link| PrimaryDC
    end

    %% Define Workstations and ATMs in Jeddah Branch
    subgraph BranchJeddah
        ATM2[ATM 2] -->|Data Link| RouterJeddah[Router - Jeddah]
        Workstation2[Workstation 2] -->|Data Link| RouterJeddah
        RouterJeddah -->|Data Link| PrimaryDC
    end

    %% Define Internet and Customer Packets
    Internet[Internet Gateway] -->|Customer Packet Route| PrimaryDC
    Internet -->|Customer Packet Route| SecondaryDC
