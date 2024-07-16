# Smart contracts

### Device Contract

| **Field**      | **Type**      | **Device** | **Node** | **Ever** | **Description**                                      |
|----------------|---------------|------------|----------|----------|------------------------------------------------------|
| address        | address       | v          | v        | v        | Address in Ever network                              |
| node           | address       | v          | v        | x        | Address of the corresponding node in the network     |
| elector        | address       | v          | v        | x        | Address of the elector in the network                |
| vendor         | address       | v          | v        | x        | Address of the vendor deploying the smart contract   |
| owners         | []address     | v          | v        | x        | Array of owner addresses with access to the device   |
| active         | bool          | v          | v        | v        | Active indicator (true/false)                        |
| lock           | bool          | v          | v        | v        | Lock indicator for certain actions                   |
| stat           | bool          | v          | v        | v        | Flag for sending statistics                          |
| type           | string        | v          | v        | v        | Device type in text format                           |
| version        | string        | v          | v        | v        | Device firmware version                              |
| vendorName     | string        | v          | v        | ?        | Vendor name                                          |
| vendorData     | string        | v          | x        | x        | Vendor data in any convenient format, encrypted      |

**Stored Data**:
- Device characteristics
- Encrypted vendor data (e.g., serial number)
- User binding
- Vendor binding
- Elector binding
- Node where the device is registered
- Device activity flag
- Device lock flag
- Flags for telemetry and event collection

**Usage**:
- Service charge deductions
- Determining user access rights to the device
- Finding the node to interact with the device
- Providing the vendor with device information
- Retrieving general device information (type, firmware, etc.)
- Managing the device (firmware update, reboot, information retrieval, etc.)

---

### Vendor Contract

| **Field**      | **Type**      | **Device** | **Node** | **Ever** | **Description**                                      |
|----------------|---------------|------------|----------|----------|------------------------------------------------------|
| address        | address       | v          | v        | x        | Address                                              |
| elector        | address       | v          | v        | x        | Address of the elector                               |
| vendorName     | string        | v          | v        | x        | Vendor name                                          |
| profitShare    | int (0-100%)  | v          | x        | v        | Profit share percentage (0-100%)                     |
| ownerInfo      | string        | v          | x        | v        | Owner information                                    |

**Stored Data**:
- Vendor data
- Name
- Contact
- Fund distribution between vendor and node

**Usage**:
- Revenue receipt
- Access to device data

---

### Node Contract

| **Field**      | **Type**      | **Device** | **Node** | **Ever** | **Description**                                      |
|----------------|---------------|------------|----------|----------|------------------------------------------------------|
| address        | address       | v          | v        | v        | Address in Ever network                              |
| elector        | address       | v          | x        | v        | Address of the elector in the network                |
| ipPort         | string        | v          | v        | v        | IP and port to contact the node                      |
| ownerInfo      | string        | v          | x        | v        | Owner information                                    |

**Stored Data**:
- Node address in the network
- Owner contact

**Usage**:
- Participation in node elections
- Service fee deductions from the device

---

### Owner Contract

| **Field**      | **Type**      | **Device** | **Node** | **Ever** | **Description**                                      |
|----------------|---------------|------------|----------|----------|------------------------------------------------------|
| address        | address       | v          | v        | x        | Address in Ever network                              |

**Stored Data**:
- Address in the Ever network

**Usage**:
- Funds deduction/receipt
- Calling device smart contract methods

---

### Elector Contract

| **Field**      | **Type**      | **Device** | **Node** | **Ever** | **Description**                                      |
|----------------|---------------|------------|----------|----------|------------------------------------------------------|
| address        | address       | v          | v        | v        | Elector address in Ever network                      |
| currentNodes   | []address     | v          | x        | x        | Array of active node addresses                       |
| nextNodes      | []address     | v          | x        | x        | Array of nodes selected for the next cycle           |

**Stored Data**:
- Elector address in the Ever network
- Active node addresses
- Nodes selected for the next cycle

**Usage**:
- Ensuring node elections and transactions
- Storing the list of nodes participating in the cycle

### Custom smart contracts
You can create your own smart contracts to extend current device functions or integrate devices with each other and third-party systems.