---

title: Intermediary system for interconnecting multiple IMS networks
abstract: An intermediary infrastructure that facilitates the interconnection of multiple IP Multimedia Subsystem (IMS) networks. The interconnections may span one or more of the IMS logical planes Services Plane, Control Plane, and Network or Transport Plane. The intermediary offers among other things a process, routing, and switching complex that is able to among other things process incoming messages including using a comprehensive routing repository to complete message routing operations.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08161192&OS=08161192&RS=08161192
owner: Sybase 365, Inc.
number: 08161192
owner_city: Reston
owner_country: US
publication_date: 20110207
---
This application is a continuation of U.S. application Ser. No. 12 112 187 filed Apr. 30 2008 which claims the benefit of U.S. Provisional Patent Application No. 60 915 730 filed on May 3 2007 both of which are herein incorporated by reference in their entireties.

The present invention relates generally to telecommunications services. More particularly the present invention relates to capabilities that enhance substantially the value and usefulness of various messaging paradigms including inter alia IP Multimedia Subsystem IMS .

As the wireless revolution continues to march forward the importance to a Mobile Subscriber MS for example a user of a Wireless Device WD such as a mobile telephone a BlackBerry etc. that is serviced by a Wireless Carrier WC of their WD grows substantially.

One consequence of such a growing importance is the resulting ubiquitous nature of WDs i.e. MSs carry them at almost all times and use them for an ever increasing range of activities.

Coincident with the social explosion of WDs technological advances have yielded among other things new communication paradigms such as IMS.

IMS is a standardized Next Generation Networking NGN architecture that among other things provides a framework for a collapsed mobile and fixed services infrastructure e.g. a form of Fixed Mobile Convergence FMC in support of possibly inter alia the ubiquitous delivery of a wide range of voice data multimedia etc. services to end users such as among others MSs .

Descriptions of the architecture function etc. of IMS may be found in various of the specification documents from the Third Generation Partnership Project 3GPP including for example Technical Specification 23.228.

The need exists for an infrastructure that allows the full universe of MSs through their WDs to seamlessly participate in the new communication environment paradigm IMS.

The present invention aspects of which may be characterized as IMS Exchange or IMS provides such capabilities and addresses various of the not insubstantial challenges that are associated with same. Among other things IMSmay 

1 Provide key interoperability capabilities across among other entities disparate fixed providers such as for example landline carriers and WCs.

2 Facilitate the seamless operation of important services such as possibly inter alia Session Initiation Protocol SIP across multiple networks platforms etc.

3 Provide legacy support thus as just one possibility potentially extending the useful life of various elements of a WC s infrastructure various legacy WDs etc. .

In one embodiment of the present invention there is provided an intermediary system for interconnecting multiple IP Multimedia Subsystem IMS networks. The system includes at least one input unit selectably connectable to a first IMS network from which a message is received at least one output unit selectably connectable to a second IMS network through which said message can reach a destination address and a process routing and switching PRS complex operable to manipulate aspects of and alter at least a portion of said message received from said input unit and sent to said output unit. In a preferred embodiment the PRS complex performs a routing operation based on a destination address of said message.

These and other features of the embodiments of the present invention along with their attendant advantages will be more fully appreciated upon a reading of the following detailed description in conjunction with the associated drawings.

It should be understood that these figures depict embodiments of the invention. Variations of these embodiments will be apparent to persons skilled in the relevant art s based on the teachings contained herein.

Aspects of the present invention build atop and extend substantively the concept of a centrally located full featured MICV facility. Reference is made to U.S. Pat. No. 7 154 901 entitled INTERMEDIARY NETWORK SYSTEM AND METHOD FOR FACILITATING MESSAGE EXCHANGE BETWEEN WIRELESS NETWORKS and its associated continuations for a description of a MICV a summary of various of the services functions etc. that are performed by a MICV and a discussion of the numerous advantages that arise from same.

As depicted in and reference numeral a MICV may be disposed between possibly inter alia multiple WCs WC WC on one side and multiple Service Providers SP SP SP on the other side thus bridging all of the connected entities. A MICV thus as one simple example may offer various routing formatting delivery value add etc. capabilities that provide possibly inter alia 

1 A WC WC WC and by extension all of the MSs that are serviced by the WC WC WC with ubiquitous access to a broad universe of SPs SP SP and

2 A SP SP Sp with ubiquitous access to a broad universe of WCs WC WC and by extension to all of the MSs that are serviced by the WCs WC WC .

