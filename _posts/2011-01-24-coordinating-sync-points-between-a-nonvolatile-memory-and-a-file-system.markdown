---

title: Coordinating sync points between a non-volatile memory and a file system
abstract: Systems and methods for coordinating sync points between a non-volatile memory (“NVM”) and a file system are provided. In some embodiments, a file system can issue one or more commands to control circuitry of a NVM, which can indicate whether a transaction is journaled or non-journaled. This way, the control circuitry can maintain a list of journaled transactions and corresponding LBA(s). By keeping track of journaled transactions, the control circuitry can ensure that sync points are not prematurely erased during a garbage collection process. In addition, upon detecting device failure events, the control circuitry can roll back to sync points corresponding to one or more journaled transactions.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08458133&OS=08458133&RS=08458133
owner: Apple Inc.
number: 08458133
owner_city: Cupertino
owner_country: US
publication_date: 20110124
---
NAND flash memory as well as other types of non volatile memories NVMs are commonly used for mass storage. For example consumer electronics such as portable media players often include flash memory to store music videos and other media.

Some systems can provide metadata journaling in order to keep track of updates made to files and folders before committing those updates to a file system. Metadata journaling can facilitate system recovery from power failures device failures and other unexpected events.

Conventionally a system may provide for metadata journaling on top of a NVM device. While this may provide some data recovery capabilities such a configuration may be unable to ensure data consistency in response to unexpected device failures. That is after the system recovers from a device failure the system may fall into an incoherent state where some portions of a file may contain old data and other portions of the file may contain updated data.

Systems and methods are disclosed for coordinating sync points between a non volatile memory NVM and a file system. As used herein a sync point can refer to the valid data states of one or more LBAs associated with a journaled transaction immediately prior to the start of the transaction. In particular a non volatile memory and a file system can have coordinated sync points such that a system can roll back to known valid states for specific transactions in case of device failure events.

Systems and methods for coordinating sync points between a non volatile memory NVM and a file system are provided. As used herein a sync point can refer to the valid data states of one or more LBAs associated with a journaled transaction immediately prior to the start of the transaction.

In some embodiments the file system can issue one or more commands to a control circuitry of the system where the commands can indicate whether a transaction is journaled or non journaled. Using this information the control circuitry can maintain a list of journaled transactions where each entry of the list of journaled transactions can correspond to a particular journaled transaction and its corresponding LBA s .

By keeping track of journaled transactions the control circuitry can ensure that sync points are not prematurely erased during a garbage collection GC process. For example when the control circuitry determines that GC needs to be performed on the NVM the control circuitry can search a block or super block to determine whether the block or super block includes a journaled transaction e.g. based at least in part on the list of journaled transactions . If the block or super block includes a journaled transaction the control circuitry can determine not to perform GC on the block or super block but rather select a new block or superblock for GC.

In addition upon detecting device failure events the control circuitry can roll back to sync points corresponding to one or more journaled transactions. For example after a device failure event has been detected in the system the control circuitry can identify at least one journaled transaction. In addition the control circuitry can locate a sync point for the identified transaction. Upon locating the sync point the control circuitry can roll back the particular journaled transaction to the sync point.

In some embodiments for journaled transactions one or more markers can be programmed in a block along with other metadata. The markers can be used by the control circuitry to distinguish between journaled and non journaled transactions.

System can include file system NVM driver NVM bus controller and NVM package . In some embodiments file system and NVM driver may be software or firmware modules and NVM bus controller may be a hardware module. Accordingly in these embodiments NVM driver may represent the software or firmware aspect of NVM interface and NVM bus controller may represent the hardware aspect of NVM interface .

NVM package can include NAND flash memory based on floating gate or charge trapping technology NOR flash memory erasable programmable read only memory EPROM electrically erasable programmable read only memory EEPROM Ferroelectric RAM FRAM magnetoresistive RAM MRAM or any combination thereof.

NVM can be organized into blocks which is the smallest erasable unit and further organized into pages which can be the smallest unit that can be programmed or read. In some embodiments NVM can include multiple dies where each die may have multiple blocks. The blocks from corresponding die e.g. blocks having the same position or block number may form super blocks . Each memory location e.g. page or block of NVM can be addressed using a physical address e.g. a physical page address or physical block address .

