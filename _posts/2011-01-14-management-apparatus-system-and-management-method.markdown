---

title: Management apparatus, system, and management method
abstract: A management apparatus transmits a reservation request for specifying time for turning off power supply of an image processing apparatus in response to determination that current time is in a time period for turning off the power supply of image processing apparatus if a start-up request is received from the image processing apparatus, transmits a start-up response for permitting start-up of functions other than a communication function provided in the image processing apparatus when a reservation response, to the reservation request from the image processing apparatus, including specified time for turning off the power supply of the image processing apparatus is received, and transmits a command for turning off the power supply of the image processing apparatus at the time specified by the reservation response, to the image processing apparatus.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08854656&OS=08854656&RS=08854656
owner: Canon Kabushiki Kaisha
number: 08854656
owner_city: Tokyo
owner_country: JP
publication_date: 20110114
---
In recent years due to the deteriorating global environment and economic conditions requirements for reducing power consumption of electric products have been increasingly made by various laws and standards. With the above described back ground also for multifunctional devices installed in large scale offices in order to reduce unnecessary standby electricity demands for developing a function to control power supply from a remote location has been increasing.

To meet such needs for example Japanese Patent Application Laid Open No. 2008 3863 discusses a system for transmitting a command from a management server at specified time and turning off power supply of multifunctional devices under management. Further for example Japanese Patent Application Laid Open No. 2002 163090 discusses a system for managing the number of activated multifunctional devices and not permitting turning on power supply of multifunctional devices of the number exceeding a predetermined upper limit.

In the above described known techniques when a user manually starts a multifunctional device that has been switched off by a command from a management server until the device receives a command from the management server again the device may be left turned on. Moreover when multifunctional devices that can be started are managed in terms of the number of the devices even in the time range in which the devices are expected not to be used so often the number of the multifunctional devices that can be started does not change. Accordingly effective power supply management is not always performed.

According to an aspect of the present invention a management apparatus configured to manage status of power supply of a plurality of image processing apparatuses capable of communicating via a network includes a setting unit configured to set a time period for turning off the power supply of the image processing apparatuses a determination unit configured to determine whether current time is in the time period set by the setting unit if a start up request is received from the image processing apparatus a request unit configured to transmit a reservation request for specifying time for turning off the power supply of the image processing apparatus that has transmitted the start up request to the transmitted image processing apparatus if the determination unit determines that the current time is in the time period set by the setting unit a start up permission unit configured to transmit a start up response for permitting start up of functions other than a communication function provided in the transmitted image processing apparatus when a reservation response to the reservation request from the transmitted image processing apparatus including specified time for turning off the power supply of the transmitted image processing apparatus is received to the transmitted image processing apparatus and a management unit configured to transmit a command for turning off the power supply of the transmitted image processing apparatus at the time specified by the reservation response to the transmitted image processing apparatus.

Further features and aspects of the present invention will become apparent from the following detailed description of exemplary embodiments with reference to the attached drawings.

Various exemplary embodiments features and aspects of the invention will be described in detail below with reference to the drawings.

The power supply management server is an example of a management apparatus. On the power supply management server a network device management program is running. The power supply management server manages power supply of the multifunctional devices and according to a procedure described below. The multifunctional devices and are an example of an image processing apparatus. The multifunctional devices have functions of a copying machine a scanner a printer a facsimile and the like.

On the multifunctional devices and software for receiving a shutdown request from the power supply management server and turning off each of their own power supply a power off state is running. The network device management program running on the power supply management server according to the present exemplary embodiment is WEB application that operates on a WWW server. The program is intended to be operated via a browser program in the client PCs and .

The power supply management server includes a central processing unit CPU read only memory ROM a random access memory RAM a system bus a keyboard controller KBC a display controller DISPC and a disk controller DKC . The power supply management server also includes a network interface card NIC a keyboard KB and a display DISP .

The power supply management server also includes a hard disk HD a flexible disk controller FD and a compact disk read only memory CD ROM drive CD .

The CPU executes the network device management program described below in detail stored in the ROM or the HD . Further the CPU performs overall control of each device connected to the system bus .

The RAM serves as a main memory a work area or the like for the CPU . The KBC controls an instruction input from the KB a pointing device not illustrated or the like. The DISPC controls display on the DISP .

The DKC controls access to the HD the FD and the CD . The NIC bi directionally transmits and or receives data to from the client PCs and the multifunctional devices and or the like via the LAN that is an example of the network.

