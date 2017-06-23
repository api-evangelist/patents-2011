---

title: Control network system, master apparatus, control data processing method, and control data processing program
abstract: A control computer as a master apparatus in a control network system includes a packet generation unit. The packet generation unit: selects a control command for writing a data from among packet generation information; references the packet generation information for each of the selected control command; and includes a data for write which is read from an address in a storage section corresponding to the each control command, in a control packet to generate the control packet. A communication unit transmits the generated control packet to a controlled object as a slave device.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09557734&OS=09557734&RS=09557734
owner: HITACHI INDUSTRIAL EQUIPMENT SYSTEMS CO., LTD.
number: 09557734
owner_city: Tokyo
owner_country: JP
publication_date: 20110127
---
This application claims the benefit of Japanese Patent Application No. 2010 015213 filed on Jan. 27 2010 the disclosure of which is incorporated herein by reference.

The present invention relates to techniques of a control network system a master apparatus a control data processing method and a control data processing program.

In a configuration of a control system one or more control computers master apparatuses control one or more controlled devices slave devices via a network. The master apparatus controls the slave device by transmitting a control packet including a control instruction or the like to the slave device. The network in which the control packet flows is for example DeviceNet CC Link registered trademark and EtherCAT registered trademark .

An API Application Programming Interface in a control application includes various methods. In one of the methods a packet to be transmitted is built in the API itself and a control instruction is stored in a data area in the packet.

In another method of the API a data area of a controlled object is allocated to an address space to which is accessible from a control application and a control instruction is written to the data area. The control instruction written to the address space is built as an outgoing packet using a prescribed technique and is transmitted to a network.

In some cases the address space is a software object developed in a memory. In others the address space is a bus space in a hardware which is accessible from a computation unit such as a CPU.

One of methods of allocating a data area to a prescribed address space is a transfer memory method see Japanese Laid Open Patent Application Publication No. 2000 076163 and ISO International Organization for Standardization 14745 4 Industrial Automation Systems and integration Open systems application integration frameworks Part 4 Reference description for Ethernet based control systems . In the transfer memory method data areas of all nodes constituting a network are allocated to an address space in equal size. Data in the address spaces in the all nodes are periodically exchanged among the all nodes via communications. Networks using the above mentioned method include CC Link and FL net. The transfer memory method is also called a common memory method.

Another method of allocating a data area to a prescribed address space is a logical address space method. In the logical address space method a given data area owned by each slave is allocated to a single virtual logical address space. Size of the allocated area or how to allocate can be arbitrarily set. Networks using the method as described above include EtherCAT registered trademark see IEC61784 Part 2 Communication Profile Family 12 .

With regard to an API in a method communicating a control instruction to a controlled object a conventional technology has a difficulty in solving problems such as efficiency of developing software communication performance in software flexibility of network configuration or the like.

In the method in which an outgoing packet is generated in an application and a control instruction to a controlled object is stored in the outgoing packet an application developer is required to understand a communications protocol of a network. However in developing such a control application the application developer preferably focuses on realization of a desired control method and achievement of a target control performance. If the application developer has to understand details of a communications protocol development man hours are increased and application development becomes complicated which is disadvantageous.

Further if communications software such as an operating system to be abbreviated as an OS hereinafter is used communication processing time is increased and control performance in an entire system is decreased. Such communications software includes for example a TCP IP protocol stack which is described hereinafter as a protocol stack of communications software . A communication processing using a protocol stack requires an increased communication processing time because a control application and a communication processing are sequentially executed. Moreover if other application is running on the OS a runtime thereof also affects and may further increase the communication processing time.

In the transfer memory method a data area of a controlled object is allocated into an address space and an instruction is read or written to the data area. The method has an advantage that there is no need of understanding details of a communications protocol compared to a method of generating an outgoing packet inside an application. However in the transfer memory method because data areas in fixed size as many as all nodes are allocated to an address space the number of nodes connectable to the network tends to be limited.

The fixed sized data area tends to create an unused free space therein. For example assume a case where there are two controlled objects. One has scores of I O of 2 and the other 1 000 . If a size of a target data area has 1 024 the latter controlled object can efficiently utilize the data area but the former cannot leaving almost all of the data area meaningless.