In some embodiments NVM package can be a managed NVM package. As used herein a managed NVM may refer to a memory device or package that includes a NVM controller configured to perform at least one memory management function for a non volatile memory. For example as shown in NVM controller can perform memory management functions for any suitable number of blocks of NVM .

NVM controller may include any suitable combination of processors microprocessors or hardware based components e.g. ASICs . For example NVM controller may share the responsibility of managing and or accessing the physical memory locations of NVM with NVM driver . Alternatively NVM controller may perform substantially all of the management and access functions for NVM .

Memory management and access functions that may be performed by NVM controller can include issuing read write or erase instructions and performing wear leveling bad block management garbage collection logical to physical address mapping SLC or MLC programming decisions applying error correction or detection and data queuing to set up program operations.

Persons skilled in the art will appreciate that NVM package may alternatively be a raw NVM package. As used herein a raw NVM may refer to a memory device or package that may be managed entirely by a host controller external to the NVM package. In such embodiments a host controller not shown in of system which can be used to control system operations through use of one or more processors can also be used to control and manage the memory locations of NVM and the data stored therein. For simplicity components of a system that can manage a NVM e.g. portions of the host controller and NVM interface or NVM controller may sometimes be referred to simply as a control circuitry .

File system can include any suitable type of file system such as a File Allocation Table FAT file system or a Hierarchical File System Plus HFS . File system can manage file and folder structures required for system to function.

File system may provide write and read commands to NVM driver when an application or operating system requests that information be read from or stored in NVM . Along with each read or write command file system can provide a logical address indicating where the data should be read from or written to such as a logical page address or a logical block address LBA with a page offset.

File system may provide read and write requests to NVM driver that are not directly compatible with NVM package . For example the LBAs may use conventions or protocols typical of hard drive based systems. A hard drive based system unlike flash memory can overwrite a memory location without first performing a block erase. Moreover hard drives may not need wear leveling to increase the lifespan of the device. Therefore NVM interface can perform any functions that are memory specific vendor specific or both to handle file system requests and perform other management functions in a manner suitable for NVM package .

NVM driver can include translation layer . In some embodiments translation layer may be or include a flash translation layer FTL . On a write command translation layer can map the provided logical address to a free erased physical location on NVM . On a read command translation layer can use the provided logical address to determine the physical address at which the requested data is stored. Because each NVM may have a different layout depending on the size or vendor of the NVM this mapping operation may be memory and or vendor specific. Translation layer can perform any other suitable functions in addition to logical to physical address mapping. For example translation layer can perform any of the other functions that may be typical of flash translation layers such as garbage collection and wear leveling.

NVM driver may interface with NVM bus controller to complete NVM access commands e.g. program read and erase commands . Bus controller may act as the hardware interface to NVM package and can communicate with NVM package using the bus protocol data rate and other specifications of NVM package .

NVM interface may manage NVM package based on memory management data sometimes referred to herein as metadata . The metadata may be generated by NVM driver or may be generated by a module operating under the control of NVM driver . For example metadata can include any information used for managing the mapping between logical and physical addresses bad block management wear leveling ECC data used for detecting or correcting data errors markers used for journaling transactions or any combination thereof.

The metadata may include data provided by file system along with the user data such as a logical address. Thus in general metadata may refer to any information about or relating to user data or used generally to manage the operation and memory locations of a non volatile memory. NVM interface may be configured to store metadata in NVM .

In some embodiments system can provide for transaction journaling. As used herein transaction journaling can refer to a process that is used to keep track of particular transactions in system such that a consistent state can be achieved after a device failure event e.g. a power failure event or a system crash .

Conventionally a system may be unable to ensure data consistency in response to unexpected device failures. For example a device failure event may occur when a file system is in the middle of a file or folder structure update. During a boot up process following the device failure event the file or folder structure may reach an inconsistent state because the system is unable to determine a valid data state corresponding to the file or folder structure.

In order to ensure data consistency system can provide for atomicity in one or more transactions such that in response to a device failure event data e.g. user data and metadata associated with journaled transactions can be rolled back to a valid state. In particular system can provide coordinated sync points between file system and NVM package in order to achieve consistent states through all layers of system e.g. through the application or operating system layer the file system layer and the NVM layer .

For example when an application or operating system initiates a transaction on one or more files or folder structures file system can detect the transaction and can issue one or more commands to a control circuitry. In some embodiments the one or more commands can be in the form of an application programming interface API operation. An API can be any suitable interface that can allow a software program or module to interact with other software.

