
# Smart Contracts
1. [Device Contract](#Device-Contract)
2. [Device Group Contract](#Device-Group-Contract)
3. [Elector Contract](#Elector-Contract)
4. [Node Contract](#Node-Contract)
5. [Vendor Contract](#Vendor-Contract)
6. [Owner Contract](#Owner-Contract)

### Device Contract

**Fields:**
| **Field**          | **Type**                 | **Description**                                      |
|--------------------|--------------------------|------------------------------------------------------|
| owners             | mapping(uint256 => address) | Device owners: public_key => contract_address(if exists) |
| dtype              | string                   | Device type                                          |
| version            | string                   | Firmware version                                     |
| lastRegisterTime   | uint32                   | Last registration timestamp                          |
| group              | address                  | Address of DeviceGroup contract                      |
| node               | address                  | Current node address                                 |
| elector            | address                  | Elector contract address                             |
| vendor             | address                  | Vendor contract address                              |
| vendorName         | string                   | Readable name of vendor                              |
| vendorData         | string                   | Vendor data                                          |
| active             | bool                     | Device active/inactive for IoT services              |
| lock               | bool                     | Device lock/unlock for management                    |
| stat               | bool                     | Enable/disable collecting statistics                 |
| events             | bool                     | Enable/disable sending events                        |

**Methods:**
| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| `get() public view returns (address, address, address, mapping(uint256 => address), bool, bool, bool, bool, string, string, string, string, uint32)` | Get all contract data                    |
| `setNode(address node) public`        | Set current node address for the device                                                         |
| `getNode() public view returns (address)` | Get current node address for the device                                                      |
| `getElector() public view returns (address)` | Get elector address for the device                                                         |
| `getVendor() public view returns (address)`  | Get vendor address for the device                                                          |
| `getVendorData() public view returns (string)` | Get vendor data for the device                                                           |
| `getLastRegisterTime() public view returns (uint32)` | Get last registration time of the device                                               |
| `setActive(bool active) public`       | Set device active/inactive status                                                               |
| `setStat(bool stat) public`           | Enable/disable collecting statistics                                                            |
| `setEvents(bool events) public`       | Enable/disable sending events                                                                   |
| `setGroup(address group) public`      | Set the group address for the device                                                            |
| `sendTransaction(address dest, uint128 value) public` | Send tokens to destination address                                                     |
| `upgrade(TvmCell code) external`      | Upgrade contract code                                                                           |
| `deviceEvent(string name, string data) public view` | Emit a custom device event                                                              |
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

**Fields:**
| **Field**      | **Type**                 | **Description**                                      |
|----------------|--------------------------|------------------------------------------------------|
| owners         | mapping(uint256 => address) | Device group owners: public_key => contract_address(if exists) |
| devices        | mapping(address => uint256) | List of group devices: contract_address => public_key(optional) |
| name           | string                   | Group name                                           |
| elector        | address                  | Elector contract address                             |
| active         | bool                     | Active indicator                                     |

**Methods:**
| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| `get() public view returns (string, address, mapping(uint256 => address), mapping(address => uint256), bool)` | Get all contract data                                    |
| `getElector() public view returns (address)` | Get elector address for device                                                           |
| `getOwners() public view returns (mapping(uint256 => address))` | Get device group owners list                                                            |
| `getDevicesCount() public view returns (uint256)` | Get the count of devices in the group                                                    |
| `setActive(bool active) public`       | Set the group active/inactive status                                                       |
| `transferToElector(uint128 value) public view` | Transfer tokens to elector contract                                                    |
| `transfer(address dest, uint128 value) public view` | Transfer tokens to a destination address for owners                                   |
| `setDevice(address addr, uint256 pubKey) public` | Add or update a device in the group                                                      |
| `removeDevice(address addr) public`   | Remove a device from the group by address                                                  |
| `upgrade(TvmCell code) external`      | Upgrade the contract code                                                                 |

**Stored Data**:
- Device group owners
- List of group devices
- Group name
- Elector contract address
- Active status

**Usage**:
- Managing device group membership
- Storing and retrieving device group details
- Transferring funds within the group
- Activating or deactivating the group

---

### Elector Contract

**Fields:**
| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| nodesCurrent       | address[]         | List of current nodes                                |
| nodesNext          | address[]         | List of next nodes                                   |
| nodesParticipants  | address[]         | List of all nodes that want to participate in the election |
| nodesFault         | mapping(address => uint) | List of nodes with fault counts                         |
| contractVersion    | uint32            | Current contract version                             |

**Methods:**
| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| `getPayment(address group) public pure` | Get tokens from DeviceGroup by transferring to elector                                        |
| `setNodes(address[] _nodes) public`   | Set current period nodes                                                                       |
| `currentList() public view returns (address[] nodes)` | Return current period nodes                                                         |
| `participantList() public view returns (address[] participants)` | Return next period participants                                             |
| `takeNextRound(address _address) public` | Add node to next round                                                                 |
| `reportFaultNode(address _address) public` | Increase fault node counter, if counter >= 5 then remove node from current list     |
| `kickNode(address _address) private`  | Remove node from current list by address                                                   |
| `arrayIndex(address value, address[] array) private pure returns (int)` | Check if address value exists in array, returns index if exists, -1 otherwise |
| `v() public view returns (uint32 contractVersion)` | Get current contract version                                                         |
| `upgrade(TvmCell code) external`      | Upgrade contract code                                                                       |

**Stored Data**:
- List of current nodes
- List of next nodes
- List of all nodes that want to participate in the election
- List of nodes with fault counts

**Usage**:
- Ensuring node elections and transactions
- Managing participation of nodes in current and next cycles
- Handling fault reports and removing faulty nodes
- Upgrading the contract code

---

### Node Contract

**Fields:**
| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| elector            | address           | Address of the elector in the network                |
| ipPort             | string            | IP and port to contact the node                      |
| contactInfo        | string            | Owner contact information                            |
| contractVersion    | uint32            | Current contract version                             |

**Methods:**
| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| `get() public view returns (address, string, string)` | Get all contract data                                                                        |
| `deviceRegister(address device, address oldnode) public pure` | Emit DeviceRegister event with device and old node addresses                          |
| `deviceUpdate(address device) public pure` | Emit DeviceUpdate event with device address                                                |
| `getElector() public view returns (address)` | Get elector address for the node                                                             |
| `getIpPort() public view returns (string)` | Get IP and port for the node                                                                 |
| `getContactInfo() public view returns (string)` | Get owner contact information                                                               |
| `setIpPort(string value) public`      | Set IP and port for the node                                                                  |
| `setContactInfo(string value) public` | Set owner contact information                                                                |
| `v() public view returns (uint32 contractVersion)` | Get current contract version                                                                |
| `upgrade(TvmCell code) external`      | Upgrade contract code                                                                         |

**Stored Data**:
- Elector address in the network
- IP and port for the node
- Owner contact information

**Usage**:
- Participation in node elections
- Service fee deductions from devices
- Registering and updating devices
- Managing node contact information

---

### Vendor Contract

**Fields:**
| **Field**          | **Type**          | **Description**                                      |
|--------------------|-------------------|------------------------------------------------------|
| elector            | address           | Address of the elector                               |
| vendorName         | string            | Vendor name                                          |
| profitShare        | uint (0-100%)     | Profit share percentage (0-100%)                     |
| contactInfo        | string            | Owner contact information                            |
| contractVersion    | uint32            | Current contract version                             |

**Methods:**
| **Method**                            | **Description**                                                                                 |
|---------------------------------------|-------------------------------------------------------------------------------------------------|
| `get() public view returns (address, string, uint, string)` | Get all contract data                                                                        |
| `getElector() public view returns (address)` | Get elector address for the vendor                                                        |
| `getVendorName() public view returns (string)` | Get vendor name                                                                           |
| `getProfitShare() public view returns (uint)` | Get profit share percentage                                                               |
| `getContactInfo() public view returns (string)` | Get owner contact information                                                             |
| `setVendorName(string value) public`  | Set vendor name                                                                             |
| `setProfitShare(uint value) public`   | Set profit share percentage                                                                 |
| `setContactInfo(string value) public` | Set owner contact information                                                              |
| `v() public view returns (uint32 contractVersion)` | Get current contract version                                                            |
| `upgrade(TvmCell code) external`      | Upgrade contract code                                                                       |

**Stored Data**:
- Elector address
- Vendor name
- Profit share percentage
- Owner contact information

**Usage**:
- Managing vendor-specific information
- Accessing and modifying vendor's profit share
- Retrieving and updating contact information
- Interacting with the elector contract
- Upgrading the contract code

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