As long as not mentioned in the following descriptions in the power supply management server a main entity of execution on the hardware is the CPU and a main entity of control on the software is the network device management program stored in the ROM or the HD .

The network device management program can be stored in a storage medium such as a CD ROM and can be provided in that state. In such a case the program is read from the storage medium such as the CD or the like and installed on the HD .

In the description the network device management program operates on a WWW server program and performs communication using a WWW browser program not illustrated on the client PCs and and an HTTP protocol.

In the description the network device management program and the multifunctional devices and communicate with each other using a SIMPLE Management Network Protocol SNMP or another unique protocol.

In a general control module analyzes a command received from the WWW server program . The general control module assigns control to a scheduler module a device management module a device search module and a power supply management module according to the results of the analysis.

Further the general control module transmits HTML data generated in the scheduler module the device management module the device search module and the power supply management module to the WWW server program .

The scheduler module controls timing for executing various types of processing executable in the network device management program . That is execution timing of the various types of processing by the device management module the device search module and the power supply management module is managed by the scheduler module .

The device management module performs setting of information to multifunctional devices to be managed and acquisition of information from the multifunctional devices. Further the device management module performs control of display or the like of an associated user interface UI . The device management module further controls a device setting acquisition module for acquiring information from a multifunctional device and a device setting transmission module for transmitting information to a multifunctional device.

The device search module performs search of the multifunctional devices connected to the LAN control of various parameters associated with the search processing display of the associated UI and the like. A device list module according to the control of the device search module performs processing such as list display of information information update import export and the like of the searched multifunctional device.

A power supply management module in response to the control by the scheduler module performs control so that a command for requesting shutdown at predetermined time is transmitted and the multifunctional device is shut down. Further the power supply management module when the multifunctional device is started in the time period set according to a procedure described below checks existence or nonexistence of associated multifunctional devices and comparison of capability of the devices in order to efficiently manage power supply of the multifunctional devices.

A communication module performs communication with the multifunctional devices in response to an instruction from the device management module the device search module and the power supply management module and transmits and receives various pieces of information.

A database stores various pieces of information acquired in the device management module and the device search module and various pieces of information set by user operation.

The multifunctional device includes a core control unit a network interface unit a document transmission unit an operation unit a formatter unit a memory unit a scanner unit and a printer unit .

The core control unit is connected to each of the network interface unit the document transmission unit the operation unit the formatter unit the memory unit the scanner unit and the printer unit and performs overall control of the devices. The core control unit can install an application program that runs in the apparatus by a procedure described below.

The network interface unit controls communication with the various network devices connected to the LAN receives job control data from the computers client PCs and the like and transmits and receives document data. The job control data includes a job control instruction to be transmitted together with page description language PDL data. For example the job control instruction is to rasterize PDL data to print as image data perform staple sort and discharge paper.

Further via the network interface unit a request of shutdown by the power supply management server and an inquiry of information by the other management programs are processed.

The document transmission unit is connected to the LAN via the core control unit and the network interface unit . The document transmission unit uses various communication protocols and transmits information input from the scanner unit and information stored in the memory unit to each device.

The operation unit performs an instruction to output a document to the document transmission unit and an instruction to input a document via the scanner unit . Setting to the various application programs installed in the apparatus can be made via the operation unit .

The formatter unit is connected to the core control unit and rasterizes PDL data received from a computer via the network interface unit into image data that can be output by the printer unit .

The memory unit includes a storage unit such as a ROM a RAM or a hard disk. The memory unit stores image data input from the scanner unit or application the other programs and the like downloaded via the network.

The scanner unit converts contents of a read paper document into image data and transmits the data to another computer on the network via the network interface unit . Further the scanner unit stores the data into the memory unit and outputs the data to the printer unit .

The printer unit outputs image data inputted from the scanner unit in response to an instruction by the operation unit or image data received from the computer or the other multifunctional devices via the network interface unit .

A real time OS is a first execution environment of a program that can control various functions of the multifunctional device in real time. The real time OS includes a library group that can control each function including an optional device or a function expansion card of the multifunctional device and a module group that provides interface commands to a basic application that operates in an upper layer.

A controller control unit includes a module that operates on the real time OS to control the document transmission unit the operation unit the formatter unit the scanner unit the printer unit and the like.