For instance upon detecting a transaction file system via NVM interface can assign a transaction ID to the newly initiated transaction and can issue a command e.g. an API operation to the control circuitry indicating that a transaction has been newly initiated. In some cases the command may include the transaction ID as a parameter. For example a BEGIN TRANSACTION command associated with the newly initiated transaction can be issued to the control circuitry with the following format BEGIN TRANSACTION TRANSACTION ID 1 where TRANSACTION ID corresponds to the transaction ID that has been assigned by file system to the newly initiated transaction.

File system can assign any suitable value to a transaction ID. In some embodiments transaction IDs can be selected based on whether a particular transaction is a journaled transaction or a non journaled transaction. For instance if a transaction is a non journaled transaction the file system can assign a specific default value to the TRANSACTION ID. If on the other hand a transaction is a journaled transaction the file system can assign a non default value to the TRANSACTION ID.

Furthermore if the application or operating system requests to write data for this transaction file system can issue via NVM interface a write command e.g. an API operation to the control circuitry with the following format WRITE USER DATA LBA AGE TRANSACTION ID 2 where USER DATA corresponds to the user data to be written LBA corresponds to the one or more LBAs associated with the transaction AGE corresponds to the age of the user data and TRANSACTION ID corresponds to the transaction ID of the transaction. In some cases LBA AGE and TRANSACTION ID can be metadata associated with the transaction. In addition to or instead of the parameters shown in 2 persons skilled in the art will appreciate that the WRITE command can include any other suitable parameters such as for example a counter a buffer and or ECC data.

In response to receiving the WRITE command control circuitry can program the user data and associated metadata to one or more memory locations of NVM . In addition in response to receiving the BEGIN TRANSACTION command and the WRITE command the control circuitry can update a list of journaled transactions. The list of journaled transactions can be used to keep track of pending journaled transactions where each entry can include a journaled transaction and its corresponding LBA s . The list of journaled transaction can be stored in volatile memory not shown in or non volatile memory e.g. NVM and will be discussed in more detail in connection with the following figures.

In some cases a particular transaction may be kept open for a period of time. Accordingly over a period of time file system via NVM interface can issue multiple API operations e.g. write or read commands associated with the same transaction to control circuitry.

In addition during a particular period of time file system can simultaneously handle multiple transactions. For example file system can detect a new transaction after issuing the WRITE command provided in 2 . In response to detecting the new transaction file system can assign a new TRANSACTION ID to the transaction and issue a corresponding command to the control circuitry.

Once the application or operating system has finished updating the file or folder structure file system can detect an end of the transaction and issue a corresponding command to the control circuitry. For example file system via NVM interface can issue an end transaction command indicating that the transaction has ended with the following format END TRANSACTION TRANSACTION ID 3 

In response to receiving the END TRANSACTION command the control circuitry can update the list of journaled transactions by removing the transaction and its associated LBA s from the list.

Referring now to graphical views of three blocks e.g. blocks and of a NVM e.g. NVM of are shown at various stages of a transaction. Persons skilled in the art will appreciate that the memory locations where the user data and metadata are stored in blocks and are merely illustrative. For example in some embodiments user data and corresponding metadata may be stored in the same memory locations e.g. pages of a block. In other embodiments user data and corresponding metadata may be stored in different blocks. Persons skilled in the art will also appreciate that other types of metadata can also be stored in blocks and . For example ECC data can be stored in one or more portions of blocks and .

As shown in block may include data and metadata associated with a particular file or folder structure. In particular metadata can include LBA metadata and age metadata which can have values of x and a 1 respectively.

Moreover as shown in block may include data and metadata associated with another file or folder structure. In particular metadata can include LBA metadata and age metadata which can have values of y and n 1 respectively.

Referring now to at time t file system e.g. file system of via a NVM interface e.g. NVM interface of can issue a begin transaction command and a write command to a control circuitry. For example the following two commands may be issued to the control circuitry BEGIN TRANSACTION 0 4 WRITE USER DATA10 5 where TRANSACTION ID has a value of 0 USER DATA has a value of USER DATA x1 LBA has a value of x and AGE has a value of a. Thus the file system may be writing to the same LBAs as LBAs previously stored in the NVM e.g. LBA x .