In the logical address space method a data area of a controlled object can be arranged with less limitations as compared to the transfer memory method. The logical address space method thus has a high use efficiency of an address space and smaller limitations on the number of connectable nodes. A network using the logical address space method has a larger maximum allowable number of connectable nodes than that of a network using the transfer memory method.

The logical address space method however also requires the developer to well understand which meaning a data at a prescribed address location has in an application similarly to the transfer memory method. Therefore it is not possible to develop an application in such a way that a meaning in a control application is expressed. The developer executes a processing on the application to a prescribed address which decreases development efficiency.

The logical address space method requires the application developer to have expertise on a logical address space or a network such as generation of an outgoing packet which results in prolonged time of application development and thus further sophisticated necessary skills. This also increases cost of application development. Additionally implementation by software requires sequential execution which results in a prolonged communication processing time and deterioration of control performance.

The present invention has been made in an attempt to solve the above problems and provide an information processing apparatus having improved development efficiency and communication performance.

In a control network system a master apparatus that generates a control packet is connected to a slave device that is controlled according to the control packet. The master apparatus includes a packet generation information registration unit a packet generation unit a communication unit and a storage section. The packet generation information registration unit allocates for each control command to the slave device a data area to the storage section which stores therein a data handled by the control command associates an allocated address the control command to the slave device an identifier of the slave device targeted by the control command and an address for data access in a storage area in the slave device with one another and stores the associated data in the storage section as packet generation information. The packet generation unit selects a control command for writing a data from the master apparatus to the slave device from among the packet generation information references the packet generation information for each selected control command and includes a data for write which is read from an address in the storage section corresponding to the each control command in the control packet so as to generate the control packet. The communication unit transmits the generated control packet to the slave device.

Other features and advantages of the present invention will become more apparent from the following detailed description of the invention when taken in conjunction with the accompanying exemplary drawings.

Next are described in detail embodiments of the present invention with reference to related drawings.

A first embodiment describes a configuration in which a data structure is allocated using a physical address space.

A second embodiment describes a configuration in which a data structure is allocated using a logical address space.

The control network is for example a network of EtherCAT registered trademark which operates in a protocol of the Ethernet registered trademark .

The CPU transfers a program from the nonvolatile storage medium to the memory and executes the program. An execution and processing program to be used is for example an OS Operating System and an application program which operates in the OS.

The communication LSI receives a communication request from a program which operates in the CPU and communicates with the control network using the PHY . The communication LSI is implemented in for example ICs Integrated Circuits such as an FPGA Field Programmable Gate Array a CPLD Complex Programmable Logic Device an ASIC Application Specific Integrated Circuit and a gate array.

The PHY is a transceiver IC capable of communicating with the control network . A communication standard provided by the PHY is for example a PHY chip of the Ethernet registered trademark . Note that in the configuration of the PHY is connected to the communication LSI and a processing in a MAC Media Access Control layer of the Ethernet is thus included in the communication LSI .

Note that other configurations are also applicable in which an IC serving as MAC is placed between the communication LSI and the PHY or in which a communication IC having a combination of an IC serving as MAC and the PHY is connected to the communication LSI .

The memory is a temporary storage area in which the CPU can operate and stores therein an OS an application program or the like transferred from the nonvolatile storage medium .

The nonvolatile storage medium is an information storage medium and is used for storing a program for operating the CPU and for storing a result of executing a program.

The bus connects the CPU the memory the nonvolatile storage medium and the communication LSI each other. The bus is for example a PCI Peripheral Components Interconnect bus a PCI Express bus an ISA Industrial Standard Architecture bus a system bus and a memory bus.

Note that the packet used in this embodiment is a control packet for controlling the controlled object as a slave device.

In the hardware configuration of the control computer the bus connection unit communicates with the bus . The bus connection unit is connected to the CPU or the memory according to a communication specification of the bus . In the communication LSI the bus connection unit is connected to the data storage unit the packet generation information storage unit and the operation management unit .

The bus connection unit transmits and receives a data for creating a communication frame to and from the data storage unit .

The bus connection unit transmits and receives information for creating a communication frame from a data stored in the data storage unit to and from the packet generation information storage unit .

The bus connection unit transmits and receives a data on management setting of operations or states of the packet generation unit and the packet filter unit to and from the operation management unit .