An application programming interface API is a module that performs processing to access the controller control unit according to an instruction from the basic application .

The basic application is a module that requests various types of processing to the controller control unit using the API . The basic application also can communicate with the power supply management server the client PCs and and the other multifunctional devices and on the LAN via the network interface unit . A virtual machine is a second execution environment suitable for executing specific application. The virtual machine is for example implemented by Java registered trademark .

A framework performs overall control of the application on the virtual machine that is the second execution environment of the multifunctional device . Application operates on the virtual machine that is the second execution environment.

The application provides the functions according to the present exemplary embodiment such as transmitting and receiving commands according to the control of the power supply management server displaying a screen and performing shutdown according to the operation unit . As long as not mentioned in the present exemplary embodiment in the multifunctional device a main entity of execution on the hard ware is the core control unit and a main entity of control on the software is the application that is executed by the core control unit .

In step S the device search module performs search processing of the multifunctional devices and connected to the LAN on a condition set by a user in advance. In the device search processing according to the present exemplary embodiment the search processing is performed by a broadcast packet of SNMP or a multicast packet of Service Location Protocol SLP however it is not limited to the above.

In step S the power supply management module selects a device in this example the multifunctional device to be the target of the power supply management from among the network devices searched in step S according to the operation of the user. Then the processing proceeds to step S.

In step S the scheduler module sets a shutdown recommended time period via a setting screen see to the multifunctional device selected in step S. Then the processing proceeds to step S. The shutdown recommended time period according to the present exemplary embodiment is a time period the manager wants to keep the power supply of the multifunctional device shutdown for example time after office hours and holidays. The shutdown recommended time period includes start time and end time.

In step S the general control module stores the name of the multifunctional device that is the target of the power supply management selected in step S and the shutdown recommended time period set in step S in the database and ends the processing.

In step S the scheduler module sets a timer for the start time of the shutdown recommended time period stored in the database in step S in and the processing proceeds to step S.

In step S the scheduler module determines whether the timer indicating the start time of the shutdown recommended time set in step S times out. If it is determined that the time out occurs YES in step S the processing proceeds to step S. If it is determined that the time out has not occurred NO in step S the processing in step S is subsequently performed.

In step S the power supply management module transmits a command shutdown request for requesting shutdown to the multifunctional device via the communication module to the multifunctional device . Then the processing proceeds to step S.

In this example a response shutdown response to the shutdown request transmitted in step S is transmitted from the multifunctional device . In step S the power supply management module receives the shutdown response via the communication module . Then the processing proceeds to step S.

In step S the power supply management module analyzes the shutdown response received in step S. As a result of the analysis in step S if the power supply management module determines that the shutdown is normally performed by the multifunctional device YES in step S the processing proceeds to step S. If the power supply management module determines that the shutdown is not normally performed NO in step S the processing proceeds to step S.

If the multifunctional device cannot normally perform the shutdown due to print processing being performed receiving facsimile information or the like the multifunctional device returns a shutdown response indicating that the shutdown processing has not been normally performed failure to the shutdown request.

In step S the power supply management module registers history information indicating that the shutdown processing has been successfully performed in the database . Then the processing ends. In step S the power supply management module registers the history information indicating that the shutdown processing has been failed and sets a timer for resending the shutdown request. Then the processing in step S is performed.

The timer value for resending the shutdown request is registered in the network device management program in advance.

In step S the application receives the shutdown request transmitted from the network device management program running on the power supply management server in step S in . Then the processing proceeds to step S.

In step S in order to respond to the shutdown request received in step S the application determines whether the multifunctional device can perform the shutdown processing.

If the application determines that the multifunctional device cannot perform the shutdown processing NO in step S the application performs processing in step S. If the application determines that the multifunctional device can perform the shutdown processing YES in step S the application performs processing in step S. The multifunctional device according to the present exemplary embodiment cannot perform the shutdown processing when print processing is being performed facsimile information is being received and the like.

In step S the application transmits a shutdown response indicating failure of the shutdown processing to the power supply management server and ends the processing. In step S the application transmits a shutdown response indicating success of the shutdown processing to the power supply management server . Then the processing proceeds to step S.

In step S the application performs the shutdown processing including shutdown and ends the processing. Hereinafter the processing performed by the power supply management server illustrated in and the processing performed by the multifunctional device illustrated in is referred to as shutdown reservation processing .

