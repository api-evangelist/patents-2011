---

title: Device driver for use in a data storage system
abstract: A device driver includes an aggregator aggregating data blocks into one or more container objects suited for storage in an object store; and a logger for maintaining in at least one log file for each data block an identification of a container object wherein the data block is stored with an identification of the location of the data block in the container object.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09256383&OS=09256383&RS=09256383
owner: AMPLIDATA NV
number: 09256383
owner_city: Lochristi
owner_country: BE
publication_date: 20110111
---
This application claims benefit of U.S. provisional application 61 314 240 filed Mar. 16 2010 which is incorporated herein by reference.

Cloud storage services are becoming well adopted by the market. Typically the cloud storage services are targeted at storing large amounts of objects or files redundantly in a distributed storage infrastructure. Cloud storage is used to offer public storage services over the internet or local enterprise storage over the local area network LAN . Enterprise storage systems typically use block devices that are accessed over storage area network SAN interfaces such as FibreChannel FC or iSCSI. The current invention offers a solution to make cloud storage accessible through a standard block device interface such that the cloud storage system can be used as an enterprise storage system.

In computing specifically data transmission and data storage a block is a sequence of bytes or bits having a nominal length which is also referred to as a block size. The process of putting data into blocks is used to facilitate the handling of the data stream by the computer program receiving the data. Blocked data are normally read a whole block at a time. This means that there is no means to address the data put inside a block.

Blocks in a block device are typically only 512 bytes large. An operating system that uses this block device would typically write or read 8 blocks at a time. Such a group of 8 blocks is typically referred to as a cluster. As such a cluster is a sequence of blocks that is written and read consecutively.

Block special files or block devices correspond to devices through which the operating system moves data in the form of blocks. Device nodes corresponding to these devices often represent addressable devices such as hard disks CD ROM drives or memory regions.

Logical Block Addressing LBA is a particularly simple linear addressing scheme. Blocks are located by an index with the first block being LBA 0 the second LBA 1 and so on. The LBA scheme replaces earlier schemes which exposed the physical details of the storage device to the software of the operating system. Chief among these was the cylinder head sector CHS scheme where blocks were addressed by means of a tuple which defined the cylinder head and sector at which they appeared on the hard disk. Current LBA schemes allow disks of size 128 PetaByte to be addressed assuming a block size of 512 bytes.

A storage snapshot is a set of reference markers or pointers to data stored on a disk drive on a tape or in a storage area network SAN . A snapshot is something like a detailed table of contents but it is treated by the computer as a complete data backup. Snapshots streamline access to stored data and can speed up the process of data recovery. In current storage technologies there are two main types of storage snapshot called the copy on write or low capacity snapshot and the split mirror snapshot. Utilities are available that can automatically generate either type.

A copy on write snapshot utility creates a copy of the existing data blocks at another location to store new data blocks in a given location every time existing data blocks are updated. This allows rapid recovery of data in case of a disk write error corrupted file or program malfunction. However all previous snapshots must be available when complete archiving or recovery of all the data on a network or storage medium is needed. The copy operation for every block of data that is updated slows down the write process significantly.

A split mirror snapshot utility references all the data on a set of mirrored drives. Every time the utility is run a snapshot is created of the entire volume not only of the new or updated data. This makes it possible to access data offline and simplifies the process of recovering duplicating or archiving all the data on a drive. However this is a slower process and it requires more storage space for each snapshot.

Cloning is the process of providing a copy of a point in time of data storage and allowing write operations on it without modifying the original data storage where this copy has been taken from.

MetaData in a block device and storage context is data that describes data operations when specific block operations have been executed on what data in what sequence and where these blocks or block changes are stored and how these can be addressed.

Cloud storage solutions are typically best suited to store large objects with a size of 1 MB and more e.g. mp3 files mpeg files jpg files etc. .

