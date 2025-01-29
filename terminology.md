### General

| Term | Description |
| --- | --- |
| **IOT Node** | Gateway between IoT devices and Everscale. Provides physical connection with devices, two-way data exchange, telemetry aggregation, smart contract signing initiation, access control, and node operation management. |
| **Everscale** | Blockchain platform used for storing data and transactions related to IoT devices. |
| **Data Storage** | Data storage for telemetry, configurations, and events. |
| **APP** | Application for managing IoT devices and interacting with Everscale. |
| **Everscale API** | API for transmitting transactions between the device and Everscale. |
| **IOT/EVER SDK** | SDK for embedding in devices and interacting with Everscale. |


### Tech
| Term | Description |
| --- | --- |
| **COAP Protocol** | Protocol for data exchange between the device and the node, based on UDP. |
| **Device API Proxy** | API for transmitting commands between the DAPP and the device. |
| **Aliver** | Mechanism for maintaining a two-way connection with the device. |
| **NodeList Syncer** | Logic block responsible for syncing the node list and monitoring their operability. |
| **Private Key Storage** | Secure storage of the private key on the device. |
| **Data Synchronization** | Process of data synchronization between nodes, devices, and smart contracts. |
| **Encryption** | Process of encrypting requests and commands to ensure data security. |

### Smart Contracts

| Term | Description |
| --- | --- |
| **Node Contract** | Smart contract for managing nodes, syncing the node list, and monitoring their operability. |
| **Elector Contract** | Contract similar to validator contracts but uses different criteria for participant selection. |
| **Vendor Contract** | Vendor smart contract for receiving rewards and accessing certain data on devices. |
| **Device Group** | Smart contract that unites a group of devices. |
| **Device Contract** | Device smart contract storing characteristics, encrypted data, bindings to users and vendors, device management, and service fee deductions. |
| Device API Contract | The Device API contract describes the device management interface for a specific model and firmware version. It is created and maintained by the vendor. |
| **Owner Contract** | Device owner smart contract, usually representing a user wallet. |
