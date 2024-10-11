graph TD;
  
  %% Physical links %%
  A[Customer's Device] -->|Physical Link: Internet Service Provider| B[Branch Router];
  B -->|Physical Link: Ethernet| C[Branch LAN - Switch];
  C -->|Physical Link: Fiber Optic| D[WAN Router];
  D -->|Physical Link: Wide Area Network (WAN)| E[Headquarters Router];
  E -->|Physical Link: Ethernet| F[Headquarters LAN - Switch];
  F -->|Physical Link: Server Connection| G[Main Bank Server];

  %% Data-links %%
  C ---|Data-link Layer: Frame moves within Branch LAN| H[Branch Switch];
  F ---|Data-link Layer: Frame moves within HQ LAN| I[Data Center Switch];

  %% Packet Routes %%
  A -->|Packet Route: Customer sends packet to Branch Router| B;
  B -->|Packet Route: Router forwards packet to WAN| D;
  D -->|Packet Route: Packet routed to Headquarters Router| E;
  E -->|Packet Route: Packet delivered to Main Bank Server| G;
  G -->|Packet Route: Server response back to Headquarters Router| E;
  E -->|Packet Route: Response packet forwarded to WAN Router| D;
  D -->|Packet Route: Back to Branch Router| B;
  B -->|Packet Route: Finally back to Customer's Device| A;

  %% Descriptions %%
  click A "https://example.com/customer-device" "Customer initiates request";
  click G "https://example.com/server" "Server processes the transaction";

  %% Styles %%
  style A fill:#f9f,stroke:#333,stroke-width:2px;
  style G fill:#bbf,stroke:#333,stroke-width:2px;
  style B fill:#ff9,stroke:#333,stroke-width:2px;
  style C fill:#aff,stroke:#333,stroke-width:2px;
  style D fill:#faa,stroke:#333,stroke-width:2px;
  style E fill:#9ff,stroke:#333,stroke-width:2px;
  style F fill:#cff,stroke:#333,stroke-width:2px;