In order to make cloud storage available to systems such as operating systems file systems applications hypervisors . . . which were developed mainly to interface with block devices there is a need for a device driver that can manage the transfer between a block or clusters and cloud storage container objects in an efficient way.

As such it is an object of the current invention to provide intelligent caching technology such that a sequence of block or cluster writes is grouped and stored in a cloud storage container object with a size that is well suited for a cloud storage system e.g. 4 MB .

According to a first aspect of the invention there is provided a device driver comprising a block device interface able to handle data in the form of small fixed length data blocks and an object reader writer able to transfer data in the form of larger data objects from and or to a storage system said device driver comprising 

aggregation means for aggregating said data blocks into one or more container objects suited for storage in said object store and

log means for maintaining in at least one log file for each data block an identification of a container object wherein said data block is stored and an identification of the location of said data block in said container object.

As such the device driver according to the invention allows the application and optionally the file system to interact with the cloud storage system using the same facilities as it has available for known physical block devices.

In this way the device driver according to this embodiment of the invention can be implemented with a few simple and efficient components.

According to a further embodiment of the invention said means for closing said container object are adapted to close said container object whenever 

means for updating said transaction log file each time a data block is appended to a container object 

According to still a further embodiment of the invention said means for closing said transaction log file are adapted to close said transaction log file whenever 

According to a preferred embodiment the device driver according to the invention further comprises one or more of the following 

According to still a further embodiment of the invention said means for maintaining a metadata cache comprise 

According to a preferred embodiment of the invention said container object cache comprises plural tiers of cache memories a first tier with low capacity and fast access speed and one or more successive tiers having higher capacity and lower access speeds.

According to a further embodiment of the invention the device driver comprises a plurality of block devices interfaces said device driver comprising 

a single container object cache eventually comprising plural tiers of cache memories for handling data blocks received from said plural block device interfaces 

According to a preferred embodiment of the invention the device driver further comprises means for generating a snapshot comprising 

means for writing a meta data file in said object store referencing said transaction log file in relation to said snapshot.

This allows a snapshot to be generated without the overhead of additional data copy operations and without affecting the performance of the block device interface.

According to a preferred embodiment of the invention said device driver further comprises means for generating a clone comprising 

means for reading from said object storage system transaction log files from creation of said block device interface up to a given snapshot and

means for replaying said transaction log files to thereby generate a meta data cache for said clone block device interface.

This allows a clone to be generated without the overhead of additional data copy operations and without affecting the performance of the block device interface.

According to a preferred embodiment of the invention said device driver further comprises means for scrubbing to remove obsolete data stored in between two successive snapshot events from said object storage system.

According to a preferred embodiment of the invention the device driver further comprises means for failover caching a data block before appending said data block to said container object and before updating said transaction log file.

This allows for a robust device driver that is able to recover without errors even when severe failures occur.

According to a second aspect of the invention there is provided an application programming interface API with functionality of the device driver according to the first aspect of the invention.

According to a third aspect of the invention there is provided a software application module with functionality of the device driver according to the first aspect of the invention.

According to a fourth aspect of the invention there is provided a method for providing a block device interface able to handle data in the form of small fixed length data blocks and an object reader writer for transferring data to an object storage system able to store data in the form of larger data objects the method operating in accordance with the device driver the application programming interface or software application module according to any of the previous aspects of the invention.

Device driver according to the invention provides a block device interface that allows for the block based read and write operations with for example a 512 byte block size. Typically a sequence of 8 or a multitude of 8 blocks is accessed in sequence. Such a sequence is also called a cluster. Every cluster read or write operation is identified by an LBA Logical Block Address of the first block in the cluster.

