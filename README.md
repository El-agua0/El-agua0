```mermaid
graph TD
    %% Define Data Centers
    PrimaryDC[Riyadh Data Center] -->|Physical Link| BranchRiyadh[Branch LAN - Riyadh]
    PrimaryDC -->|Physical Link| BranchJeddah[Branch LAN - Jeddah]
    SecondaryDC[Jeddah Data Center] -->|Physical Link| BranchJeddah
    PrimaryDC -->|Redundant Link| SecondaryDC

    %% Define Branch LANs for Riyadh
    subgraph BranchRiyadh
        ATM1[ATM 1] -->|Data Link| RouterRiyadh[Router - Riyadh]
        Workstation1[Workstation 1] -->|Data Link| RouterRiyadh
        CustomerService1[Customer Service Workstation] -->|Data Link| RouterRiyadh
        TransactionProcessing1[Transaction Processing Workstation] -->|Data Link| RouterRiyadh
        ITSupport1[IT Support Workstation] -->|Data Link| RouterRiyadh
        HR1[HR Workstation] -->|Data Link| RouterRiyadh
        Marketing1[Marketing Workstation] -->|Data Link| RouterRiyadh
        Operations1[Operations Workstation] -->|Data Link| RouterRiyadh
        RouterRiyadh -->|Data Link| PrimaryDC
    end

    %% Define Branch LANs for Jeddah
    subgraph BranchJeddah
        ATM2[ATM 2] -->|Data Link| RouterJeddah[Router - Jeddah]
        Workstation2[Workstation 2] -->|Data Link| RouterJeddah
        CustomerService2[Customer Service Workstation] -->|Data Link| RouterJeddah
        TransactionProcessing2[Transaction Processing Workstation] -->|Data Link| RouterJeddah
        ITSupport2[IT Support Workstation] -->|Data Link| RouterJeddah
        HR2[HR Workstation] -->|Data Link| RouterJeddah
        Marketing2[Marketing Workstation] -->|Data Link| RouterJeddah
        Operations2[Operations Workstation] -->|Data Link| RouterJeddah
        RouterJeddah -->|Data Link| PrimaryDC
    end

    %% Define Internet and Customer Packets
    Internet[Internet Gateway] -->|Customer Packet Route| PrimaryDC
    Internet -->|Customer Packet Route| SecondaryDC

