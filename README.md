```mermaid
graph TD
    %% Define Data Centers
    PrimaryDC[Riyadh Data Center] -->|Physical Link| BranchRiyadh[Branch LAN - Riyadh]
    PrimaryDC -->|Physical Link| BranchJeddah[Branch LAN - Jeddah]
    SecondaryDC[Jeddah Data Center] -->|Physical Link| BranchDammam[Branch LAN - Dammam]
    PrimaryDC -->|Redundant Link| SecondaryDC

    %% Define Branch LANs
    subgraph BranchRiyadh
        ATM1[ATM 1] -->|Data Link| RouterRiyadh[Router - Riyadh]
        Workstation1[Workstation 1] -->|Data Link| RouterRiyadh
        CustomerService[Customer Service Workstation] -->|Data Link| RouterRiyadh
        TransactionProcessing[Transaction Processing Workstation] -->|Data Link| RouterRiyadh
        ITSupport[IT Support Workstation] -->|Data Link| RouterRiyadh
        HR[HR Workstation] -->|Data Link| RouterRiyadh
        RouterRiyadh -->|Data Link| PrimaryDC
    end

    %% Define Branch LANs for Jeddah
    subgraph BranchJeddah
        ATM2[ATM 2] -->|Data Link| RouterJeddah[Router - Jeddah]
        Workstation2[Workstation 2] -->|Data Link| RouterJeddah
        CustomerServiceJeddah[Customer Service Workstation] -->|Data Link| RouterJeddah
        TransactionProcessingJeddah[Transaction Processing Workstation] -->|Data Link| RouterJeddah
        ITSupportJeddah[IT Support Workstation] -->|Data Link| RouterJeddah
        HRJeddah[HR Workstation] -->|Data Link| RouterJeddah
        RouterJeddah -->|Data Link| PrimaryDC
    end

    %% Define Branch LAN for Dammam
    subgraph BranchDammam
        ATM3[ATM 3] -->|Data Link| RouterDammam[Router - Dammam]
        Workstation3[Workstation 3] -->|Data Link| RouterDammam
        CustomerServiceDammam[Customer Service Workstation] -->|Data Link| RouterDammam
        TransactionProcessingDammam[Transaction Processing Workstation] -->|Data Link| RouterDammam
        ITSupportDammam[IT Support Workstation] -->|Data Link| RouterDammam
        HRDammam[HR Workstation] -->|Data Link| RouterDammam
        RouterDammam -->|Data Link| SecondaryDC
    end

    %% Define Internet and Customer Packets
    Internet[Internet Gateway] -->|Customer Packet Route| PrimaryDC
    Internet -->|Customer Packet Route| SecondaryDC