Generally speaking a MICV may have varying degrees of visibility e.g. access etc. to the MS E MS MS SP etc. messaging traffic 

1 A WC may elect to route just their out of network messaging traffic to a MICV. Under this approach the MICV would have visibility e.g. access etc. to just the portion of the WC s messaging traffic that was directed to the MICV by the WC.

2 A WC may elect to route all of their messaging traffic to a MICV. The MICV may possibly among other things subsequently return to the WC that portion of the messaging traffic that belongs to i.e. that is destined for a MS of the WC. Under this approach the MICV would have visibility e.g. access etc. to all of the WC s messaging traffic.

IMSx extends the concept of a centrally located full featured MICV by abstracting away and to the extent possible isolating away all of the complexities inherent incompatibilities etc. that are associated with IMS. IMSprovides among other things a single protocol interface etc. agnostic access or connection point into which different entities within an IMS ecosystem for example possibly inter alia carriers may plug. 

To help illustrate aspects of IMS s single access connection point consider IMS three logical planes as illustrated in and reference numeral 

1 Services Plane . For example one or more Application Server AS instances Billing facilities Reporting facilities etc.

2 Control Plane . For example a Home Subscriber Server HSS capability a Call Session Control Function CSCF capability one or more Media Gateway MG instances etc.

3 Network or Transport Plane . Support interfaces etc. for possibly inter alia Voice over IP VoIP WiFi Public Land Mobile Network PLMN Public Switched Telephone Network PSTN etc.

As illustrated in and reference numeral the different functional elements of an entity e.g. carriers such as C C etc. within an IMS ecosystem may plug in to IMS s single access connection point e.g. elements of carrier C s Control Plane and Network or Transport Plane may plug in to IMS s single access connection point elements of carrier C s Services Plane may plug into IMS s single access connection point . Similar access points may be realized at .

As illustrated in and reference numeral the single access connection point serves much like a fa ade behind which connected entities e.g. carriers such as C C etc. may access one or more of the virtual implementations of IMS logical planes .

Thus for example as a carrier s environment grows and changes as a carrier s business needs and models change and evolve as a carrier deploys new service offerings etc. it can possibly among other things plug into and thus take advantage of the features and functions that are offered by different combinations of the virtual implementations of IMS logical planes all through the single access communication point.

Additionally placing the virtual planes behind a single fa ade allows for possibly among other things ongoing and dynamic changes updates etc. to the physical implementation of a plane without any impact on or interruptions to any of the connected entities.

1 Carriers Networks Providers etc. . The full universe of users such as possibly inter alia MSs of User Equipment UE UE UE such as for example mobile telephones computers Blackberrys and PalmPilots etc. are supported by carriers networks providers etc. The carriers networks providers etc. may connect to IMS which is shown generally below the carriers networks providers etc. layer and which would fit within e.g. element of using the single access communication point that was described above and then possibly inter alia exchange traffic with IMSover any combination of a range of communication channels e.g. Transmission Control Protocol TCP Internet Protocol IP User Datagram Protocol UDP IP Signaling System Number 7 SS7 etc. using any combination of a range of protocols e.g. SIP Short Message Peer to Peer SMPP MM4. etc. .

2 Protocol . A Protocol Engine PE Complex may house a dynamically updateable set of one or more PEs PE PE in the diagram . A PE may for example leverage a body of flexible extensible and dynamically updateable configuration information as it completes its tasks including possibly inter alia 

A Receiving incoming and sending outgoing traffic using any combination of the supported communication protocols paradigms etc.

B Performing various extraction validation editing formatting conversion etc. operations on the elements of an incoming and or outgoing data stream e.g. source address destination address encoding indicators or flags payload or body etc. The specific elements that were just described are illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other elements are easily possible and indeed are fully within the scope of the present invention.

C Encapsulating various elements of an incoming data stream within an internal i.e. intra IMS artifact and or un encapsulating various elements of an outgoing data stream from an internal artifact. An exemplary internal artifact is depicted in and reference numeral . Such an artifact may include a header that includes various information such as a type or identifier properties that include other information such as source address destination address and or date time for a given message and a body that may contain the contents of the body of an original message.

The catalog of PE processing steps that was described above is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other processing steps are easily possible and indeed are fully within the scope of the present invention.

3 Processing Routing Switching PRS . A Switching Complex SC may house possibly inter alia a dynamically updateable set of one or more SC Directors SCD SCD SCD in the diagram a dynamically updateable set of one or more Queues Q Q in the diagram and a Cross Complex Highway CCH .