The data storage unit is configured by a combination of a storage for write unit and a storage for read unit so as to store a data for creating a communication frame.

The storage for write unit stores a data written by the bus connection unit . The stored date is read by the packet generation unit . The storage for read unit stores a data written by the packet filter unit . The store data is read by the bus connection unit .

If an access is made from outside the storage for write unit and the storage for read unit each perform mutual exclusion control to the access or create a plurality of data areas inside thereof where necessary. Below is described a specific example of such a case using the storage for write unit .

The data storage unit is connected to the bus connection unit the packet generation unit and the packet filter unit as a communication path of data. Herein there is a possibility that the bus connection unit and the packet generation unit simultaneously make each access to the storage for write unit . In order to avoid access collision for example either of two methods as follows can be used.

In a method A an access right management is performed. An access right is set such that if one of the bus connection unit and the packet generation unit makes an access to the storage for write unit an access from the other is prohibited.

In a method b an access is orderly processed using buffering such as ring buffer. For example a plurality of data storage areas are prepared in the storage for write unit to build ring buffer. This makes it possible for the bus connection unit and the packet generation unit to simultaneously make each access. The number of data storage areas required for the ring buffer is determined according to relation between access rates of the two storage units.

Note that more storage areas are used in the method B than the method A. However the method B has performance higher than that of the method A. Either of the method A or the method B is used according to conditions of storage performance or restrictions. Note that similarly to the storage for write unit the storage for read unit can use the method A or the method B so as to avoid access collision.

The packet generation information storage unit stores therein packet generation information to be detailed in hereinafter .

The packet generation unit acquires an appropriate data from the data storage unit according to the packet generation information read from the packet generation information storage unit generates a packet for controlling the controlled object and transmits the generated packet to a data transmission unit .

The packet filter unit extracts a control data from the packet received via a data reception unit and stores the control data in the data storage unit . Herein a storage location and a size of a storage area of the control data in the data storage unit is determined accordance with the packet generation information .

The communication unit is connected to the control network and performs communication according to a communications protocol of the control network . The communication unit is configured by a combination of the data transmission unit and the data reception unit . Note that in the configuration of because the PHY is provided outside the communication LSI the communication unit corresponds to a processing section of a MAC layer. However the PHY may be configured as an Ethernet communication device including the MAC layer and PHY layer. Or the communication LSI may serve as PHY.

The data transmission unit serves as a transmitting section in the communication unit and transmits a packet from the control computer to the control network .

The data reception unit serves as a receiving section in the communication unit and receives a packet transmitted from the control network .

The operation management unit is configured by a functional register or the like. The operation management unit presents management of operations or states of the packet generation unit and the packet filter unit to the bus . A program running on the CPU controls operations of the packet generation unit and the packet filter unit by accessing to the functional register of the operation management unit via the bus and acquires states of the controlled operations. Data or information which the operation management unit can set or acquire includes a timing of a packet communication performed by the packet generation unit and information necessary for generating a packet.

The development computer includes a control instruction structure unit as a processing section. The development computer has system information a program source and a control instruction structure as data in a storage section thereof.

Herein the control computer operates for itself an OS a device driver a library an API an application and a packet generation information registration unit .

However the control instruction structure unit the program source the control instruction structure and the system information may be provided and operated in the control computer or in the development computer which is provided separately from the control computer .

Also the development computer may not be necessarily a single computer and may be configured by for example one computer in which the control instruction structure unit is operated and another in which the application is developed using the program source .

The control instruction structure unit analyzes information on a controlled object defined by the system information and a control network to thereby generate the control instruction structure .

The packet generation information registration unit also analyzes the information on the controlled object defined by the system information and the control network to thereby register the packet generation information in the packet generation information storage unit utilizing access provided by the device driver .

The program source is a source code of a program using the control instruction structure . The program source is compiled so as to serve as the application . Note that this embodiment describes a compiler language which becomes executable by compiling. However as an executable form of a program source an interpreter language may be used in which a program source is interpreted upon execution and is sequentially executed.

The control instruction structure shows a structure of the data storage unit of the communication LSI . Some specific examples of the control instruction structure are a structure definition and a union definition of C language.

