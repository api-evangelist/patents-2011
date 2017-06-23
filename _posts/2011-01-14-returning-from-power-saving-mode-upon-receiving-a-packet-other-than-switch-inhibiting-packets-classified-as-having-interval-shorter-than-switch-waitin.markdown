---

title: Returning from power saving mode upon receiving a packet other than switch inhibiting packets classified as having interval shorter than switch waiting time to power saving mode
abstract: In a multifunctional device, a packet analysis unit determines whether a received packet contributes to inhibition of a power saving mode, stores the time at which a packet is received and information indicating whether a packet is received during the power saving mode as information about the packet determined as contributing to the inhibition thereof, and calculates a period of access by a plurality of packets based on the stored information about the packet and a factor analysis unit classifies the access of which the calculated period is shorter than the waiting time of the power saving mode into an access inhibiting a shift to the power saving mode and classifies the access of which the period is not shorter than the waiting time of the power saving mode and which is made by the packet received during the power saving mode, into an access returning from the power saving mode.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08671297&OS=08671297&RS=08671297
owner: Canon Kabushiki Kaisha
number: 08671297
owner_city: Tokyo
owner_country: JP
publication_date: 20110114
---
The present invention relates to a multifunctional device for analyzing and reporting the influence of an external access on a power saving mode.

In recent years a demand has been increased for reducing power consumption in electrical products by various laws and standards with a worsening global environment and economical situations as a background. Under such a situation a power saving mode has generally been provided also for a multifunctional device.

On the other hand a large number of software products exists which operates on a computer and monitors the state of the multifunctional device and consumables to effectively use the multifunctional device. Although the software provides users of the multifunctional device with various pieces of information the access inhibits the power saving mode of the multifunctional device.

For this reason an administrator needs to realize the existence of a variety of software accessing the multifunctional device and change the setting thereof or stop thereof if required to effectively use the power saving mode of the multifunctional device.

In order to cope with such a problem there has been a control method for a conventional multifunctional device in which an external periodic access inhibiting the power saving mode of the multifunctional device is recorded to report the access to a user refer to Japanese Patent Application Laid Open No. 2007 295145 .

However in the above conventional technique an external access apt to inhibit the power saving mode is uniformly reported which causes a problem that it is difficult to grasp how each access affects the power saving mode of the multifunctional device.

The present invention provides a mechanism capable of grasping in detail how access to the multifunctional device affects the power saving mode.

According to an aspect of the present invention an multifunctional device which is communicable with an external device via a network and shifts to a power saving mode in a case where a specific request is not made within a waiting time of the power saving mode includes a determination unit configured to determine whether a packet received via the network contributes to inhibition of the power saving mode a storage unit configured to store the time at which a packet is received and information indicating whether a packet is received during the power saving mode as information about the packet determined as contributing to the inhibition thereof by the determination unit a calculation unit configured to calculate a period of access by a plurality of packets based on the information about the packet stored in the storage unit an analysis unit configured to compare the period of access calculated by the calculation unit with the waiting time of the power saving mode to analyze the degree of inhibition of the power saving mode and classify accesses by the plurality of packets according to the degree and a notification unit configured to provide notification of results analyzed by the analysis unit wherein the analysis unit classifies the access of which the period is shorter than the waiting time of the power saving mode into an access inhibiting a shift to the power saving mode and classifies the access of which the period is not shorter than the waiting time of the power saving mode and which is made by the packet received during the power saving mode into an access returning from the power saving mode.

Further features of the present invention will become apparent from the following description of exemplary embodiments with reference to the attached drawings.

Various exemplary embodiments features and aspects of the invention will be described in detail below with reference to the drawings.

The multifunctional device has functions such as a copying machine a scanner a printer and a facsimile machine. The multifunctional device is provided with a function to move a normal mode to a power saving mode in which power consumption is automatically reduced if there is no request for the use of the above functions printing request for example or there is no operation for inquiries about information via the network within a preset power saving mode standby time.