Various interfaces to storage devices are also well known in the art. For example Small Computer System Interface SCSI is a well known family of interfaces for connecting and transferring data between a file system and a block device. There are also a number of standards for transferring data between a file system and storage area networks SAN . For example Fibre Channel is a networking technology that is primarily used to implement SANs. Fibre Channel SANs can be accessed through SCSI interfaces via Fibre Channel Protocol FCP which effectively bridges Fibre Channel to higher level protocols within SCSI. Internet Small Computer System Interface iSCSI which allows the use of the SCSI protocol over IP networks is an alternative to FCP and has been used to implement lower cost SANs using Ethernet instead of Fibre Channel as the physical connection. Interfaces for both FCP and iSCSI are available for many different operating systems and both protocols are widely used. The iSCSI standard is described in Java iSCSI Initiator by Volker Wildi and Internet Engineering Task Force RFC 3720 both of which are hereby incorporated by reference

In its basic form the device driver according to the current invention groups a sequence of cluster writes associated with a predetermined LBA and transferred from the file system in a larger object called a storage container object SCO . The metadata that references which cluster was written in which SCO is written in an object called a transaction log TLOG . As SCO s and TLOG s fill up they are being transferred to the object store interface . The device driver also offers the functionality to the file system to retrieve the stored data from the SCO s and TLOG s by means of a simple LBA based lookup.

1. The cluster is transferred from the block device interface to a volume interface that writes the cluster into a Storage Container Object SCO . The SCO is an object that is a coalescence of clusters that have been written to the block device interface arranged in order of time of writing. The first cluster will create the SCO the second cluster written will be appended to the SCO etc. . . . Once the SCO exceeds a defined size the SCO is closed and transferred to an object reader writer . Optionally the SCO could also be closed after a predetermined time period a snapshot or a sync command. This object reader writer will then transfer the SCO in a suitable way in this embodiment through object store interface to one or more object storage systems which will finally store the SCO on a physical storage device for subsequent retrieval. Such a object store interface is for example known from WO2009 135630 but any other suitable object store interface will do. A new SCO object will be created as soon as a new write operation arrives after a previous SCO was closed. An SCO is identified by an SCO name which could comprise a Universally Unique IDentifier UUID or a Globally Unique IDentifier GUID .

2. The transaction log TLOG is then updated by the volume interface with the LBA x the SCO name and the offset d within that SCO. The offset d is a number that identifies how many bytes from the beginning of the SCO the block or cluster associated with LBA x is written. Once a TLOG exceeds a defined size the TLOG is closed by the volume interface and transferred to the object store interface by the object reader writer . Optionally the TLOG could also be closed after a predetermined time period a snapshot or a sync command. Subsequently the TLOG is transferred to the object store interface that writes it to the object storage systems . A new TLOG object will be created as soon as a new write operation arrives. A TLOG is identified by a TLOG name which could comprise a Universally Unique IDentifier UUID or a Globally Unique IDentifier GUID .

When a block or cluster read operation is issued through the block device interface for reading a cluster at a predetermined LBA y comprising data sized 4 Kbytes following actions will happen 

1. TLOG s will be read from the object storage system by the object reader writer through the object store interface in reverse order this means most recent first. Inside the read TLOG s the logged operations are read in reverse order until the most recent TLOG entry associated with a block write operation on the requested LBA y is found. For that LBA y TLOG entry the associated SCO name z of the SCO where the actual block data associated with LBA y is residing and what it s offset d is inside that SCO is retrieved

3. The SCO with SCO name z is opened and a read operation will be executed by the object reader writer starting at offset d and will retrieve the 4 Kb cluster data and provide it to the volume interface which will transfer it to the block device interface which will then transfer it to the file system for the application which is interacting in this way with the block device interface .

This first embodiment provides a basic architecture that provides a solution to aggregate small block writes in larger SCO and TLOG objects. These objects are better suited for storage in the object storage system .

Whenever an SCO is filled up and closed by the block device interface the SCO is queued for writing to the object storage system by the object reader writer . The object reader writer will process the write jobs as they appear in this queue. Only one object reader writer is working for a given block device interface also known as a volume at any time. Multiple object writers can process multiple volumes in parallel.

