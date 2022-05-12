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

**Types Of PDU Session**<br />
1. IP Based PDU Session<br />
    In this , PDU session carries the IP traffic and it supports IPv4, IPv6 and dual-stack traffic. In this, SMF holds the responsibility to allocate the IP address to the device. So when the PDU session is created , the device can request either IPv4, IPv6 or dual-stack IPv4v6.

2. Ethernet PDU Session<br />
    It is newly introduced in 5G. It provides connectivity between the device and the Layer-2 Network. If we see, IP is a Layer-3 protocol. Sometime a device want to connect at Layer-2 data network. In such case 5G supports Ethernet PDU Session. In this, PDU session will not carry IP packets instead of that it carries ethernet frames between device and the data network. It supports SSC Mode 1 and 2. Since there is no IP address is used so how the routing will happens. There are some solution to make routing possible as follows:<br />
    MAC address learning in SMF/AMF
    DN may provides the MAC address
    Point-to-point tunnel between the device and data network

3. Unstructured PDU Session <br />
    Here user data is treated as unstructured bits, the 5G networks thinks it does not know anything about the nature of thw traffic added over this PDU session. This is used to carry IOT related protocols such as MQTT, 6LoPAN etc. There is no addressing so there is no Layer-2 or 3 because it does not know IP or internet frames. There is no QoS differentiation of the data that is transmitted in a unstructured. They get default priorities from the perspective of QoS. It supports Mode 1 and 2.

**SMF Services**<br />
There are two main services as follows:  

1. Nsmf_PDUSession Service<br />
    It manages the PDU Session. It has includes functions:<br />
    1. Nsmf_PDUSession_Create<br />
      Used to create a new PDU session in H(home)-SMF.<br />
    2. Nsmf_PDUSession_Update<br />
      Used between the V(visitor)-SMF and H-SMF in roaming scenarios to update the established PDU session.<br />
    4. Nsmf_PDUSession_Release<br />
      Used in roaming scenario bu V-SMF to request thw H-SMF to release PDU Session.<br />
    5. Nsmf_PDUSession_StatusNotify<br />
      Used in roaming scenario by the H-SMF to notify V-SMF.<br />
    6. Nsmf_PDUSession_CreateSMContext<br />
      Used by AMF to creates an AMF-SMF association to support a PDU Session.<br />
    7. Nsmf_PDUSession_UpdateSMContext<br />
      Used by AMF to updates an AMF-SMF association to support a PDU Session.<br />
    8. Nsmf_PDUSession_ReleaseSMContext<br />
      Used by AMF to release the AMF-SMF association.<br />
    9. Nsmf_PDUSession_SMContextStatusNotify<br />
      Used by SMF to notify the AMF when PDU Session is released.<br />
    10. Nsmf_PDUSession_ContextRequest<br />
      Used by AMF to fetch the SM-Context during handover to EPS.<br />

2. Nsmf_EventExposure Service<br />
   It is used to subscribe and get notified about eventd related to PDU session. Exposes the information about PDU session related events like: UE address or Prefix change, PDU session release, User Plane path change, PLMN chnages. Event filter can be used.