A dynamically updateable set of one or more Queues e.g. Q Q may operate as intermediate or temporary buffers for incoming and outgoing traffic.

A CCH may consist of a rotating buffer containing a configurable number of Time Slots TS TS in the diagram that may be utilized for possibly inter alia the rapid redirection of traffic when for example no further substantive processing routing etc. of that traffic is required. For example a SCD may deposit incoming traffic that was received from a PE e.g. PE PE on to one or more TSs e.g. TS TS on a CCH and as the CCH rotates or spins a SCD e.g. the same SCD or another SCD may at the appropriate point remove traffic from those TSs e.g. TS TS for return to a PE e.g. PE PE .

A Selectively deposit incoming traffic e.g. traffic received from a PE e.g. PE PE on one or more Queues e.g. Q Q for subsequent processing by a PRS Engine PRSE .

B Selectively remove processed traffic from one or more Queues e.g. Q Q for return to a PE e.g. PE PE .

C Selectively deposit incoming traffic e.g. traffic received from a PE e.g. PE PE on one or more TSs e.g. TS TS on a CCH .

D Selectively remove traffic from one or more TSs e.g. TS TS on a CCH for return to a PE e.g. PE PE .

The catalog of SCD activities that was described above is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other activities are easily possible and indeed are fully within the scope of the present invention.

A PRSE Complex may house a dynamically updateable set of one or more PRSEs PRSE PRSE in the diagram .

A PRSE e.g. PRSE PRSE may be workflow based with a dynamically updateable set of one or more workflows removing incoming traffic from a Queue e.g. Q Q performing all of the required processing operations explained below and depositing processed artifacts on a Queue e.g. Q Q . Through flexible extensible and dynamically updatable configuration information a workflow component may be quickly and easily realized to support any number of activities. For example workflows might be configured to remove an item from a Queue e.g. Q Q deposit an item on a Queue e.g. Q Q perform one or more lookup operations in support of traffic routing implement aspects of a logical IMS plane etc. The specific workflows that were just described are exemplary only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other workflow arrangements alternatives etc. are easily possible.

A PRSE e.g. PRSE PRSE may leverage a comprehensive flexible scalable etc. lookup facility indicated albeit at a very high level as Routing Data in the diagram to support possibly inter alia its traffic routing operations. Such a lookup facility may provide authoritative answers to inquiries like At this moment in time what carrier services the Telephone Number TN 1 703 555 1212 What entity services the SIP address sip john.doe bigcompany.com etc. Among other things such a lookup facility may address 1 the complexities that are associated with all of the different TN numbering plans schemes etc. that exist around the world 2 the complexities that arise with worldwide Mobile Number Portability MNP regimes etc. A more detailed depiction of such a lookup facility is presented in and reference numeral . Such a lookup facility may consist of possibly inter alia 

A An Electronic Numbering ENUM fa ade through which various PRSEs E in the diagram may connect submit routing inquiries receive routing responses etc.

B A dynamically updateable set of one or more In Memory Databases In Memory Database In Memory Database in the diagram that optionally house or host selected data including possibly inter alia data from a Composite Routing Database CRD to provide as one example optimal performance.

C A Real Time Query Facility RTQF through which inquiries may be dispatched real time to authoritative bodies such as for example TN assignment administrators around the world. A RTQF may support multiple communication channels paradigms protocols etc. such as possibly inter alia SS7 TCP IP UDP IP SMPP etc. .

D A CRD containing comprehensive routing information for possibly inter alia TNs within all of the different TN numbering plans schemes etc. that exist around the world. A CRD may receive updates e.g. dynamically on a scheduled basis etc. from any number of sources or feeds including possibly inter alia domestic such as for example from a Local Exchange Routing Guide LERG from one or more Number Portability Administration Centers NPACs etc. and international such as for example from Hong Kong from the United Kingdom etc. .

With reference again to the catalog of PRS processing activities that was described above is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other processing steps are easily possible and indeed are fully within the scope of the present invention.

4 Persistence . A Database DB Complex may house a dynamically updateable set of one or more DBs DB DB in the diagram . A DB e.g. DB DB may contain a range of data or information including possibly inter alia Transaction Detail Records TDRs which may capture elements or aspects of all of the traffic is processed by IMS selected details of all administrative processing etc. activities etc.

A Data Warehouse DW Complex may house a dynamically updateable set of one or more DWs DW DW in the diagram . A DW e.g. DW DW may be fed by possibly inter alia a suite of flexible extensible and dynamically updatable Extraction Transformation Loading ETL Universal Rating Engine URE described further below etc. facilities that may pull data or information from possibly among other sources one or more DBs e.g. DB DB .

