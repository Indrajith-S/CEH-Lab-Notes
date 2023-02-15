- Many IoT devices such as security cameras host websites for controlling or configuring cameras from remote locations. These websites mostly implement the insecure HTTP protocol instead of the secure HTTPS protocol and are, hence, vulnerable to various attacks. If the cameras use the default factory credentials, an attacker can easily intercept all the traffic flowing between the camera and web applications and further gain access to the camera itself. Attackers can use tools such as Wireshark to intercept such traffic and decrypt the Wi-Fi keys of the target network.


### Capture and Analyze IoT Traffic using Wireshark

- Open Terminal (in ubuntu)
	> sudo snap install mqtt-explorer (to install the MQTT Explorer tool)
	- MQTT Explorer is a comprehensive MQTT client that provides a structured overview of your MQTT topics and simplifies working with devices/services on your broker.

- Open Wireshark (in parrot/kali)
- Double-click the interface icon in front of **SSH remote capture: sshdump** option.
- Under **Server** tab of the **Wireshark Interface Options** window, enter Ubuntu's machine IP address for **Remote SSH server address** and **22** for **Remote SSH server port**. Switch to **Authentication** tab.
- Under **Authentication** tab of the **Wireshark Interface Options** window, enter username of ubuntu machine for **Remote SSH server username** and password of ubuntu machine for **Remote SSH server password**. Switch to **Capture** tab.
- Under **Capture** tab of the **Wireshark Interface Options** window, enter **eth0** for **Remote interface** and **not port 22** for **Remote capture filter**, and click **Start**.
	- Here, **eth0** is the interface in the Ubuntu machine from where we have to capture traffic and **not port 22** instructs Wireshark to filter out SSH traffic from the capture.


- switch back to ubuntu
	> mqtt-explorer (to launch MQTT Explorer tool)
	- In the **MQTT Connection** window, enter the **Host** as **mqtt.eclipseprojects.io** and click **CONNECT**.
	- **MQTT Explorer** starts establishing a connection with the devices mentioned in the left pane.
	- Wait for some time (~ 2 minute), and then click **DISCONNECT** in the top section of the **MQTT Explorer** window to disconnect the tool.

- Switch to parrot or kali
- In the **Wireshark** window, click the **Stop** button to stop capturing the packets.
- Now, in the **Apply a display filter** field, type **mqtt** and press **Enter** to display only the MQTT protocol packets.


- Select a **Connect Command** packet from the **Packet List** pane. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol** and **MQ Telemetry Transport Protocol** nodes.
- Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Protocol Name**, **Version**, and **Client ID**.
	> Note: The MQTT protocol establishes a connection between clients through a broker. A CONNECT command is sent to initiate a connection from the client to the broker. After the connection is established, it remains active until a disconnect command is sent from the client. Some of the headers of the CONNECT command are given below:
	> - Header Flags: Contains information regarding the MQTT control packet type.
	> - Connect Flags: Contains parameters specifying the behavior of the MQTT connection.
	> - Clean Session: Indicates whether the client wants to establish a persistent connection with the broker or not.
	> - Client ID: Indicates a unique identifier for each MQTT client connecting to an MQTT broker.


- Select a **Connect Ack** packet from the **Packet List** pane. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
- Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Header Flag** and **Return Code**.
	> Note: The broker sends the Connect Ack packet on receiving a Connect command request from the client. Some of the headers in the Connect Ack packet are given below:
	> - Header Flags: Contains information regarding the MQTT control packet type.
	> - Session Present: Indicates the session between the broker and client; Bit 0 is the Connection Ack bit in the session present flag.
	> - Return Code: The values and responses of the return code are summarized in the table below:
	> 	![[Pasted image 20220805150642.png]]
	

- Select a **Subscribe Request** packet from the **Packet List** pane. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
- Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Msg Len**, **Message Identifier**, and **Topic Length**.
	> Note: To receive a relevant message, a client sends a SUBSCRIBE message to an MQTT broker. Some of the headers in the Subscribe Request packet are given below:
	> - Header Flags: Contains information regarding the MQTT control packet type.
	> - Message Identifier: Identifies a message in a message flow between a client and a broker.
	> - Topic and QoS Level: A subscription is a pair of a topic filter and a QoS level; the topic defines a subject of interest on which the client would like to get messages.
	> - Payload: Contains a list of subscriptions.
	

- Select a **Subscribe Ack** packet from the **Packet List** pane. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
- Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Msg Len** and **Message Identifier**.
	> Note: The MQTT broker confirms subscription by sending an acknowledgment back to the client using a SUBACK message. Some of the headers in the Subscribe Acknowledgement packet are given below:
	> - Header Flags: Contains information regarding the MQTT control packet type.
	> - Message Identifier: Identifies a message in a message flow between a client and a broker.
	> - Payload: Contains a list of return codes.
	> - Return Code: For each Topic/QoS pair received, a return is sent by the MQTT broker in the SUBSCRIBE message; the return code is in line with the QoS level in the case of a success.
	> - The values and responses of the return code are summarized in the table below:
			- ![[Pasted image 20220805150857.png]]



- Select any **Publish Message** packet from the **Packet List** pane. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
- Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Msg Len**, **Topic Length**, **Topic**, and **Message**.
- Publish Message can be used to obtain the message sent by the MQTT client to the broker.
	> Note: After establishing a successful connection with the MQTT broker, the MQTT client can publish messages. The headers in the Publish Message packet are given below:
	> - Header Flags: Contains information regarding the MQTT control packet type.
	> - DUP flag: If the DUP flag is 0, it indicates the first attempt at sending this PUBLISH packet; if the flag is 1, it indicates a possible re-attempt at sending the message.
	> - QoS: Determines the assurance level of a message.
	> - Retain Flag: If the retain flag is set to 1, the server must store the message and its QoS, so it can cater to future subscriptions matching the topic.
	> - Topic Name: Contains a UTF-8 string that can also include forward slashes when it needs to be hierarchically structured.
	> - Message: Contains the actual data to be transmitted.
	> - Payload: Contains the message that is being published.
	

- Select any **Publish Release** packet from the **Packet List** pane. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
- Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Msg Len**, **Message Type**, **Message Identifier**.
	> Note: A Publish Release (PUBREL) packet is the response to a Publish Received (PUBREC) packet.
	

- Now, scroll down, look for the **Publish Complete** packet from the **Packet List** pane, and click on it. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
- Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Msg Len** and **Message Identifier**.
	> Note: The Publish Complete (PUBCOMP) packet is the response to a Publish Release (PUBREL) packet.
	