An application program for periodically inquiring of the multifunctional device about information on status and the remaining amount of a consumable and a printer driver are installed on the computers and .

In the present exemplary embodiment an SNMP is presumed as an example of a communication protocol for inquiring of the multifunctional device about various pieces of information however the communication protocol is not limited to the SNMP. The SNMP stands for a simple network management protocol.

In the power saving mode of the multifunctional device inquires from the computers and delay the timing of movement of the power saving mode or return the power saving mode to the normal mode.

The multifunctional device can execute the application program in the system using a configuration described later. In the present exemplary embodiment a power saving mode inhibiting factor is analyzed by the application program in the system.

As illustrated in the multifunctional device includes a core control unit a network interface unit a document transmission unit an operation unit a formatter unit a memory unit a scanner unit and a printer unit .

The core control unit is connected to the network interface unit the document transmission unit the operation unit the formatter unit the memory unit the scanner unit and the printer unit to integrally control each functional block. The core control unit causes a processor provided in the core control unit to read the application program which is installed in the memory and operated in the system with a configuration described later and can execute the application program.

The network interface unit is a function module for controlling communication with various network devices connected to the local area network receives job control data from the computers and transmits and receives document data. The job control data include a job control command transmitted with PDL data which is for example a command for developing the PDL data printing them as image data stapling and sorting the print and discharging it. Inquiries about information on status and the remaining amount of a consumable from the computers and are made via the network interface unit .

The document transmission unit is connected to the local area network via the core control unit and the network interface unit and transmits information input from the scanner unit and information stored in the memory unit .

The operation unit is a function module for instructing the printer unit and document transmission unit to output a document and input a document via the scanner unit . Settings can be performed via the operation unit on various application programs installed in the system. The operation unit is equipped with a display panel and can display various messages.

The formatter unit is connected to the core control unit and develops the PDL data received from the computer via the network interface unit into image data which can be output by the printer unit .

The memory unit includes a storage device such as a ROM a RAM and a hard disk HDD and stores image data input from the scanner unit applications downloaded from the network and other programs.

The scanner unit is a function module for converting the contents of a read paper document into image data transmitting the image data to other devices on the network via the network interface unit stores the image data in the memory unit and outputting the image data to the printer unit .

The printer unit outputs image data input from the scanner unit instructed by the operation unit and image data received from the computer or other multifunctional devices.

In a real time OS operating system is a first execution environment of a program capable of controlling various functions of the multifunctional device in real time.

The real time OS incorporates a library group capable of controlling each function including an optional device of the multifunctional device or an expansion card and a module group providing an interface command for a basic application operating on a host device.

A controller control unit operating on the real time OS includes a module controlling the document transmission unit the operation unit the formatter unit the scanner unit and the printer unit .

An application programming interface hereinafter referred to as API is a module performing a process for accessing the controller control unit in accordance with the command of the basic application .

The basic application is a module for requesting the controller control unit to perform various processes using the API . The basic application is communicable with the computers and on the local area network via the network interface unit .

A second execution environment is most suitable for executing a specific application which is a virtual machine realized by Java registered trademark for example.

A frame work integrally controls the application on the virtual machine being the second execution environment of the multifunctional device .

An application operates on the virtual machine of the second execution environment. The application provides a function to analyze and report the power saving mode inhibiting factor in the present exemplary embodiment.

The application is downloaded from an external application providing server for example via the network interface unit installed in the memory unit and executed by the core control unit .

In a general control unit integrally controls a network monitor unit a packet analysis unit a packet information storage unit a factor analysis unit an analysis result storage unit and an analysis result notification unit .

The network monitor unit is a module for monitoring a packet to make an inquiry about information on status and the remaining amount of a consumable received from the computers and via the network interface unit .