In step S the network device management program receives a command start up request indicating start up of the multifunctional device is instructed by operation of the user from the multifunctional device . Then the processing proceeds to step S.

In step S the scheduler module reads out the shutdown recommended time period of the multifunctional device stored in the database and compares current time to the shutdown recommended time period. If it is determined that the current time is out of the shutdown recommended time period NO in step S the processing proceeds to step S. If it is determined that the current time is within the shutdown recommended time period YES in step S the processing proceeds to step S.

In step S the power supply management module transmits a response start up response permission for permitting turning on the power supply in response to the start up request received in step S to the multifunctional device via the communication module and ends the processing.

In step S to the start up request received in step S the power supply management module transmits a response shutdown reservation request for requesting reservation of execution of the shutdown processing to the multifunctional device via the communication module .

In step S the power supply management module via the communication module receives the response shutdown reservation response from the multifunctional device in response to the shutdown reservation request transmitted in step S. Then the processing proceeds to step S. The shutdown reservation response received in step S includes setting specification of time shutdown reservation time the power supply of the multifunctional device is shut down according to a procedure described below.

In step S the power supply management module transmits a command start up response permission for permitting start up to the multifunctional device via the communication module . Then the processing proceeds to step S. The power supply management module that performs the processing in steps S to S is an example of a start up permission unit.

In addition in step S the scheduler module sets the timer for the shutdown reservation time acquired in step S. Then the processing proceeds to step S. In step S the scheduler module determines whether the timer indicating the set shutdown recommended time has timed out.

If it is determined that the time out occurs YES in step S the processing after step S is performed. If it is determined that the time out has not occurred NO in step S the processing in step S is performed. As described above the power supply management server performs the management power supply OFF management for shutting down the power supply of the multifunctional device.

In step S the application receives the operation of start up of the multifunctional device from the operation unit by the user. Then the processing proceeds to step S. At the time the operation of the start up is performed in step S only the core control unit the network interface unit the operation unit and the memory unit in the multifunctional device are started.

By a part of the functions communication functions started in step S communication between the multifunctional device and the power supply management server such as sending and receiving of requests or responses is performed. Other than the communication function includes functions of a copying machine a scanner a printer a facsimile and the like are provided.

That is the other hardware for example the document transmission unit the formatter unit the scanner unit and the printer unit which are devices used for information processing are not started.

In step S in response to the start up operation in step S the application transmits a start up request to the power supply management server . In step S as a response to the start up request transmitted in step S the application determines whether a shutdown reservation request is received.

If the application determines that the shutdown reservation request is received YES in step S the processing proceeds to step S. If the application determines that the shutdown reservation request is not received NO in step S the processing proceeds to step S. In step S the application displays a screen see for reserving shutdown on the operation unit . Then the processing proceeds to step S.

In step S the application receives an input of reservation time from the user on the screen for reserving shutdown displayed on the operation unit . Then the processing proceeds to step S.

In step S the application transmits a shutdown reservation response including information of the reservation time of shutdown input via the operation unit to the power supply management server . In step S the application receives a start up response permission which is a command for permitting the start up transmitted from the power supply management server . Then the processing proceeds to step S.

In step S the application starts all hardware in the multifunctional device in response to the start up response permission received in step S. In the processing hardware that has not started for example engine units in the formatter unit and the printer unit are started.

A device list lists the multifunctional devices searched in step S and selected in the processing in step S in . The device list includes device names that are user friendly names that can be set in the multifunctional devices IP addresses and input control of the shutdown recommended time periods. The display items are not limited to these items.

The control is for inputting the shutdown recommended time periods. The control includes text boxes for inputting start time and end time. Buttons are for storing setting or discarding cancelling setting values of the shutdown recommended time period set to the control .

A control is for inputting default values of a shutdown recommended time period and for applying the default values to a device selected by a check box . Buttons are for uniformly setting the check box to a check state select all or an uncheck state cancel all .

Buttons are for storing setting or discarding cancelling shutdown reservation time set to the control . Although not illustrated in if the cancel button is pressed on the screen the multifunctional device is shut down.

As described above in the power supply management system first a time period a shutdown state of a multifunctional device is to be maintained is set by a manager as a shutdown recommended time period. Then by a user within the shutdown recommended time period for example if the multifunctional device is started in response to a request of the network device management program the shutdown reservation screen is displayed on the operation unit in the multifunctional device