In response to receiving the WRITE command control circuitry can program user data e.g. user data to block . In addition the control circuitry can program corresponding metadata to block . For example as shown in the programmed metadata can include LBA metadata and age metadata which can have values of x and a respectively.

At the same time in response to receiving the BEGIN TRANSACTION command the control circuitry can determine if the TRANSACTION ID associated with the BEGIN TRANSACTION command indicates that the transaction is a journaled transaction e.g. TRANSACTION ID has a non default value . Upon determining that the transaction is a journaled transaction the control circuitry can update a list of journaled transactions by adding the TRANSACTION ID and associated LBAs to the list. For example Table 1 shows an illustrative list of journaled transactions after the list has been updated.

At time t the control circuitry can receive other commands from the file system. For example the file system may initiate another transaction and issue the following two commands to the control circuitry via the NVM interface BEGIN TRANSACTION 1 6 WRITE USER DATA11 7 where TRANSACTION ID has a value of 1 USER DATA has a value of USER DATA y1 LBA has a value of y y and AGE has a value of n. Thus although the file system is writing to some of the same LBAs as LBAs previously stored in the NVM e.g. LBA y the file system is also writing to new LBAs e.g. LBA y .

In response to receiving the WRITE command the control circuitry can program user data e.g. user data to block . In addition the control circuitry can program metadata associated with the write command to block . For example as shown in the programmed metadata can include LBA metadata and age metadata which can have values of y y and n respectively.

In response to receiving the second BEGIN TRANSACTION command the control circuitry can determine that the transaction is a journaled transaction and add the newly initiated transaction to the list of journaled transactions. For example Table 2 shows an illustrative list of the currently journaled transactions after the list has been updated.

Although only two transactions are shown in Table 2 persons skilled in the art will appreciate that the control circuitry can provide for the concurrent journaling of any suitable number of transactions.

Referring now to a flowchart of illustrative process is shown for reading user data from a NVM e.g. NVM of . The steps of process can be executed by a control circuitry e.g. portions of a host controller and NVM interface of or NVM controller of or by any other component or combination of components of an electronic device or system e.g. system of .

Process can begin at step where a file system e.g. file system of may issue a read command to the control circuitry via a NVM interface such as NVM interface of in order to perform a read operation on a particular file or a folder structure.

At step the control circuitry can receive the read command to read user data associated with the file or folder structure. At step the control circuitry can scan a journaled transaction list to determine which LBAs are associated with a currently journaled transaction. Any suitable approach can be used to scan the journaled transaction list such as for example a list traverse hashing or any other suitable algorithm.

For instance referring now specifically to in response to receiving a read command to read LBA x the control circuitry can scan the journaled transaction list of Table 2 to determine that LBA x corresponds to a journaled transaction.

Continuing to step the control circuitry can search for the most current version of user data stored in the NVM that corresponds to the LBAs. In some embodiments the control circuitry can search for a version of the user data that has the youngest age. In the example shown in for instance the control circuitry can determine that the most current version of user data for LBA x is stored on block of e.g. age a .

Then at step the control circuitry can obtain the user data associated with the most current version. For example the control circuitry can obtain user data of block which can correspond to the most recently programmed user data associated with LBA x. At step the control circuitry can transmit the user data to the file system via the NVM interface . Process can then end at step .

Referring back to at time t the file system can issue via the NVM interface a write command to update the user data associated with TRANSACTION ID 0. For example the write command can have the following format WRITE USER DATA21 0 8 where user data has a value of USER DATA x2 LBA has a value of x AGE has a value of a 1 and TRANSACTION ID has a value of 0.

In response to receiving this WRITE command the control circuitry can program user data e.g. user data to block . In addition the control circuitry can program metadata associated with the write command to block . For example as shown in the programmed metadata can include LBA metadata and age metadata which can have values of x and a 1 respectively. Consequently although the file system is writing new data to the same LBAs as before e.g. LBA x age metadata has been changed to reflect that user data is an updated version of user data .

After issuing the write command the file system may detect an end of the transaction for TRANSACTION ID 0 e.g. the application or the operating system may have finished updating the file or folder structure . In response to detecting the end of the transaction the file system may issue an end transaction command for the transaction via the NVM interface. For example the following command may be issued to the control circuitry END TRANSACTION 0 9 

In response to receiving the END TRANSACTION command the control circuitry can update the list of journaled transactions by deleting TRANSACTION ID 0 and its associated LBA s from the list. For example Table 3 shows an illustrative list of the currently journaled transactions after the update.