The packet analysis unit is a module for storing information about a packet which may contribute to the inhibition of the power saving mode out of the packets monitored by the network monitor unit in the packet information storage unit .

The packet information storage unit is a database for storing information about a packet determined as possibly contributing to the inhibition of the power saving mode. The entity of information stored in the packet information storage unit is stored in the memory unit .

The factor analysis unit is a function module for classifying the information about the packet stored in the packet information storage unit by a transmission source address and a packet content analyzing influence on the power saving mode and storing it in the analysis result storage unit .

The analysis result storage unit is a database for storing analysis result in the factor analysis unit . The entity of information stored in the analysis result storage unit is stored in the memory unit .

The analysis result notification unit is a function module for notifying an administrator of the analysis result stored in the analysis result storage unit through means of a preset electronic mail.

When a packet is received by the network monitor unit the packet is delivered to the packet analysis unit and the packet analysis unit starts the process of the flow chart.

In step S the packet analysis unit analyzes a packet hereinafter referred to as a reception packet received via the network monitor unit . The processing proceeds to step S. In step S the protocol of the received packet and the contents of request are analyzed.

In step S the packet analysis unit determines whether the reception packet may contribute to the inhibition of the power saving mode based on the analysis result in step S. In the present exemplary embodiment a request for causing the multifunctional device to respond is determined as the power saving mode inhibiting factor.

If the packet analysis unit determines that the reception packet does not contribute to the inhibition of the power saving mode NO in step S the packet analysis unit determines that the reception packet does not contribute to the inhibition of the power saving mode and the process of the flow chart is ended. If the packet analysis unit determines that the reception packet contributes to the inhibition of the power saving mode YES in step S the packet analysis unit causes the processing to proceed to step S.

The OS such as Windows registered trademark Vista is provided with a function to cause the SNMP packet to periodically inquire of a printer in which a driver is installed about the status of the printer. Typically the request for causing the multifunctional device to respond like the inquiry of the SNMP packet about the status contributes to the inhibition of the power saving mode of the multifunctional device . The multifunctional device of the present exemplary embodiment is configured to return a response to accesses from the computer which are expected to frequently occur without affecting the power saving mode. In the present exemplary embodiment information such as transmission source address protocol and contents of request about a packet which is excluded from the power saving mode inhibiting factors to be warned of can be set by the user previously setting from the application . The setting is stored in the memory unit .

In step S the packet analysis unit determines whether the reception packet is information about a packet which is excluded from the previously set power saving mode inhibiting factors to be warned of based on the result analyzed in step S.

If the packet analysis unit determines that the reception packet is information about a packet which is excluded from the previously set power saving mode inhibiting factors to be warned of YES in step S the process of the flowchart is ended. On the other hand if the packet analysis unit determines that the reception packet is not information about a packet which is excluded from the previously set power saving mode inhibiting factors to be warned of NO in step S the packet analysis unit causes the processing to proceed to step S.

In step S the packet analysis unit determines whether the reception packet is the packet received during the power saving mode based on the result analyzed in step S reception determination during the power saving mode . If the packet analysis unit determines that the reception packet is not the packet received during the power saving mode NO in step S the packet analysis unit causes the processing to proceed to step S. On the other hand if the packet analysis unit determines that the reception packet is the packet received during the power saving mode YES in step S the packet analysis unit causes the processing to proceed to step S.

In step S the packet analysis unit records that the reception packet is the one that is received during the power saving mode. More specifically information indicating that the packet is received during the power saving mode is added to the analysis result in step S. The processing proceeds to step S. Many multifunctional devices with the power saving mode notify a computer of timing at which the device shifts to the power saving mode by multicast of a service location protocol SLP . Similarly it is assumed that the multifunctional device according to the present exemplary embodiment has a function to notify a computer of timing at which the device shifts to the power saving mode. Therefore in step S if the packet analysis unit determines that the reception packet is the one received during the power saving mode the packet analysis unit determines that the application program operating on the transmission source computer does not correspond to a function to notify of shift to the power saving mode and records that the reception packet is the one received during the power saving mode in step S.