Whenever a TLOG is filled up and or closed by the block device interface it is queued for writing to the object storage system by the object reader writer . The TLOG will be queued after all SCO s that the TLOG is referring to. Like this any TLOG in the object storage system always refers to SCO s which are already present in the object storage system .

A sync to object storage system command is given. This is triggered by an external application e.g. a database that wishes to reset to a particular situation or state or once every x seconds.

The object storage system is considered to be always available and redundant such that every SCO and TLOG written to that object storage system can always be retrieved.

One of the drawbacks of this basic architecture is that every object needs to be read back from the object store to perform a read operation. This is potentially too slow.

Therefor as shown in and in more detail in the embodiment according to a local object cache is added. The local object cache comprises a data cache for locally storing multiple SCOs and a data cache manager for deciding which SCO s need to be stored in the data cache . The data cache manager uses a caching algorithm that attempts to predict which clusters will be read next. The SCO s that contain these clusters are retained in the data cache such that read requests for these clusters can be fulfilled from the SCO s in the data cache without having to read the SCO s back from the object storage system .

Several caching algorithms can be used to decide which SCO s are retained in the cache. Examples are but the implementation is not limited to most recently used MLU and most frequently used MFU .

As the capacity of the data cache is limited SCO s will need to be removed from the data cache to make room for other SCO s that are identified as better candidates to cache by the caching algorithm. Cleaning the cache is also done by a data cache manager .

The data cache manager can be part of the volume interface or optionally it can be implemented as a separate parallel process. The advantage of implementing it as a separate process is that the data cache manager can manage the cache across multiple volumes that are running on the volume interface spreading all the available cache space amongst all available volumes.

The data cache manager if implemented as a separate process uses the reverse process as explained above to decide which blocks can be removed. I.e if the data cache manager implements a most recently used MLU algorithm to identify SCO s to be retained in the data cache the data cache manager will use a least recently used LRU algorithm to decide which SCO s to remove. Similarly if the data cache manager implements a most frequently used MFU algorithm to identify SCO s to be kept the data cache manager will use a least frequently used LFU algorithm to decide which SCOs to remove.

According to a further embodiment shown in optionally there can be provided a multi tier data cache . The performance of the data cache determines the performance of the block device interface . Performance is measured as input output operations per second IOPS and as throughput in MB s. Higher performance of the data cache will yield higher performance of the exposed block device interface .

Memory and solid state drives typically have higher IOPS specifications than mechanical disk drives. Mechanical disk drives then again have higher IOPS specifications than the object storage system . On the other hand the higher IOPS devices typically have lower capacity.

The data cache manager will manage the placement and retention of the SCO s in the data cache based on the implemented caching algorithm. The candidates with highest cache ranking MFU MRU or other are stored in the Tier 1 data cache . Also the newly created SCO s are stored in Tier 1 data cache by the volume interface .

According to this embodiment of the invention SCO s with lower ranking are moved to the Tier 2 data cache whenever the Tier 1 data cache capacity fills over 80 of the available capacity. It is clear that alternative levels of available capacity could equally be determined such as for example 90 . Only SCO s that were closed and written to the object storage system can be moved from the Tier 1 data cache to the Tier 2 data cache . According to still further embodiments any suitable amount of multiple Tiers of data cache can be provided. Then similarly if the Tier 2 capacity fills over 80 of the available capacity SCO s with lower ranking can be moved to lower tiers of data cache. If the lowest tier of the data cache fills up over 80 of the available capacity SCO s can be removed by the data cache manager . This will not lead to data loss as the SCO s were written to the object storage system when they were created in the Tier 1 data cache . If data from these removed SCO s is needed to serve read requests from the block device interface they are first read from the object storage system into the Tier 1 data cache of the local object cache .