At time t the file system can issue a write command to update the user data associated with TRANSACTION ID 1 via the NVM interface. For example the WRITE USER DATA2 1 1 10 where USER DATA has a value of USER DATA y2 LBA has a value of y y AGE has a value of n 1 and TRANSACTIONID has a value of 1.

In response to receiving the WRITE command the control circuitry can program user data e.g. user data to block . In addition the control circuitry can program updated metadata associated with the write command in block . For example as shown in the programmed metadata can include LBA metadata and age metadata which can have values of y y and n 1 respectively. Consequently although the file system is writing new data to the same LBAs as before e.g. LBAs y and y age metadata has been changed to reflect that user data is an updated version of user data .

Referring now to flowcharts of illustrative processes and are shown in accordance with various embodiments of the invention. Processes and can be executed by a control circuitry e.g. portions of a host controller and NVM interface of or NVM controller of or by any other component or combination of components of an electronic device or system e.g. system of .

Turning first to process may illustrate steps used to perform garbage collection GC on a block or super block of a NVM e.g. NVM of . In particular GC may be performed on one or more blocks or super blocks of the NVM when additional space needs to be made available on the NVM for programming. Thus in order to free up space for reprogramming data stored on the one or more blocks or super blocks can be erased.

Before performing GC on the NVM the control circuitry may first need to verify that LBAs programmed in a journaled transaction will not be erased. That is for a multi page multi call transaction older versions of LBAs that have been programmed in the journaled transaction may need to be retained such that the transaction can behave atomically. In some cases in order to ensure atomicity of transactions the control circuitry may delay erasing older versions of LBAs of a journaled transaction until after the transaction is complete.

Process may start at step where the control circuitry may determine that GC needs to be performed on a NVM. At step the control circuitry can search a list of journaled transactions in order to identify which LBAs have been programmed in one or more journaled transactions. For example based on the list of journaled transactions in Table 3 the control circuitry can determine that LBAs y and y are still associated with a journaled transaction e.g. TRANSACTION ID 1 .

Then at step the control circuitry can cross check the LBAs stored in a block or super block with the LBAs that have been programmed in one or more journaled transactions. For example the control circuitry can cross check the LBAs stored in block with LBAs y and y .

Continuing to step the control circuitry can determine if there is a conflict. That is the control circuitry can determine whether the block or super block includes LBAs that have been programmed in one or more journaled transactions. If at step the control circuitry determines that there is no conflict e.g. the block or super block does not include LBAs that have been programmed in one or more journaled transactions process can move to step .

At step the control circuitry can perform GC on the block or super block. Process may then end at step .

Referring back to step if the control circuitry instead determines that there is a conflict e.g. the block or super block includes LBAs that have been programmed in one or more journaled transactions process can move to step . For example for block the control circuitry can determine that there is a conflict because block has user data associated with LBA y e.g. user data . As a result the control circuitry can determine that GC is inappropriate for block .

At step the control circuitry can select a new block or super block for GC. Process may then return to step where the control circuitry can cross check the LBAs stored in the new block or super block with the LBAs that have been programmed in one or more journaled transactions.

Accordingly in contrast to conventional approaches that erase data stored in a block when the block has been filled and no program failures have been detected e.g. no uncorrectable error correction coding uECC errors this approach ensures that the system can roll back to known valid states e.g. sync points for one or more journaled transactions. As used herein a sync point can refer to valid data states of LBAs associated with a transaction immediately prior to the start of that transaction.

For instance in the example shown in user data corresponds to a valid data state of LBA y immediately prior to the start of a transaction with TRANSACTION ID 1. Thus the memory locations of user data and metadata of block provide the locations of a sync point for LBA y.

As another example because the transaction with TRANSACTION ID 0 ended at time t user data corresponds to a valid data state for LBA x. Thus the memory locations of user data and metadata provide the locations of a sync point for LBA x.

By preserving older versions of data associated with a transaction while a transaction is still pending the system can roll back to the front of the transaction in case of device failure events. This way the system can avoid a situation where the system is unable to roll back to a known valid state because older sync points have been erased during a GC process.

In addition the coordination of sync points between the file system and the NVM can provide coherency from the perspective of an application or an operating system. In particular for a system that only provides data roll back at the NVM level the roll backs may still be incoherent from an application or operating system perspective.