In step S the packet analysis unit classifies the received packet information by a transmission source address with reference to the existing information stored in the packet information storage unit . The packet analysis unit causes the processing to proceed to step S.

In step S the packet analysis unit classifies the packet information classified by a transmission source address in the above step S by the contents of a packet type . The processing proceeds to step S.

In step S the packet analysis unit extracts a packet similar in content to that transmitted from the same transmission source address as the above reception packet classified in the above steps S and S and calculates the average of access intervals of the extracted plurality of packets. The processing proceeds to step S.

In step S the packet analysis unit stores information on the reception packet including information added in step S and information calculated in step S which is determined as the power saving mode inhibiting factor in steps S and S in the packet information storage unit . The process of the flow chart is ended.

The general control unit starts the process of the flow chart at a timing according to the period previously set in the memory unit of the multifunctional device . The general control unit can also start the process of the flow chart when an instruction for notifying the user of the power saving mode inhibiting factor is input from the operation unit or external devices of the computers to .

In step S the factor analysis unit reads the reception packet information stored in the packet information storage unit and causes the processing to proceed to step S.

In step S the factor analysis unit counts the total n of entries of the reception packet information read in the above step S and causes the processing to proceed to step S.

In step S the factor analysis unit initializes an index i for counting the entries of the reception packet information read from the packet information storage unit in step S to 0 and causes the processing to proceed to step S.

In step the factor analysis unit determines whether the index i initialized in step S is smaller than the total n of entries of the reception packet information calculated in step S. If the factor analysis unit determines that the index i is equal to or greater than the total n of entries of the reception packet information NO in step S the factor analysis unit causes the processing to proceed to step S.

If the factor analysis unit determines that the index i is smaller than the total n of entries of the reception packet information YES in step S the factor analysis unit causes the processing to proceed to step S.

In step S the factor analysis unit reads the i th reception packet information stored in the packet information storage unit and causes the processing to proceed to step S.

In step S the factor analysis unit determines whether the i th reception packet information is a periodic access with reference to the access interval average calculated in step S in within the i th reception packet information read in step S. In step S even if the i th reception packet information is a periodic access if the i th reception packet information is an access period exceeding a predetermined threshold it is determined that the influence of the access on power saving mode is small and the access is not analyzed. In the application of the present exemplary embodiment the user can set a threshold with respect to presence and absence of periodicity of the received packet information. The threshold is stored in the memory unit . If the access interval exceeds the threshold the factor analysis unit determines that even if the i th reception packet information is an entry related to a periodically received packet information the influence of the entry over the power saving mode is small. Then the factor analysis unit determines that the reception packet information is an entry of non periodic packet information NO in step S and causes the processing to proceed to step S.

If the access interval does not exceed the threshold the factor analysis unit determines that the i th reception packet information is an entry of periodic packet information YES in step S and causes the processing to proceed to step S.

In the present exemplary embodiment the non periodic packet information is filtered in step S to take only the periodic packet information as the object of the subsequent analysis processes. In the subsequent steps S to S the factor analysis unit compares the access period of the periodic packet information with the waiting time of the power saving mode to analyze a power saving mode inhibition degree and classify accesses though a plurality of packets by the degree. The processes are described in detail below.

In step S the factor analysis unit compares the access interval of the i th reception packet information with the waiting time of the power saving mode previously set by the multifunctional device and stored in the memory unit and causes the processing to proceed to step S.

In step S the factor analysis unit determines whether the access period of the reception packet information is shorter than the waiting time of the power saving mode based on the comparison result in step S.