According to a further embodiment as shown in there can optionally be provided a transaction log cache . This means that whenever read operation is requested for a cluster at LBA x through the block device interface the volume interface needs to identify in which SCO and at with offset d that cluster was stored. In the embodiment according to it was described how this SCO and offset can be found by scanning through the TLOG objects in reverse order. To make the scanning through these TLOG s faster TLOG objects can also be cached locally in the local object cache . This is called the transaction log cache . The most frequently created TLOG s are retained in the transaction log cache such that the most recently written entries can be found in the local object cache and thus faster.

To respond to these read requests faster an optional meta data cache can be implemented locally. The meta data cache is a sparse memory map that comprises entries that map every written cluster LBA address to its corresponding SCO and offset d. By maintaining the meta data cache the meta data of every cluster can be retrieved locally and quickly without having to read data from the object storage system .

The role of the meta data cache is to map a cluster at a predetermined LBA to an associated SCO and an offset d within that SCO. The Meta data cache is thus related to the current state of the block device interface . It does not provide historical information. The meta data cache can be implemented as a high performance lookup cache. The meta data cache is not persisted to the object storage system as it can always be reconstructed from the TLOG s if this would be needed after a crash or reboot of a volume.

The role of the TLOG s is to maintain a chronological log of all write operations in a volume. It provides a mechanism to roll back a volume to a previous state restart or clone a volume as it was any time in the past or remove overwritten cluster data. Since a block device interface only has write update operations and no delete operations one needs a mechanism to be able to identify what blocks have been overwritten. The transaction log comprises a list of entries comprising an LBA an associated SCO and offset d written in a chronological fashion. One can identify what block is overwritten by another block by parsing this transaction log.

For the embodiment shown in a write operation issued through the block device interface is performed as described below. When a cluster write operation is issued through the block device interface for writing a cluster at a predetermined LBA x comprising data sized 4 Kbytes following actions will happen 

1. The cluser is written into a Storage Container Object SCO in the Tier 1 data cache . The SCO is an object that is a coalescence of clusters that have been written to the block device interface arranged in order of time of writing. The first cluster will create the SCO the second cluster written will be appended to the SCO etc. Once an SCO exceeds a defined size the SCO is closed for writing and a new SCO object will be created as soon as a new write operation arrives. An SCO is identified by an SCO name.

2. The transaction log is updated with an entry comprising the LBA x the associated SCO name and the offset d within that SCO. The offset d is a number that identifies how many bytes from the beginning of the SCO the cluster associated with LBA x is written.

3. The meta data cache is updated with the LBA x the associated SCO name and the offset d within that SCO.

For the embodiment shown in a read operation issued through the block device interface is performed as described below. When a cluster read operation is issued through the block device interface for reading a cluster at a predetermined LBA y comprising data sized 4 Kbytes following actions will happen 

1. A lookup operation will happen inside the meta data cache to identify the SCO name z of the SCO where the actual cluster associated with LBA y is residing and what its offset d is inside that SCO.

2. The volume driver identifies whether the SCO z resides in the data cache . If the SCO is not in the data cache it is first loaded by the object reader writer from the object storage system into the data cache .

3. The SCO with SCO name z is opened and a read operation will be executed starting at offset d and will retrieve the 4 Kb cluster data and provide it to the application interacting with the block device interface .

According to still a further embodiment it is optionally possible to run multiple block device interfaces . Multiple block device interfaces can run in parallel on the volume interface . In that case a meta data cache and a transaction log is created per block device interface .

The data cache is managed across all block device interfaces . Thus SCO s that are most frequently accessed across all block device interfaces will remain in the Tier 1 data cache while SCO s that are accessed infrequently across all block device interfaces are moved to Tier 2 data cache and eventually removed from the data cache . By managing the data cache across volumes the volume driver avoids reserving cache space for idle volumes.