For example a particular file may have five different sectors where user data associated with three sectors of the file may be stored on a first block that has been fully programmed. In addition user data associated with two sectors of the file may be stored on a second block that is currently open. If a program failure was detected in a page of the second block the system may roll back to that page in order to maintain time order consistency. However this may in fact result in an inconsistent state from an application perspective because the file now includes two sectors with updated data and three sectors with data that have been rolled back to an older version.

Accordingly by involving the file system and keeping track of individual transactions a system can roll back an entire file or folder structure to a consistent state from an application or operating system perspective. This consistent data roll back can be ensured even when data associated with a single transaction are stored on multiple blocks.

Referring now to a flowchart of illustrative process is shown for rolling back a transaction to a sync point. Process may begin at step where a device may be booted up after a device failure event. A device failure event can include for example a power failure event or a system crash. At step a control circuitry can detect that a device failure event has occurred.

At step in response to detecting that a device failure event has occurred the control circuitry can identify one or more journaled transactions. For example the control circuitry can search a list of journaled transactions and determine LBAs corresponding to each journaled transaction using the list of journaled transactions.

For instance based on the list of journaled transactions shown in Table 3 the control circuitry can determine that there is currently one journaled transaction e.g. TRANSACTION ID 1 and that LBAs y and y correspond to the journaled transaction.

Continuing to step the control circuitry can locate a sync point for each of the one or more journaled transactions. Any suitable approach can be used to locate a sync point. In some embodiments the control circuitry can search for the physical address of the oldest data in the NVM that is associated with each of the one or more journaled transactions. The oldest data may be determined by comparing corresponding age metadata stored on one or more blocks or super blocks e.g. by comparing ages and .

For instance for TRANSACTION ID 1 the oldest data associated with the transaction is located on block e.g. user data has an age of n 1 . The location of the sync point can therefore be identified as the corresponding physical addresses of user data and metadata in block .

In other embodiments the control circuitry can search a tree that is maintained and stored in the system such as for example in volatile memory or non volatile memory e.g. NVM of . The tree can include any suitable tree structure for storing logical to physical address mappings.

In some cases the logical to physical address mappings of the tree can be updated only once a transaction has ended. Thus by searching the tree for LBAs associated with a journaled transaction the control circuitry can locate a proper sync point for that transaction e.g. the physical location of LBAs associated with the journaled transaction immediately prior to the start of the transaction .

At step the control circuitry can roll back each of the one or more journaled transactions to the corresponding sync point in a NVM e.g. NVM of . That is the control circuitry can discard any data programmed during the one or more journaled transactions and revert back to valid data states prior to the start of the transactions. Process may end at step .

Turning now to a flowchart of illustrative process is shown for locating a sync point for a journaled transaction. In some embodiments process may represent a more detailed view of locating step of process .

Process may start at step . At step control circuitry can determine a LBA that has been programmed in a journaled transaction e.g. a journaled transaction such as TRANSACTION ID 1 . For example the control circuitry can determine the LBA by searching a list of journaled transactions.

Then at step the control circuitry can determine whether the LBA is in a tree. If the control circuitry determines that the LBA is in the tree process may move to step .

For instance based on the list of journaled transactions shown in Table 3 the control circuitry can determine that LBA y is associated with TRANSACTION ID 1 and that LBA y is listed in the tree. This can be an indication that a file or folder structure is being updated in place. Moreover because TRANSACTION ID 1 has not yet ended the tree includes the physical address of the valid user data for LBA y.

At step the control circuitry can identify a corresponding physical address in the tree as the location of a sync point for the journaled transaction. For example for LBA y the control circuitry can find the location of the sync point based on the physical address stored in the tree that maps to LBA y. Process may then end at step .

Referring back to step if the control circuitry instead determines that the LBA is not in the tree process may move to step . This may be in an indication that the LBA is a new LBA that has been programmed during a journaled transaction and is therefore not a sync point for the journaled transaction. For instance based on the list of journaled transactions shown in Table 3 the control circuitry can determine that LBA y is associated with TRANSACTION ID 1 but that LBA y is not listed in the tree.

At step the control circuitry can ignore the LBA. Then at step the control circuitry can determine whether there are any additional LBAs that are associated with the journaled transaction. If at step the control circuitry determines that there are additional LBAs that are associated with the journaled transactions process may return to step where the control circuitry can determine another LBA that has been programmed in the journaled transaction.