If the factor analysis unit determines that the access period of the reception packet information is shorter than the waiting time of the power saving mode YES in step S the factor analysis unit causes the processing to proceed to step S. If the access interval of the reception packet information is shorter than the waiting time of the power saving mode the multifunctional device never moves to the power saving mode. For this reason in step S the factor analysis unit analyzes the influence on the power saving mode as large HIGH because the i th reception packet information becomes a factor for completely inhibiting the shift to the power saving mode and causes the processing to proceed to step S.

If the factor analysis unit determines that the access period of the reception packet information is not shorter than the waiting time of the power saving mode NO in step S the factor analysis unit causes the processing to proceed to step S.

In step S the factor analysis unit refers to the information recorded in step S out of the i th reception packet information read in step S to determine whether the information is an access during the power saving mode.

If the factor analysis unit determines that the information is an access during the power saving mode YES in step S the factor analysis unit causes the processing to proceed to step S. If the factor analysis unit determines that the information is not an access during the power saving mode NO in step S the factor analysis unit causes the processing to proceed to step S.

The multifunctional device in the present exemplary embodiment has a function to notify the user of the aforementioned timing at which the device shifts to the power saving mode. For this reason if an access occurs during the power saving mode the factor analysis unit determines that the application program does not correspond to notification of shift to the power saving mode from the multifunctional device .

In step S the factor analysis unit determines that the i th reception packet information is the access considering the waiting time of the power saving mode but not considering shift to the power saving mode and causes the processing to proceed to step S. In step S the i th reception packet information does not completely inhibit shift from the normal mode to the power saving mode but becomes a factor for returning to the normal mode from the power saving mode so that the factor analysis unit analyzes the influence on the power saving mode as middle MID . The processing proceeds to step S.

In step S the factor analysis unit determines that the i th reception packet information becomes a factor for delaying shift to the power saving mode from the determination results in steps S and S and causes the processing to proceed to step S. The reception packet information to be determined in step S neither completely inhibits shift to the power saving mode nor performs access for returning to the power saving mode so that the factor analysis unit analyzes the influence on the power saving mode as small LOW . The factor analysis unit determines the reception packet information as an access considering the power saving mode and causes the processing to proceed to step S.

In step S the factor analysis unit stores the analysis results in steps S S or S with the i th reception packet information in the analysis result storage unit and causes the processing to proceed to step S.

In step S the factor analysis unit increments the index i and causes the processing to return to step S.

In step S if the factor analysis unit determines that the index i is smaller than the total n of entries of the reception packet information the factor analysis unit repeats the processes in steps S to S.

In step S if the factor analysis unit determines that the index i is equal to or greater than the total n of entries of the reception packet information the factor analysis unit causes the processing to proceed to step S.

In step S the analysis result notification unit notifies the previously set user of the analysis result stored in the analysis result storage unit in step S and ends the process of the flow chart. The setting of the user to be notified is stored in the memory unit . The notification method in step S includes electronic mail display on a computer of the user to be notified display on the display panel of the operation unit and a report output. The notification method is not particularly limited in the present invention.

If notification is made by electronic mail the mail address of the user to be notified should be previously set. For display on a computer of the user to be notified the IP address of the computer of the user to be notified is set and displayed on the computer of the IP address by popup. If notification is made by report output printing is performed by the multifunctional device the IP address of a printer used by the user to be notified and a facsimile number are previously set to perform printing by the printer of the IP address or facsimile is transmitted to the facsimile number.

In a column there is indicated the access period calculated by the packet analysis unit in . In a column there is indicated the communication protocol of the reception packet analyzed by the packet analysis unit in .

In a column there is indicated information about the contents of the reception packet analyzed by the packet analysis unit in step S in as is the case with the column . If an SNMP packet is received the contents of the type of request get request set request get next request and management information base MIB for example are written in the column .

In a column there is indicated the degree of influence on the power saving mode analyzed by the factor analysis unit in steps S S and S in .

As described above the administrator of the multifunctional device can correctly in detail grasp the degree of influence of an external access on the power saving mode and easily confirm whether an unnecessary access exists by referring to the analysis result illustrated in .