The embodiments according to the invention allow for advantageous snapshot operations. A snapshot is a point in time copy of a block device. One will make a snapshot to freeze the state of that block device. A snapshot can be a known state to roll back a block device to if it would get corrupted. A snapshot can also serve as a restore point to access data which is already removed in the current block device. Finally a snapshot can be used to create a clone of the block device as it was at the point of the snapshot.

Copy on write snapshot implementations copy away a block to another location when it is overwritten after a snapshot. The disadvantage of this method is that block writes are slowed down by the copy operation for underlying snapshots. The number of snapshots on a given volume will be limited because of that.

Split mirror snapshot implementations copy all block writes to 2 block devices up till the point a snapshot is taken. At that point the mirror is broken and the state of one of these volumes at the time of the snapshot is maintained. This implementation requires all data to be stored for each snapshot which requires a multitude of capacity to support snapshots. The mirroring operation also slows down the write performance of the system.

The current invention allows for a very efficient method for making snapshot. Making a snapshot on the block device interface has no impact on the performance of the block device interface . Making a snapshot does not involve any data copy operations which limits the amount of disk capacity required to retain snapshots and it avoids disk IO operations and bandwidth consumption that are associated with copy operations.

When a user requests a snapshot on the volume interface for a given block device interface the following actions are triggered 

1. The SCO which is currently being filled for the block device interface is closed and a new SCO is created to store subsequent block writes. The closed SCO is queued for writing to the object storage system .

2. The TLOG that is currently being filled is closed and queued for writing to the object storage system .

3. A meta data file is written to the object storage system to reference this TLOG as the endpoint for this snapshot.

As one can see these operations are no different than the operations during a normal write operation. Therefore snapshots do not cause a performance drop on the block device interface . And snapshots do not initiate data copy operations.

The embodiments according to the invention also allow for an advantageous implementation of cloning operations. Clones are fully functional read write block devices that are an identical copy of a snapshot state of a volume.

The current invention offers a unique method to create a fully functional read write clone of a block device without copying any data. When a snapshot of a block device interface is cloned the following actions are performed 

3. The TLOGs associated with the parent volume starting from the creation of the parent volume up to the TLOG of the snapshot where the clone is created from are read from the object storage system .

Now the clone block device interface is ready for use. As its meta data cache refers to the same SCOs as the parent volume no data was copied at this point. As soon as clusters are being written to the clone block device interface these are added to SCOs which are created specifically for the cloned block device interface while the meta data is added to a TLOG which is specific to this clone block device interface .

According to an embodiment of the invention as shown in additionally scrubbing can be provided. The described device driver is a write optimized implementation where every block is written to the object storage system . As the object storage system is not infinite in size it will be necessary to remove obsolete data from the object storage system . This process is called scrubbing.

The block device interface receives a write command for a cluster at LBA x its data is appended to SCO y.

Later in time the block device interface receives a new write command to write a cluster at LBA x its data is appended to the then current SCO z.

Now the cluster associated with LBA x in SCO y is not needed anymore and can be deleted. The process of deleting this obsolete data is called scrubbing.

A write command is received by the block device interface also known as the volume to write a cluster at LBA x its cluster data is appended to SCO y.

Later in time a new write command is received by the block device interface to write a cluster at LBA x its data is appended to the then current SCO z.

Now the cluster in SCO y needs to be retained as it is required to represent the volume state at the point of the snapshot. Therefore scrubbing cannot cross snapshot boundaries.

Scrubbing can be integrated in the volume interface . Or optionally it can be implemented as an efficient method for scrubbing data in an object storage system with minimal impact on the volume interface operations. In an efficient implementation the scrubbing agent runs in parallel to the volume interface . It can potentially run on a separate machine to avoid impacting the performance of the volume interface .

The scrubbing agent operates between the time of the creation of the block device interface also known as a volume and the first snapshot or between two subsequent snapshot points. Multiple scrubbing agents can operate in parallel as long as they each operate between different snapshot points.