Then the shutdown reservation time input by the user from the shutdown reservation screen displayed on the multifunctional device is notified to the network device management program . The network device management program transmits a shutdown request to the multifunctional device at the notified shutdown reservation time and shuts down the multifunctional device .

With the above described configuration within the time the shutdown state is to be maintained it is possible to prevent the multifunctional device that is started by the user from being left in the activated state as much as possible. Accordingly unnecessary power consumption can be effectively prevented.

A second exemplary embodiment of the present invention is described. A system configuration a hardware configuration and a software configuration or a module configuration of a power supply management system according to the second exemplary embodiment are basically similar to those in the first exemplary embodiment. Configurations different from those in the first exemplary embodiment will be described if necessary.

In step S the device search module performs search processing of network devices on a condition set by the user in advance. In step S the power supply management module selects a multifunctional device to be the target of the power supply management from the searched network devices. Then the processing proceeds to step S.

In step S the device management module associates the multifunctional devices selected in step S with each other. Then the processing proceeds to step S. The association in step S is for example operation for performing grouping by using setup locations of the multifunctional devices as a key.

In step S the device management module acquires capability of the multifunctional devices selected in step S and manages the multifunctional devices by the association group unit in step S. Then the processing proceeds to step S. The acquisition of the capability in step S is performed by the device management module for example using means such as SNMP.

In step S the scheduler module sets a shutdown recommended time period to each of the multifunctional devices selected in step S. Then the processing proceeds to step S. In step S the general control module stores the names of the multifunctional devices selected in step S information of the association performed in step S and the shutdown recommended time period set in step S in the database and ends the processing.

In step S the network device management program receives a command start up request indicating power supply operation of the multifunctional device is performed by the user. Then the processing proceeds to step S.

In step S the scheduler module reads out the shutdown recommended time period of the multifunctional device stored in the database and compares current time and the shutdown recommended time period. If it is determined that the current time is out of the shutdown recommended time period NO in step S the processing proceeds to step S. If it is determined that the current time is within the shutdown recommended time period YES in step S the processing proceeds to step S.

In step S the power supply management module transmits a response start up response permission for permitting turning on the power supply in response to the start up request received in step S to the multifunctional device via the communication module and ends the processing.

In step S the device management module performs processing of acquiring information of the status of the multifunctional devices associated with the multifunctional device in the association in step S in . Then the processing proceeds to step S.

In step S the device management module refers to the associated multifunctional device status information acquired in step S and detects a multifunctional device that is activated. As a result of the detection in step S if there is a multifunctional device that is activated YES in step S the processing proceeds to step S. If there is no multifunctional device that is activated NO in step S the processing proceeds to step S.

In step S the power supply management module compares the capability of the multifunctional device and that of the activated multifunctional device in the example the multifunctional device detected in step S. Then the processing proceeds to step S.

The comparison of the capability in step S includes for example whether capability of color printing two sided printing and stapling are included or comparison of optional mounting state of a paper feeding discharging unit is performed.

In step S as a result of the comparison of the capability in step S the power supply management module determines which capability of the multifunctional device and the multifunctional device is higher. As a result of the determination in step S if it is determined that the capability of the multifunctional device is higher YES in step S the power supply management module performs processing in step S. If it is determined that the capability of the multifunctional device is lower or the multifunctional device has similar functions NO in step S the processing proceeds to step S.

In the comparison of the capability of the devices differences of the functions such as processable sheet size color printing post processing such as bookbinding and facsimile are determined. For example a device A that is activated has a scanner function and a monochromatic print function and a device B that has already been activated has the function of the scanner function and a color monochromatic print function. In such a case it is determined that the device B has a higher capability.

In step S the power supply management module transmits a request device selection request for selecting which of the multifunctional device and the multifunctional device is to be used to the multifunctional device via the communication module . Then the power supply management module performs processing in step S.

In step S the power supply management module receives a response device selection response to the device selection request transmitted in step S via the communication module . Then the processing proceeds to step S. The device selection response received in step S includes information of the multifunctional device to be used and information of the shutdown reservation time input by the user when the user changes the shutdown reservation time.

In step S the power supply management module analyzes the device selection response received in step S and determines that the selected device is the multifunctional device or the multifunctional device . As a result of the determination in step S if it is determined that the multifunctional device is selected YES in step S the processing proceeds to step S. If it is determined that the multifunctional device is selected NO in step S the processing proceeds to step S.