If at step the control circuitry instead determines that there are not any additional LBAs that are associated with the journaled transactions process may end at step .

In some embodiments control circuitry e.g. portions of a host controller and NVM interface of or NVM controller of can distinguish between journaled and non journaled transactions using one or more markers stored in the NVM. In particular the control circuitry can program one or more pages of a block with a marked or unmarked value indicating whether a transaction is journaled or non journaled.

Referring now to graphical views of four blocks e.g. blocks and of a NVM e.g. NVM of are shown at various stages of a transaction. Persons skilled in the art will appreciate that the memory locations where the user data and metadata are stored in blocks and are merely illustrative. For example in some embodiments user data and corresponding metadata may be stored in the same memory locations e.g. pages of a block. In other embodiments user data and corresponding metadata may be stored in different blocks. Persons skilled in the art will also appreciate that other types of metadata can also be stored in blocks and .

Turning now specifically to the physical address corresponding to user data may correspond to a valid data states for a transaction prior to the start of that transaction. Metadata may include LBA metadata e.g. LBA metadata and age metadata e.g. age metadata .

In addition metadata may include one or more markers indicating whether user data is associated with a journaled transaction. In some embodiments for example one or more pages of metadata may include a transaction ID marker associated with the user data. For example if user data is associated with a pending transaction with TRANSACTION ID 0 the transaction ID marker may have a value of 0.

In other embodiments because the amount of bit space available for transaction IDs may be limited and because transactions IDs may be recycled after a period of time the metadata can instead include a BEGIN transaction marker and an END transaction marker. BEGIN and END transaction markers may be programmed in any suitable manner. For example BEGIN and END transaction markers may be embedded in the metadata of the first and last pages of a transaction. As another example BEGIN and END transaction markers can be programmed in separate metadata pages.

As shown in for instance metadata can include BEGIN transaction marker and END transaction marker . Each of the markers can provide journaling information regarding a particular transaction. For example the value of BEGIN transaction marker can provide an indication of whether a particular transaction is a journaled transaction e.g. BEGIN transaction marker has a marked valued or a non journaled transaction e.g. BEGIN transaction marker has an unmarked valued . In some embodiments BEGIN and END transaction markers may have initial unmarked values prior to the start of a transaction.

Referring now to once a new transaction begins a BEGIN transaction marker associated with the transaction can be correspondingly updated. For instance the control circuitry can receive a BEGIN TRANSACTION command similar to the BEGIN TRANSACTION command shown in 4 . In addition the control circuitry can receive a WRITE command similar to the WRITE command shown in 5 .

In response to receiving these commands the control circuitry can determine if the TRANSACTION ID associated with the BEGIN TRANSACTION command indicates that the transaction is a journaled transaction e.g. TRANSACTION ID has a non default value . If the control circuitry determines that the transaction is a journaled transaction the control circuitry can program an associated BEGIN transaction marker with a marked value. If the control circuitry instead determines that the transaction is a non journaled transaction the associated BEGIN transaction marker can be left unprogrammed with an unmarked value.

For instance as shown in assuming that the transaction associated with LBA is a journaled transaction BEGIN transaction marker can be programmed with a marked value. In addition as mentioned above the control circuitry can update a list of journaled transactions with the transaction e.g. as shown in Table 1 .

Turning now to the control circuitry can receive a WRITE command similar to the WRITE command shown in 8 . In response to receiving the WRITE command the control circuitry can program user data and metadata e.g. including BEGIN transaction marker and END transaction marker .

Accordingly by maintaining one or more markers indicating which transactions are journaled a control circuitry can perform garbage collection more efficiently. For example because user data may only need to be rolled back to a sync point in the NVM older versions of user data that have been programmed during a journaled transaction can be erased once an updated version has been programmed for the transaction.

Referring now to a flowchart of illustrative process is shown for performing GC on a block or super block of a NVM e.g. NVM of in accordance with various embodiments of the invention. Process can be executed by a control circuitry e.g. portions of a host controller and NVM interface of or NVM controller of or by any other component or combination of components of an electronic device or system e.g. system of .

Process may start at step where the control circuitry may determine that GC needs to be performed on the NVM. At step the control circuitry can search a list of journaled transactions in order to identify which LBAs have been programmed in one or more journaled transactions. For example based on the list of journaled transactions shown in Table 1 the control circuitry can determine that LBA x is associated with a journaled transaction e.g. TRANSACTION ID 0 .