A second exemplary embodiment is described below with reference to drawings. The system described in the second exemplary embodiment includes the same hardware and software as those of the first exemplary embodiment.

When a packet is received by the network monitor unit the packet is delivered to the packet analysis unit and the packet analysis unit starts the process of the flow chart.

In step S the packet analysis unit analyzes a packet hereinafter referred to as a reception packet received via the network monitor unit . As is the case with step S in in step S the protocol of the received packet and the contents of request are analyzed.

In step S the packet analysis unit determines whether the reception packet contributes to the inhibition of the power saving mode based on the analysis result in step S. If the packet analysis unit determines that the reception packet does not contribute to the inhibition of the power saving mode NO in step S the packet analysis unit determines that the reception packet does not contribute to the inhibition of the power saving mode and ends the process.

If the packet analysis unit determines that the reception packet contributes to the inhibition of the power saving mode YES in step S the packet analysis unit determines that the reception packet contributes to the inhibition of the power saving mode and causes the processing to proceed to step S. The details of step S are similar to those of step S in .

In step S the packet analysis unit determines whether the reception packet is information about a packet which is excluded from the previously set power saving mode inhibiting factors to be warned of based on the result analyzed in step S.

If the packet analysis unit determines that the reception packet is information about a packet which is excluded from the previously set power saving mode inhibiting factors to be warned of YES in step S the process of the flowchart is ended. On the other hand if the packet analysis unit determines that the reception packet is not information about a packet which is excluded from the previously set power saving mode inhibiting factors to be warned of NO in step S the packet analysis unit causes the processing to proceed to step S. The details of step S are similar to those of step S in .

In step S the packet analysis unit stores information on the reception packet which is determined as the power saving mode inhibiting factor and an object to be warned of in steps S and S respectively in the packet information storage unit and ends the process of the flow chart.

The general control unit starts the process of the flow chart at a timing according to the period previously set in the memory unit of the multifunctional device . The general control unit can also start the process of the flow chart when an instruction for notifying the user of a factor for inhibiting transfer to the power saving mode is input from the operation unit or external devices of the computers to .

In step S the factor analysis unit reads the reception packet information stored in the packet information storage unit and causes the processing to proceed to step S.

In step S the factor analysis unit filters a non periodic reception packet information out of the reception packet information read from the packet information storage unit in step S and causes the processing to proceed to step S.

In the application of the present exemplary embodiment the user can set a threshold with respect to presence and absence of periodicity of the received packet information. The threshold is stored in the memory unit . The factor analysis unit determines that the packet in which the access interval exceeds the threshold exercises a small influence on the power saving mode even if the packet is an entry related to a periodically received packet information. The factor analysis unit determines that the packet is an entry of non periodic packet information.

On the other hand in step S the factor analysis unit determines that the packet in which the access interval does not exceed the threshold is an entry of periodic packet information and extracts the packet.

In step S the factor analysis unit counts the number m of the reception packet information determined as periodic in step S out of information read in step S and causes the processing to proceed to step S.

In step S the factor analysis unit initializes an index j for counting a periodic reception packet information to 0 and causes the processing to proceed to step S.

In step S the factor analysis unit determines whether the index j initialized in step S is smaller than the number m 1 of the periodic reception packets calculated in step S. If the factor analysis unit determines that the index j is equal to or greater than the number m 1 of the periodic reception packets NO in step S the factor analysis unit causes the processing to proceed to step S.

If the factor analysis unit determines that the index j is smaller the number m 1 of the periodic reception packets YES in step S the factor analysis unit causes the processing to proceed to step S.

In step S the factor analysis unit calculates the packet reception interval between the j th and the j 1 th packets out of the periodic reception packet information read from the packet information storage unit and causes the processing to proceed to step S.

In step S the factor analysis unit compares the packet reception interval between the j th and the j 1 th packets calculated in step S with the waiting time of the power saving mode previously set by the multifunctional device and stored in the memory unit and causes the processing to proceed to step S.