The OS provides basic functions such as program management and access to hardware. The OS is not always necessary but is preferably used because it provides the basic functions for using a general purpose application and an existing software asset and performing task management. A real time OS is also preferably used in which task scheduling is executable according to time restrictions.

The device driver makes access to a data area operation management information and state information which are available at the communication LSI via the bus using an access means to hardware provided by the OS . The device driver may or may not be part of the OS .

The library includes therein a frequently used function and provides basic operations such as memory management task management input output and file operation using the OS . A specific example of the library is glibc used in Linux registered trademark .

The application is a software which computes a control instruction for controlling the controlled object and executes transmission and receipt of a communication packet using the communication LSI .

The control instruction name shows which meaning and name a given data area has as a control instruction. The command shows a command of a telegram of EtherCAT registered trademark corresponding to a given data area.

Table 1 lists abbreviated names to be selected as the command . If the command has the last character of W of the abbreviated name it is a command for write. If the last character of R a command for read. And if the last character of RW a command for both read and write. Note that the terms read and write will be defined hereinafter in describing the input output direction .

Referring back to the slave identifier of the system information is an identifier of a slave. However some commands do not require the slave identifiers . For example commands LRD LWR LRW corresponding to logical addresses such as the control instruction items do not require the slave identifiers .

The address is a physical address or a logical address in case of command corresponding to a logical address in a storage section in a slave device corresponding to the slave identifier .

The input output direction shows whether a generated packet is for read write or read write. Note that in this embodiment the term write means that a data present in a storage area of a master is copied in a storage area of a slave. The term read means that a data present in a storage area of a slave is copied in a storage area of a master.

The command is a data copied from the command and is a command in a telegram of EtherCAT registered trademark .

The address is a data showing a result of a data allocation processing and indicates a location of a data area of a packet generated from the packet generation information in the data storage unit .

The slave identifier is an identifier of a slave and is copied from the slave identifier . However some commands do not require the slave identifiers . For example commands LRD LWR LRW corresponding to logical addresses do not require the slave identifiers .

The physical logical address is a data copied from the address and is a physical address or a logical address in case of a command corresponding to a logical address in a given slave.

The input output direction is a data copied from the input output direction and shows whether a generated packet is for read write or read write. Note that the item of the input output direction is necessary because the command does not uniquely determine whether a give packet is for read write or read write. The input output directions of LRD LWR LRW commands are determined as read write and read write respectively. The input output directions of ARMW and FRMW commands are both determined as write.

Next is described the flowchart of . Note that a subject which performs the steps of the flowchart of is the packet generation information registration unit .

In S from among the system information whether or not there exists the control instruction item including the slave identifier which has not yet allocated a data structure to the data storage unit is determined. If there is no such not yet allocated control instruction item if No in S the processing of is terminated.

In S if there still exists the not yet allocated control instruction item if Yes in S a not yet allocated slave identifier corresponding thereto is selected. A slave having the slave identifier selected in S is hereinafter referred to as a selected slave.

In S any control instruction items of which slave identifiers are owned by the slaves selected in S from among the system information are selected.

Note that all of those control instruction items are selected in S. However a developer may arbitrarily select any of the control instruction items . In this case to the selected control instruction item of the system information is added an attribute which indicates whether allocation of a data structure from the control instruction item and or generation of packet generation information is enabled or disabled. Thus the attribute is enabled or disabled is another example for determining which data is to be selected from among the control instruction item in S.

In S from among the control instruction items selected in S any control instruction item that has the input output direction of both read and write is selected.

In S a data area of each of the selected control instruction item is sequentially allocated to respective beginnings of the storage for write unit and the storage for read unit according to a size of the data area.

In S from among the control instruction items selected in S any control instruction item that has the input output direction of write only is selected.

In S a data area of the control instruction item each selected in S is sequentially allocated to a data area subsequent to the data area having been allocated in S of the storage for write unit according to a size of the data area.

In S from among the control instruction items selected in S any control instruction item having the input output direction of read only is selected.

In S a data area of the control instruction item each selected in S is sequentially allocated to a data area subsequent to the data area having been allocated in S of the storage for read unit according to a size of the data area.