Continuing to step the control circuitry can search a block or super block to determine whether the block or super block includes a journaled transaction. In some embodiments the control circuitry can make this determination based at least in part on the list of journaled transactions and one or more markers stored on the block or super block. For example the control circuitry can determine that the block or super block has a BEGIN transaction marker with a marked value and a corresponding END transaction marker with an unmarked value. Based on this determination the control circuitry can determine LBAs associated with the markers based on metadata stored in the block or the super block. If at least a portion of the determined LBAs matches the LBAs obtained from the list of journaled transactions e.g. LBAs that have been programmed in at least one journaled transaction the control circuitry can determine that the block or super block includes a journaled transaction.

For instance referring specifically to for block the control circuitry can determine that BEGIN transaction marker has a marked value but END transaction marker has an unmarked value. As another example for block the control circuitry can determine that BEGIN transaction marker has a marked value but END transaction marker has an unmarked value. Moreover the control circuitry can determine that LBA x obtained from the list of journaled transactions in Table 1 matches the LBA associated with both sets of BEGIN and END transaction markers.

If at step the control circuitry determines that the block or super block includes a journaled transaction process can move to step .

At step the control circuitry can determine if the block or super block includes the newest version of user data corresponding to the journaled transaction. If at step the control circuitry determines that the block or super block does not include the newest version of user data corresponding to the journaled transaction process can move to step . That is the block or super block may contain user data that are all outdated e.g. the user data may correspond to older versions of more recently programmed user data . This may allow the control circuitry to perform GC on the block or super block even though the corresponding journaled transaction is still pending. For example if the block under consideration is block the control circuitry can determine that there is a newer version of LBA x stored in block .

At step the control circuitry can perform GC on the block or super block. Process may then end at step .

Referring back to step if the control circuitry instead determines that the block or super block includes the newest version of user data corresponding to the journaled transaction process can move to step . For example if the block under consideration is block the control circuitry can determine that the newest version of the LBA x is currently located in this block.

At step the control circuitry can select a new block or super block for GC. Process may then return to step where the control circuitry can search another block or super block to determine whether the block or super block includes a journaled transaction.

Referring back to step if the control circuitry instead determines that the block does not include a journaled transaction process can move to step . For example the block under consideration may be block of . At step the control circuitry can cross check LBAs stored in the block or super block with the LBAs that have been programmed in one or more journaled transactions. For example the control circuitry can cross check the LBAs stored in block with LBA x.

Continuing to step the control circuitry can determine if there is a conflict. That is the control circuitry can determine if the LBAs stored in the block or super block conflict with the LBAs that have been programmed in one or more journaled transactions. This may be an indication that the block or super block includes at least one sync point. As a result the control circuitry needs to ensure that the block or super block is not erased during a GC process.

If at step the control circuitry determines that the LBAs stored in the block or super block do not conflict with the LBAs that have been programmed e.g. the block or super block does not include LBAs that are associated with journaled transactions process can move to step . At step the control circuitry can perform GC on the block or super block.

Referring back to step if the control circuitry instead determines that the LBAs stored in the block or super block conflicts with the LBAs that have been programmed e.g. the block or super block includes LBAs that are associated with journaled transactions process can move to step . For example for block the control circuitry can determine that there is a conflict because block has LBAs associated with journaled transactions e.g. LBA x . As a result the control circuitry can determine that GC is inappropriate for block . Correspondingly at step the control circuitry can select a new block or super block for GC.

Turning now to the control circuitry can receive another WRITE command associated with TRANSACTION ID 0. In response to receiving this WRITE command the control circuitry can program user data and metadata in block . In addition the control circuitry may receive an END TRANSACTION command similar to the END TRANSACTION command shown in 9 .

In response to receiving the END TRANSACTION command the control circuitry can program END transaction marker with a marked value which can indicate that the transaction associated with LBA x has completed e.g. TRANSACTION ID 0 . In addition the control circuitry can update a list of journaled transactions by removing the entry associated with TRANSACTION ID 0.

It should be understood that processes and of are merely illustrative. Any of the steps may be removed modified or combined and any additional steps may be added without departing from the scope of the invention.

The described embodiments of the invention are presented for the purpose of illustration and not of limitation.