The DBs e.g. DB DB and DWs e.g. DW DW that are depicted are logical representations of the possibly multiple physical repositories that may be implemented to support inter alia configuration word catalog calculation etc. information. The physical repositories may be implemented through any combination of conventional Relational Database Management Systems RDBMSs such as Sybase or Oracle through Object Database Management Systems ODBMSs through in memory Database Management Systems DBMSs through specialized data repositories or through any other equivalent facilities.

5 Administration . An Administrator may provide management for or command and control over all of the different IMSelements through as one example a Web based interface. It will be readily apparent to one of ordinary skill in the relevant art that numerous other interfaces e.g. data feed Application Programming Interface API etc. are easily possible.

Additionally an Administrator may provide access to the body of flexible extensible and dynamically updateable configuration information that all of the different IMSelements rely upon.

An Administration layer or tier may provide comprehensive reporting facilities . Such reporting facilities may leverage possibly inter alia one or more DBs e.g. DB DB and or one or more DWs e.g. DW DW to generate scheduled e.g. hourly daily weekly etc. and or on demand reporting with report results delivered to for example a MS or a WC or a MICV or others through Short Message Service SMS Multimedia Message Service MMS IMS etc. messages through Electronic Mail E Mail through Instant Messenger IM through a World Wide Web WWW based facility through an Interactive Voice Response IVR facility via File Transfer Protocol FTP through an API etc. Generated reports may contain possibly inter alia textual and graphic elements.

The specific IMSlayer or tier arrangement that was described above is illustrative only and it will be readily apparent to one of ordinary skill in the relevant art that numerous other arrangements are easily possible and indeed are fully within the scope of the present invention.

Beyond providing basic IMS support and services IMSmay offer among other things additional e.g. value add features and functions such as possibly inter alia 

1 Billing. Support for a comprehensive array of billing e.g. rating etc. activities. Such billing activities may leverage a URE to flexibly and dynamically rate events where an event may include possibly inter alia some aspect of incoming traffic some activity by a PRSE etc. . A URE may evaluate any number of items as it rates an event including for example 

B One or more charging models pricing plans etc. that may consider possibly inter alia origination such as for example carrier TN SIP address etc. destination such as for example carrier TN SIP address etc. surcharges and discounts date day of week time volume etc. .

C One or more flexible extensible and dynamically configurable Point in Transaction PiT hooks. At a PiT hook one or more processing actions e.g. a calculation a call out to an external system etc. may be completed.

4 Support for variable Quality of Service QoS levels each level having possibly inter alia different cost charging paradigms. For example different QoS levels may be established for different classes of traffic etc. e.g. one QoS level for voice traffic such as VoIP another QoS level for interactive video another QoS level for streaming video another QoS level for image and text exchanges through vehicles such as SMS and MMS etc.

5 Filtering. Support for possibly inter alia zero one or multiple Black List and or White List artifacts malware e.g. virus detection spam detection etc. Each filtering option may have possibly inter alia one or more cost charging paradigms.

6 Sandbox. The ability to create one or more sandboxes or experimentation areas wherein an entity such as for example a carrier may conduct controlled development activities perform testing complete evaluation efforts conduct demonstrations etc. A sandbox option may have possibly inter alia one or more cost charging paradigms.

A Informational elements e.g. a service announcement a relevant or applicable factoid etc. An informational element may be selected statically e.g. the same informational text is used selected randomly e.g. informational text is randomly selected from a pool of available informational text or location based i.e. informational text is selected from a pool of available informational text based on the current physical location of a source and or recipient e.g. a MS WD as derived from as one example a Location Based Service LBS or similar facility .

B Advertising content e.g. textual material multimedia images of brand logos sound video snippets etc. material etc. containing advertisements promotional materials coupons etc. The advertising material may be selected statically e.g. the same advertising material is used selected randomly e.g. advertising material is randomly selected from a pool of available material or location based i.e. advertising material is selected from a pool of available material based on the current physical location of a source and or recipient e.g. a MS WD as derived from as one example a LBS or similar facility . IMSmay optionally allow advertisers to register and or provide e.g. directly or through links references to external sources advertising content.

It is important to note that the hypothetical example that was presented above which was described in the narrative and which was illustrated in the accompanying figures is exemplary only and was presented for purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the specific forms disclosed. It will be readily apparent to one of ordinary skill in the relevant art that numerous alternatives variations modifications etc. to the presented example are easily possible and indeed are fully within the scope of the present invention.