A difference between the flowchart of and the flowchart of is the same as a difference between S and S. In S a data area of the control instruction item each selected in S is sequentially allocated according to the size of the data area to a data area subsequent to the data area having been allocated in S of the storage for read unit plus the data area having been allocated in S of the storage for write unit . This makes it possible to allocate the data area in the storage for write unit in which the input output direction is only read and the data area in the storage for read unit in which the input output direction is only write from respective start addresses different from each other.

In S from among the system information any control instruction item that has the input output direction of both read and write is selected.

In S a data area of each of the selected control instruction items is sequentially allocated to respective beginnings of the storage for write unit and the storage for read unit according to a size of the data area.

In S from among the system information any control instruction item that has the input output direction of read only is selected.

In S a data area of the control instruction item each selected in S is sequentially allocated to a data area subsequent to the data area having been allocated in S of the storage for write unit according to a size of the data area.

In S from among the system information any control instruction item having the input output direction of read only is selected.

In S a data area of the control instruction item each selected in S is sequentially allocated to a data area subsequent to the data area having been allocated in S of the storage for read unit according to a size of the data area.

A difference between the flowchart of and the flowchart of is the same as a difference between S and S. In S a data area of the control instruction item each selected in S is sequentially allocated according to the size of the data area to a data area subsequent to the data area having been allocated in S of the storage for read unit plus the data area having been allocated in S of the storage for write unit . This makes it possible to allocate the data area in the storage for write unit in which the input output direction is only read and the data area in the storage for read unit in which the input output direction is only write from respective start addresses different from each other.

Using the steps of to as described above the packet generation information registration unit allocates the data area of each record in the system information to the data storage unit .

The packet generation information registration unit then generates the packet generation information from the system information . As described in the packet generation information registration unit copies the data of the packet generation information other than the address from the corresponding data of the system information and writes an address resultant from the allocation shown in and at the address of the packet generation information .

The packet generation information registration unit registers the generated packet generation information in the packet generation information storage unit via the API .

Similarly to illustrates steps in which in allocating a data structure for each slave identifier the data structure is allocated from the same start address to both a data area in the storage for write unit of which input output direction is write only and an area in the storage for read unit of which input output direction is read only.

In allocating a data structure to the data storage unit steps from S to S of correspond to steps from S to S of . Note that a result obtained from the allocation of a data structure is herein written out not to the address of the packet generation information but to the built control instruction structure .

The control instruction structure includes for example a structure of C language having the control instruction name as a variable name and the size as a variable type a union definition and a class definition of an object oriented language.

As the control instruction structure for example a structure of C language as follows is generated from the system information of 

Herein the variable name such as position is that the control instruction name is represented in lower case letters. The data type int which means a 4 byte integer type is determined from the size . The API for accessing to the structure is for example as follows 

The first line represents an API which assigns a specified value to the position variable. The second line represents an API which acquires a value from the position variable.

Note that owing to restrictions of C language for example the control instruction name of the control instruction structure is written in English and a space a tab character or the like is replaced with an underscore   . If the size is larger than a variable type defined by C language or does not correspond with a size of a given variable type an array based definition is made for example.

In some cases where the control instruction structure is built the control instruction structure needs to be made into the same specific size due to restrictions of a software environment running on the CPU a compiler for generating the application or the like. For example if the size is not in terms of bytes several bits of a value of 0 are added to the size . This allows the size to be represented in terms of bytes and the control instruction structure to be subjected to allocation of a data area. In another case where the CPU is of 32 bit type depending on a compiler components control instructions of a structure are arrayed by the 4 byte. In this case the library and the API are made to absorb a difference between allocation of the control instruction structure and allocation of the data storage unit . Alternatively data structures are allocated to the data storage unit such that data areas thereof are consistent with one another.

In S the control instruction structures built in S S and S are collected into one control instruction structure as a unitary control instruction structure corresponding to the slave selected in S. Herein the collected control instruction structure is built so as to have a data structure same as that allocated to the data storage unit by the packet generation information registration unit using the steps of .

Note that when a data structure is allocated to the data storage unit and the control instruction structure is built in S and S the data area having the input output direction of write only in the storage for write unit has a beginning address location same as that of the data area having the input output direction of read only in the storage for read unit . Thus if the control instruction structure is built a method of specifying the same area is required. One of such specific examples is a union of C language.