In step S the factor analysis unit determines whether the reception interval is shorter than the waiting time of the power saving mode previously set by the multifunctional device and stored in the memory unit based on the comparison result in step S.

If the factor analysis unit determines that the reception interval is shorter than the waiting time of the power saving mode YES in step S the factor analysis unit causes the processing to proceed to step S.

In step S the factor analysis unit records the reception packet information of the j th and the j 1 th access along with information indicating that the reception packet information is the access to be warned of inhibiting a shift to the power saving mode in the analysis result storage unit and causes the processing to proceed to step S.

If the factor analysis unit determines that the reception interval is not shorter than the waiting time of the power saving mode NO in step S the factor analysis unit causes the processing to proceed to step S.

In step S the factor analysis unit records the reception packet information of the j th access in the analysis result storage unit and causes the processing to proceed to step S.

If the factor analysis unit determines that the index j is smaller the number m 1 of the periodic reception packets YES in step S the factor analysis unit performs control to repeat the processes from steps S to S.

If the factor analysis unit determines that the index j is equal to or greater than the number m 1 of the periodic reception packets NO in step S the factor analysis unit causes the processing to proceed to step S.

In step S the analysis result notification unit notifies the previously set user of the analysis result stored in the analysis result storage unit in step S and ends the process of the flow chart. The notification method in step S is similar to that in step S in .

In in a column there is indicated a time at which a packet is received. In a column there is indicated the transmission source address of a packet received via the network interface unit . In a column there is indicated the communication protocol of the reception packet analyzed by the packet analysis unit .

In a column there is indicated information about the contents of the reception packet analyzed by the packet analysis unit . If the SNMP packet is received the contents of the type of request get request set request get next request and management information base MIB are written in the column .

Accesses to be warned of inhibiting a shift to the power saving mode determined in step S in are indicated by and . The accesses and are transferred in a form in which the accesses can be readily discriminated from other accesses which do not inhibit a shift to the power saving mode .

The user may be notified only of the accesses to be warned of inhibiting a shift to the power saving mode i.e. only and .

As described above the administrator of the multifunctional device can correctly grasp the degree of influence of an external access on the power saving mode and easily confirm whether an unnecessary access exists by referring to the analysis result illustrated in .

In the present exemplary embodiment data and time on and at which the multifunctional device shifts to the power saving mode and returns from the power saving mode are recorded in a log thereby the factor analysis unit may determine whether the j th access is the one during the power saving mode based on the log in step S in . If the reception packet information of the j th access is an access during the power saving mode the reception packet information of the j th access is recorded in the analysis result storage unit along with information indicating that the reception packet information of the j th access is the access returning the device to the power saving mode. On the other hand if the reception packet information of the j th access is not an access during the power saving mode the reception packet information of the j th access is recorded in the analysis result storage unit along with information indicating that the reception packet information of the j th access is the access considering the power saving mode. Furthermore in step S in the analysis result notification unit may notify the user of the analysis result in such a form that each access can be readily discriminated whether it is an access to be warned of inhibiting a shift to the power saving mode an access returning the device to the power saving mode or an access considering the power saving mode.

As described above the administrator of the multifunctional device can adequately grasp the degree of influence of an external access on the power saving mode and easily confirm whether an unnecessary access exists by referring to the analysis result illustrated in .

The present invention can also be realized by executing the following process. That is a process in which a software program that realizes the functions of the above described embodiments is supplied to the system or apparatus via a network or a recording medium of various types and then a computer of the system or apparatus or devices such as CPU or MPU reads out the program and executes it. In such a case the recording medium where the program is stored as well as the program are included in the present invention.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all modifications equivalent structures and functions.

This application claims priority from Japanese Patent Application No. 2010 007763 filed Jan. 18 2010 which is hereby incorporated by reference herein in its entirety.

