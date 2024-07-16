# Smart Contracts
### Device Contract

| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| node               | address           | Address of the corresponding node in the network     |
| elector            | address           | Address of the elector in the network                |
| vendor             | address           | Address of the vendor deploying the smart contract   |
| group              | address           | Address of the device group                          |
| owners             | mapping(uint256 => address) | Array of owner addresses with access to the device   |
| active             | bool              | Active indicator (true/false)                        |
| lock               | bool              | Lock indicator for certain actions                   |
| stat               | bool              | Flag for sending statistics                          |
| events             | bool              | Flag for events                                      |
| dtype              | string            | Device type in text format                           |
| version            | string            | Device firmware version                              |
| vendorName         | string            | Vendor name                                          |
| vendorData         | string            | Vendor data in any convenient format, preferably encrypted |
| lastRegisterTime   | uint32            | Last registration time of the device                 |

| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| `setNode(address node)`               | Set current node address for the device                                                         |
| `getNode() public view returns (address)`  | Get current node address for the device                                                         |
| `getElector() public view returns (address)` | Get elector address for the device                                                             |
| `getVendor() public view returns (address)`  | Get vendor address for the device                                                              |
| `getVendorData() public view returns (string)` | Get vendor data for the device                                                                |
| `getLastRegisterTime() public view returns (uint32)` | Get last registration time of the device                                                      |
| `_sendUpdate() private view`          | Send update event to node                                                                      |

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

### Device Group Contract

| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| N/A                | N/A               | This contract was not specified in detail            |

| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| N/A                                   | This contract was not specified in detail                                                      |

**Stored Data**:
- N/A

**Usage**:
- N/A

---

### Elector Contract

| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| address            | address           | Elector address in Ever network                      |
| currentNodes       | address[]         | Array of active node addresses                       |
| nextNodes          | address[]         | Array of nodes selected for the next cycle           |

| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| N/A                                   | This contract was not specified in detail                                                      |

**Stored Data**:
- Elector address in the Ever network
- Active node addresses
- Nodes selected for the next cycle

**Usage**:
- Ensuring node elections and transactions
- Storing the list of nodes participating in the cycle

---

### Node Contract

| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| address            | address           | Address in Ever network                              |
| elector            | address           | Address of the elector in the network                |
| ipPort             | string            | IP and port to contact the node                      |
| ownerInfo          | string            | Owner information                                    |

| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| N/A                                   | This contract was not specified in detail                                                      |

**Stored Data**:
- Node address in the network
- Owner contact

**Usage**:
- Participation in node elections
- Service fee deductions from the device

---

### Vendor Contract

| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| address            | address           | Address                                              |
| elector            | address           | Address of the elector                               |
| vendorName         | string            | Vendor name                                          |
| profitShare        | uint (0-100%)     | Profit share percentage (0-100%)                     |
| ownerInfo          | string            | Owner information                                    |

| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| N/A                                   | This contract was not specified in detail                                                      |

**Stored Data**:
- Vendor data
- Name
- Contact
- Fund distribution between vendor and node

**Usage**:
- Revenue receipt
- Access to device data

---

### Owner Contract

| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| address            | address           | Address in Ever network                              |

| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| N/A                                   | This contract was not specified in detail                                                      |

**Stored Data**:
- Address in the Ever network

**Usage**:
- Funds deduction/receipt
- Calling device smart contract methods