In S if there is no slave which has not yet been subjected to the allocation in S if No in S the control instruction structures built for each slave are collected into a unitary control instruction structure . Also in this case the unitary control instruction structure is built so as to have a data structure same as that allocated to the data storage unit by the packet generation information registration unit using the steps of .

In S upon an instruction from the developer the development computer invokes an instruction of making the packet generation information registration unit analyze the system information .

In S the packet generation information registration unit allocates a data structure to the data storage unit and writes a result of the allocation to the packet generation information details of which are described in the steps of any of the flowcharts of to and which flowchart is to be executed is determined by for example a selection or an entry from the developer .

In S upon an instruction from the developer the development computer invokes an instruction of making the control instruction structure unit analyze the system information .

In S the control instruction structure unit allocates a data structure to the data storage unit and creates the control instruction structure based on a result of the allocation details of which is described in the processing shown in the flowchart of or the like .

In S the development computer receives an input of the program source from the developer. The program source is created using the control instruction structure in S and the API .

In S upon an instruction from the developer the development computer converts by compiling byte code conversion or the like the program source into an executable form and makes a result obtained from the conversion such as a binary file operate on the control computer .

Note that the API includes an API which associates the control instruction structure with a data structure of the data storage unit . One of specific examples of such an API is a mmap function which is a system call of UNIX registered trademark . The API also includes an API which reads and writes the control instruction structure . In such an API a processing of aligning a byte boundary of a data structure or a consistency between a control instruction structure of setting an instruction value and an input output direction is verified.

The API also includes an API which instead of reading and writing an instruction value directly from and to the data storage unit associated with a mmap function or the like builds the control instruction structure in the memory brings together all of the built control instruction structures and makes the data storage unit read and write the brought together result.

That is a main difference between the packet generation information and the control instruction structure is that the packet generation information associates each variable that is each record of with one address and on the other hand the control instruction structure associates each structure which is obtained by grouping together one or more variables with one start address of the data storage unit . As described a processing is performed using the structure which is a large data block as a unit which can reduce the number of addresses to be managed.

The API also includes an API which makes the communication LSI transmits a packet and an API which receives a packet from the communication LSI .

A data area which is allocated into the data storage unit as a data structure may be not a control instruction or a result after control but a frame image or a mailbox command. In this case the application cannot be developed using the control instruction structure . However a communications protocol can be operated not in a computation of a control instruction but in an application.

Next is described the second embodiment. The second embodiment differs from the first embodiment in that a data structure is allocated to the data storage unit using a logical address space. Except that the second embodiment basically has the same configuration and operations as those of the first embodiment. Description hereinafter is made especially featuring the difference.

The bus address is a bus address of the address associated therewith in the address association information .

The logical address is an address in a logical address space associated therewith in the address association information .

For example in the address association information of addresses 0xef000000 to 0xef00FFFF on the bus are associated with EtherCAT registered trademark specified logical address spaces of 0x10000 to 0x1FFFF which are further associated with addresses 0x0 to 0xFFFF in the data storage unit .

The logical address is a logical address targeted by a packet generated from the packet generation information .

The input output direction indicates whether the generated packet is for read for write or for read write. Herein in this embodiment an EtherCAT registered trademark command to a logical address is to be generated and thus the input output direction uniquely determines a command to a logical address LRD LWR and LRW .

In S the system information received by the development computer is constituted only by a command to a logical address LRD LWR and LRWcommand .

S is similar to S and is different therefrom only in contents of the system information received in S.

In S the packet generation information registration unit allocates a data structure to the data storage unit and writes an address obtained from a result of the allocation as the address association information and the packet generation information via the address correction value management unit .

In S the packet generation unit starts operating. Note that the operation management unit controls a timing of starting S. For example the timing may be when the application running on the CPU makes an instruction to the operation management unit via the bus connection unit or when the operation management unit makes the packet generation unit start operating at a preset interval.

In S it is determined whether or not there is a not yet processed record of the packet generation information is in the packet generation information storage unit . If Yes in S the processing advances to S. If No in S the processing advances to S.

In S one not yet processed record of the packet generation information is extracted from the packet generation information storage unit .

In S it is determined whether or not the record of the packet generation information has the input output direction including write . If Yes in S the processing advances to S. If No in S the processing advances to S.