In step S the power supply management module transmits a request recommended device usage request for recommending the use of the multifunctional device via the communication module to the multifunctional device . Then the processing proceeds to step S.

In step S the power supply management module via the communication module receives a response recommended device usage response to the recommended device usage request transmitted in step S. Then the processing proceeds to step S.

The recommended device usage response received in step S includes information of the multifunctional device to be used and information of the shutdown reservation time input by the user when the user changes the shutdown reservation time.

In step S the power supply management module transmits a shutdown reservation request via the communication module to the multifunctional device .

In step S the power supply management module via the communication module receives a shutdown reservation response from the multifunctional device to the shutdown reservation request transmitted in step S. Then the processing proceeds to step S. In the shutdown reservation response received in step S the shutdown reservation time of the multifunctional device is set.

In step S the power supply management module transmits a command for permitting start up to the multifunctional device via the communication module to the multifunctional device . Then the processing proceeds to step S. In step S the shutdown processing illustrated in is performed to the multifunctional device and the processing ends.

In step S the power supply management module performs processing for prompting the multifunctional device to shut down the multifunctional device . Then the processing proceeds to step S.

In step S the power supply management module analyzes the device selection response received in step S or the recommended device usage response received in step S. Then the power supply management module determines whether the shutdown reservation time of the multifunctional device is updated.

As a result of the determination in step S if it is determined that the shutdown reservation time is updated YES in step S the processing proceeds to step S. If it is determined that the shutdown reservation time is not updated NO in step S the processing ends. In step S the shutdown processing illustrated in is performed to the multifunctional device and then the processing ends.

In step S the application receives the operation of turning on the power supply of the multifunctional device by the user via the operation unit . Then the processing proceeds to step S. In the operation of the turning on the power supply in step S only the core control unit the network interface unit the operation unit and the memory unit in the multifunctional device are started and the other hardware is not activated.

In step S the application receives the operation of turning on the power supply in step S transmits a start up request indicating that start up operation is performed to the power supply management server . In step S the application receives a response to the start up request transmitted in step S. Then the processing proceeds to step S.

In step S the application determines whether the response to the start up request received in step S is a recommended device usage request. If the application determines that the response to the start up request is the recommended device usage request YES in step S the processing proceeds to step S. If the application determines that the response to the start up request is not the recommended device usage request NO in step S the processing proceeds to step S.

In step S the application displays information about the recommended device on a screen see in on the operation unit . Then the processing proceeds to step S. On the recommended device information screen information about the multifunctional device included in the recommended device usage request transmitted in step S in and control for changing the shutdown reservation time of the multifunctional device and the like are displayed.

In step S the application determines whether operation for changing the shutdown recommended time of the multifunctional device is performed on the recommended device information screen displayed in step S. If the application determines that the shutdown recommended time of the multifunctional device is changed YES in step S the processing proceeds to step S. If the application determines that the shutdown recommended time of the multifunctional device is not changed NO in step S the processing proceeds to step S.

In step S the application sets the reservation time to the information of a recommended device usage response to be transmitted in step S. Then the processing proceeds to step S. In step S the application transmits a response recommended device usage response to the recommended device usage request received in step S and ends the processing.

In step S the application determines whether the response to the start up request received in step S is a device selection request. If the application determines that the response to the start up request is the device selection request YES in step S the processing proceeds to step S. If the application determines that the response to the start up request is not the device selection request NO in step S the processing proceeds to step S.

In step S the application displays information about the selection target multifunctional device on a screen see in on the operation unit . Then the processing proceeds to step S.

On the device selection screen information about the multifunctional device included in the device selection request transmitted in step S in the control for changing the shutdown reservation time of the multifunctional device and the like are displayed.

In step S the application on the device selection screen displayed in step S determines which of the multifunctional device and the multifunctional device is selected. If the application determines that the multifunctional device is to be used YES in step S the processing proceeds to step S. If the application determines that the multifunctional device is to be used NO in step S the processing proceeds to step S.

In step S the application determines whether operation for changing the shutdown reservation time of the multifunctional device is performed on the device selection screen displayed in step S. If the application determines that the shutdown reservation time of the multifunctional device is changed YES in step S the processing proceeds to step S. If the application determines that the shutdown reservation time of the multifunctional device is not changed NO in step S the processing proceeds to step S.

