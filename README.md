graph TD;
  %% Physical links %%
  A[Customer's Device] -->|Physical Link: Internet Service Provider| B[Branch Router];
  B -->|Physical Link: Ethernet| C[Branch LAN - Switch];
  C -->|Physical Link: Fiber Optic| D[WAN Router];
  D -->|Physical Link: Wide Area Network (WAN)| E[Headquarters Router];
  E -->|Physical Link: Ethernet| F[Headquarters LAN - Switch];
  F -->|Physical Link: Server Connection| G[Main Bank Server];

  %% Data-links %%
  C ---|Data-link Layer: Frame moves within LAN| H[Branch Switch];
  F ---|Data-link Layer: Frame within HQ LAN| I[Data Center Switch];

  %% Packet Routes %%
  A -->|Packet Route: Packet sent from Customer to Branch Router| B;
  B -->|Packet Route: Packet routed through WAN| D;
  D -->|Packet Route: Packet routed through HQ Router| E;
  E -->|Packet Route: Packet delivered to Main Server| G;
  G -->|Packet Route: Response packet routed back to Customer| E;
  E -->|Packet Route: Back to Branch Router| D;
  D -->|Packet Route: Back to Customer's Device| A;

  %% Descriptions %%
  click A "https://example.com/customer-device" "Customer initiates request";
  click G "https://example.com/server" "Server processes the transaction";

  %% Styles %%
  style A fill:#f9f,stroke:#333,stroke-width:4px;
  style G fill:#bbf,stroke:#333,stroke-width:4px;

