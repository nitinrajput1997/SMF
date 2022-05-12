# SMF

It is a control plane function in a 5G core network. SMF's main function is PDU Session Management.

**PDU Session Management**<br />
It is simply a logical connection between the device and the end of the user plane function (upf) which in turns connect to the data network (DN) through N6 interface.This logical connection is called PDU Session.

PDU Session Management is all the activities like setting up or modifying or releasing these PDU sessions. Everytime PDU session is created, a connectivity is created towards a specific network and the device gets a corresponding IP address if it is IP based PDU session. A device does not need to have only one PDU session, it can have multiple PDU session.

**Properties**<br />
1. PDU Session Identifier: It has identifierto get easily identify while having multiple PDU sessions.<br />
2. Slice Identifier: Every PDU session is a part of network slice so even slicing features is not supported at early stages of 5G, there is always a default network slice that is a part of 5G network. So slice identifier defines which network slice Pdu session belongs to.<br />
3. DNN: Defines which data network that PDU session provides connectivity to. Eg- Internet, IMS, Enterprise.<br />
4. PDU Session Type <br />
5. Service and Session Continuity(SSC)<br />
6. User Plane Security Enforcement Information, this indicates whether the userplane traffic needs to be safer and if its needs to use integrity protection. Based on that information , ciphering and integrity protection are activated or deactivated for particular PDU session.