In step S the application sets the updated reservation time to the information of a device selection response to be transmitted in step S. Then the processing proceeds to step S. In step S the application transmits the response device selection response to the device selection request received in step S and ends the processing.

In step S the application determines whether the response received in step S is a shutdown reservation request. If the application determines that the shutdown reservation request is received YES in step S the processing proceeds to step S. If the application determines that the shutdown reservation request is not received NO in step S the processing proceeds to step S.

In step S the application displays a shutdown reservation screen on the operation unit . If the user inputs shutdown reservation time from the shutdown reservation screen displayed on the operation unit in the multifunctional device the application performs processing in step S.

In step S the application sets shutdown reservation time in a shutdown reservation response. Then the processing proceeds to step S. In step S the application transmits the shutdown reservation response including the shutdown reservation time input from the shutdown reservation screen to the power supply management server and ends the processing.

Although not illustrated in the flowchart if the multifunctional device is selected after the above described processing start up processing of the multifunctional device is performed. If the multifunctional device is selected shutdown processing of the multifunctional device is performed.

A recommended device information part shows information about a recommended device. The information includes a device name that is a user friendly name of a multifunctional device a setup location an IP address and shutdown reservation time that is currently set.

An input control is for changing shutdown reservation time of a recommended device. A button control includes two types of selection of YES and NO . If YES is selected the shutdown reservation time set to the input control is stored. The selection is to be a trigger of the recommended device usage response to be transmitted in step S in .

On the recommended device information screen the use of the recommended device is enforced. Accordingly on the screen display is made such that the button of NO cannot be selected.

The device selection screen is for displaying information of the selection target device displayed in step S in the flowchart in . The device selection part shows information about a selection target device. The information includes a device name that is a user friendly name of the multifunctional device a setup location an IP address and shutdown reservation time that is currently set.

An input control is for changing shutdown reservation time of a selection target device. A button control includes two types of selection of YES and NO . If YES is selected the shutdown reservation time set to the input control is stored. The selection is to be a trigger of the device selection response to be transmitted in step S in . If NO is selected the screen shifts to the shutdown reservation screen illustrated in .

As described above in the power supply management system according to the present exemplary embodiment first as a shutdown recommended time period a manager of the multifunctional device sets time for maintaining a shutdown state of the multifunctional device to the network device management program . Then the network device management program associates a plurality of multifunctional devices to be managed with each other using conditions such as a setup location as a key.

In the processing if a multifunctional device is started by a user within the set shutdown recommended time period the network device management program checks the status of the associated multifunctional devices.

As a result of the check if there are activated multifunctional devices the network device management program compares capability of the devices. If there is a high performance multifunctional device the use of the high performance device is enforced and the recommended device information screen for setting shutdown reservation time is displayed.

In there is no high performance multifunctional device in the activated multifunctional devices the device selection screen for selecting a multifunctional device to be used and setting shutdown reservation time of the selected multifunctional device is displayed. The information and the shutdown reservation time of the multifunctional device selected on the device selection screen are notified to the network device management program .

The network device management program transmits a shutdown request to the selected multifunctional device at the notified shutdown reservation time and shuts down the multifunctional device.

If there is no activated multifunctional device in the associated multifunctional devices operation similar to that in the first exemplary embodiment is performed.

With the above described configuration it is possible to prevent a plurality of devices from being activated at a time period while the shutdown states are to be maintained as much as possible and more effective power supply management of the multifunctional devices can be performed.

Aspects of the present invention can also be realized by a computer of a system or apparatus or devices such as a CPU or MPU that reads out and executes a program recorded on a memory device to perform the functions of the above described embodiments and by a method the steps of which are performed by a computer of a system or apparatus by for example reading out and executing a program recorded on a memory device to perform the functions of the above described embodiments. For this purpose the program is provided to the computer for example via a network or from a recording medium of various types serving as the memory device e.g. computer readable medium . In such a case the system or apparatus and the recording medium where the program is stored are included as being within the scope of the present invention.

While the present invention has been described with reference to exemplary embodiments it is to be understood that the invention is not limited to the disclosed exemplary embodiments. The scope of the following claims is to be accorded the broadest interpretation so as to encompass all modifications equivalent structures and functions.

This application claims priority from Japanese Patent Application No. 2010 011395 filed Jan. 21 2010 which is hereby incorporated by reference herein in its entirety.