In S a data as large as the size shown in the packet generation information is extracted from the address shown in the packet generation information in the storage for write unit of the data storage unit .

Note that in S of the second embodiment an address of the data extracted from the storage for write unit is determined by the logical address and the address association information . That is a record including the logical address is searched from the address association information . The address of the searched record of the address association information is an address of the data extracted from the storage for write unit .

In S it is determined whether or not the record of the packet generation information has the input output direction including read . If Yes in S the processing advances to S. If No in S the processing advances to S. Note that if the input output direction includes both read and write there is no need to perform S after S because necessary data is generated from the storage for write unit .

In S a packet a telegram. of is generated from the data extracted in S or the data generated in S based on the packet generation information .

Note that in the telegram header information a telegram header of or the like which is not dependent on each packet is extracted from the operation management unit .

In S there exists no not yet processed record of the packet generation information if No in S one or more packets generated in S the telegram of are collected into a unitary packet the Ethernet frame of and the unitary packet is transmitted to the data transmission unit . Note that the Ethernet header and the FCS in the Ethernet frame of may be added at the data transmission unit .

In S if there is a record of the packet generation information which has the input output direction not including read the record is abnormal which is notified accordingly. For example the packet generation unit notifies the operation management unit of the abnormality and the notification is made to be obtainable from an application running on the CPU . Alternatively the operation management unit performs an interrupt for notifying the CPU of the abnormality.

Each telegram includes one telegram header one telegram data and one working counter WKC . One telegram data stores therein a data which is read or write in one or more slaves. That is one Ethernet frame includes a data which is read and write in a plurality of slaves. The working counter is a field in which each time a telegram is subjected an appropriate processing in an appropriate slave a prescribed number of times is counted up by the slave. A processing of creating the telegram corresponds to S of .

In the packet generation unit operates with the packet generation information which is fixed. However the packet generation information may be dynamically changed according to an application running on the CPU . Or a record of the packet generation information to be subjected to the processing may be selected from among a plurality of records of the packet generation information . In the latter case each record of the packet generation information includes an additional item indicating whether the record is available or not.

The packet generation unit may advance the processing to S for example in the following cases even if there is still a record of the packet generation information which has not yet been subjected to the processing in S of FIG. 

In S the packet filter unit starts operating. Note that S is started at a timing when the data reception unit receives a packet and transmits the packet to the packet filter unit . The data reception unit extracts one or more telegrams from one Ethernet frame and transmits the extracted telegrams to the packet filter unit one by one.

In S it is determined whether or not there is a record of the packet generation information corresponding to the received packet the telegram in the packet generation information storage unit . If Yes in S the processing advances to S. If No in S the processing terminates the processing of .

In S the record of the packet generation information corresponding to the packet received from the packet generation information storage unit is extracted.

In S it is determined whether or not the extracted record of the packet generation information has the input output direction of write. If Yes in S the processing advances to S. If No in S the processing returns to S.

In S a necessary data is extracted from the received packet and is stored in the storage for read unit . A data area thereof starts at the address and is as large as the size shown in the record of the packet generation information extracted in S.

Note that in S of the second embodiment an address at the starting point of a data area in a storage unit is determined using the logical address and the address association information . That is the logical address of the address association information is searched to detect whether or not any logical address includes the logical address . The address of the address association information is an address of a data to be stored in the storage for read unit .

According to the first and second embodiments of the present invention described above an information processing apparatus having improved development efficiency and communication performance can be provided.

With respect to the improved development efficiency a developer can develop the program source so as to develop the application making use of the control instruction structure and the API . This makes it possible for the developer to efficiently develop the application without much need of going into details of a network protocol or taking an address location of each control instruction into account.

With respect to the improved communication performance the communication LSI and the application running on the CPU can be executed in parallel. Further a control instruction can be transmitted to the communication LSI by an API such as a mmap function instead of using a protocol stack thus allowing a communication processing time in software to be reduced.

The embodiments according to the present invention have been explained as aforementioned. However the embodiments of the present invention are not limited to those explanations and those skilled in the art ascertain the essential characteristics of the present invention and can make the various modifications and variations to the present invention to adapt it to various usages and conditions without departing from the spirit and scope of the claims.