A scrubbing agent that is started to run between snapshot x and snapshot x 1 or between snapshot and the creation time of the volume will perform the following actions 

Retrieve all TLOGs from the object storage system that were created and stored between the predetermined snapshot points.

After this meta data scrub TLOG y only contains relevant entries for snapshot x. All entries that were overwritten have been removed from the TLOG. The next phase of the scrub is a data scrub on the referenced SCO s. This could be a basic scrub or optionally more optimized scrubbing methods 

Optimized scrub that collapses SCO s of which over 50 of the cluster entries have been obsoleted. Following actions are taken 

Optimized scrub with access frequency optimization. The volume interface is write optimized. Clusters are written in sequence in an SCO object. It might well be that the read pattern for these clusters is different. E.g. one could analyze read patterns and find that a sequence for reading clusters is fundamentally different than the initial write sequence. If this is the case the read pattern can be considered during a scrub cycle. As clusters are copied to a new SCO z by the scrubbing agent the clusters will be added to the SCO z in the expected read order. This will speed up future reads of these clusters for this volume.

According to still a further embodiment of the invention as shown in there can optionally be provided a failover cache .

The cache in the volume interface that stores the SCO and TLOG that is currently being filled until it reaches a predetermined size could potentially be a single point of failure. Data that is not written in the object storage system could be lost when the system where the volume interface is running fails unexpectedly. The current invention provides a method to protect against such failures. Associated with a volume interface a failover cache is installed on a remote system. When a cluster is written to a given LBA x via the block device interface to the volume interface the following actions are taken 

The failover cache stores the cluster data with the LBA address in an entry in a sequential data log.

The volume interface stores the cluster locally in its cache in an SCO and TLOG that is being filled as described before.

Purging the failover cache can be performed when a TLOG is written to the object storage system including all the associated SCOs as then that data is stored safely. At that point a message is sent to the failover cache to delete all entries which are part of these SCOs. Thus at any time only the data referenced by the TLOG currently being filled by the volume interface of a block device interface is retained in the failover cache .

The failover cache can be used for restarting a volume after a crash. The volume interface will then perform following actions when restarting a volume after a crash. We assume the cache to be empty in this case 

the TLOGs of the parent volume starting from the creation of the volume up to the last TLOG that was saved are read from the object storage system .

The volume interface then reads all entries in the failover cache as if they would originate from the block device interface .

Once all entries from the failover cache have been replayed the clone block device interface can be used for I O operations.

According to an alternative embodiment of the invention the functionality of the device driver as described above can be implemented as an application programming interface API or a software application module that can interact directly with the application .

Although the present invention has been illustrated by reference to specific embodiments it will be apparent to those skilled in the art that the invention is not limited to the details of the foregoing illustrative embodiments and that the present invention may be embodied with various changes and modifications without departing from the scope thereof. The present embodiments are therefore to be considered in all respects as illustrative and not restrictive the scope of the invention being indicated by the appended claims rather than by the foregoing description and all changes which come within the meaning and range of equivalency of the claims are therefore intended to be embraced therein. In other words it is contemplated to cover any and all modifications variations or equivalents that fall within the scope of the basic underlying principles and whose essential attributes are claimed in this patent application. It will furthermore be understood by the reader of this patent application that the words comprising or comprise do not exclude other elements or steps that the words a or an do not exclude a plurality and that a single element such as a computer system a processor or another integrated unit may fulfil the functions of several means recited in the claims. Any reference signs in the claims shall not be construed as limiting the respective claims concerned. The terms first second third a b c and the like when used in the description or in the claims are introduced to distinguish between similar elements or steps and are not necessarily describing a sequential or chronological order. Similarly the terms top bottom over under and the like are introduced for descriptive purposes and not necessarily to denote relative positions. It is to be understood that the terms so used are interchangeable under appropriate circumstances and embodiments of the invention are capable of operating according to the present invention in other sequences or in orientations different from the one s described or illustrated above.

