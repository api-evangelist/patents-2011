---

title: Data staging for results of analytics
abstract: Data staging for results of analytics according to an example method includes maintaining current results from the analytics in a first data structure, the first data structure having a label identifying first data structure as a target for queries. The method also includes maintaining prior results from the analytics in at least one other data structure. The method also includes changing the label of the first data structure after a predetermined time. The method also includes assigning the label to one of the other data structures, wherein the label identifies the one of the other data structures as the target for queries.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09251215&OS=09251215&RS=09251215
owner: Hewlett Packard Enterprise Development LP
number: 09251215
owner_city: Houston
owner_country: US
publication_date: 20110114
---
Mobile devices including for example mobile phones so called smart phones global positioning system GPS devices and even laptop netbook computers provide diverse remote data capabilities. Many mobile applications are based on so called cloud services such as location services messaging services and so forth. Currently most cloud services are based on statically prepared information and do not offer real time analytics of dynamically captured events. For example a weather report or traffic report may be updated periodically to a local news website.

Users of mobile devices however are coming to expect more frequent updates of events often in real time. For example users may not just want a statically prepared traffic report e.g. delays on the interstate due to an earlier accident . In addition more real time information is becoming readily available e.g. concerning the location speed and accident involvement of many individual cars . Of course to most users the interesting and more useful information is not the individual data such as each car s position and speed but information that has been analyzed and summarized for the user in real time e.g. the average or moving average speed of a lane of traffic on the interstate . This information can be derived from the individual data using various analytics.

The information is typically analyzed using a continuously running query. The continuous query executes cycle by cycle to process the data stream on a chunk by chunk basis. The query commits results to the data structure on a cycle by cycle basis to make the chunk wise results visible to users. But in the case that the information is derived from a large or infinite number of events the information is also infinite. Accordingly the data structure storing the information continues to grow and can quickly become too big to handle by most mobile devices.

Mobile devices such as those running WebOS and HTML 5 may download data in batch to ease the bandwidth limitations. However conventional batching involves data copying and moving which still incurs performance overhead and in the case of very large data structures may still cause service interruptions.

Archiving has also been used for data warehouse management applications. In these archiving techniques the latest data is maintained in the table and older data is archived from time to time. But archiving the older data also involves moving and copying the data from the table. For example the data may be moved from a first table holding the latest data to another table so that the first table only holds the new data. While this approach has been used for handling slowly updated data in data warehousing applications archiving is not efficient for supporting real time analytics.

The overhead associated with data move and or copy operations in conventional systems can be debilitating. In addition the service is often interrupted during the archiving process because the table being queried is also the same table that is being archived. Systems and methods are disclosed herein of data staging for results of analytics such as continuous stream analytics CSA . The results may be staged efficiently through metadata manipulation without actually moving and or copying data and without shutting down the continued query that generates the results on a continuous or substantially continuous basis.

In an embodiment table ring based data staging utilizes small size data structures that help to ensure low latency data retrieval. Maintaining the results of analytics in small sized tables makes the results more easily accessible by mobile applications operating in reduced bandwidth environments such as those running on WebOS with HTML 5 caching capability.

In addition the results are staged by switching labels of the data structures. This approach helps to ensure the stability of server interfaces and client interfaces e.g. application programming interfaces or APIs . That is the target label or metatag specified by database queries remains the same regardless of which table the label has been assigned to.

The networked computer system may include one or more communication networks such as a local area network LAN and or wide area network WAN . In one example the networks include the Internet or other mobile communications network e.g. a 3G or 4G mobile device network .

A host may be implemented with or as part of the cloud service in the networked computer system . As an example host may include one or more computing systems such as a personal computer or server computer and may include at least some degree of processing capability and computer readable storage. The host is also connected to or able to establish a connection with the client . By way of example the host may be a server computer or a plurality of server computers.

The host may be provided on the network via a communication connection such as via an Internet service provider ISP . In this regard host may be accessed by the client directly via the network or via an agent such as a network site. In an embodiment the agent may include a web portal on a third party venue e.g. a commercial Internet site which facilitates a connection for one or more clients with host . In another embodiment portal icons may be provided e.g. on third party venues pre installed on a computer or mobile device etc. to facilitate a communications connection between the client and the host .

Before continuing it is noted that the systems and methods described herein may be implemented with any of a wide variety of computing devices such as but not limited to stand alone personal desktop computers workstations personal digital assistants PDAs and appliances e.g. devices dedicated to providing a service to name only a few examples. Each of the computing devices may include memory storage and a degree of data processing capability at least sufficient to manage a communications connection either directly with one another or indirectly e.g. via a network .

The host may be implemented to receive data from at least one source . The source may be part of the cloud service . Or the source may be distributed in the network . For example the sources may gather data from one or more sensors e.g. traffic monitoring locations along a road or sensors provided with the GPS systems in vehicles . The source may also include user generated data. An appropriate filter may be applied e.g. to discard bad data e.g. intentional misinformation provided by users . There is no limit to the type or amount of data. The data may be unprocessed or raw or the data may undergo at least some level of processing prior to delivery to the host .

The host may execute analytics for the data to generate results based on the data. For example if the host receives traffic data including number of cars on the road the host may process the traffic data to generate a traffic report. In an example the analytics are executed continuously or substantially continuously by the host to generate results in real time or substantially in real time .

The host may maintain the results of the analytics in at least one data structure e.g. a table in computer readable media . The data structure may be accessed by the clients e.g. executing a mobile application which retrieves the results of the analytics from the host and outputs the results for the user at the client e.g. on the one mobile phone .

It is noted that the host is not limited in function. The host may also provide other services to other computing or data processing systems or devices. For example host may also provide transaction processing services email services etc.

The host may execute database program code . In an embodiment the database program code may include an analytics engine and a query engine . In an example the analytics engine may be an SQL based stream analytics engine and the query engine may be an SQL query engine. The analytics engine may be integrated into the query engine .

The query engine defines a unified query model over both static relations and dynamic streaming data. Techniques are implemented which extend the query engine to support a unified model. A cut and rewind query execution mechanism may be implemented to enable an SQL query to be executed on a cycle by cycle basis for processing a data stream on a chunk by chunk basis but without shutting the query instance down between chunks. Such an approach enables maintaining the application context across continuous execution cycles e.g. for sliding window oriented operations. The cycle based transaction model characterized by cycle based isolation and visibility may be used to deliver results of the analytics to the client while the query for generating these results is continuously or substantially continuously running.

The analytics engine executes the analytics on data. In an embodiment the results are derived by a continuously running query rather than multiple on and off queries. The results are derived from many e.g. infinite events and therefore are themselves infinite. Therefore the continuous query runs cycle by cycle for processing the data stream on a chunk by chunk basis and the query commits cycle by cycle to make chunk wise results visible to users.

Because the results are infinite the results may be staged to avoid the data structure in computer readable media that is holding these results from becoming too large. For example size of the data structure is of particular concern for mobile devices such as those running WebOS and HTML 5. Staging may also enable scaling up the analytics service to handle even more data.

In order to support fast access to the results a table ring mechanism may be implemented by the query engine . This allows the results of substantially infinite real time analytics to be maintained in a list of small sized data structures e.g. tables . The data structures may be labeled based on time sequence and staged through switching labels without having to copy and or move data and without shutting down or incurring performance penalties for the continued query instance which is continuously generating those results.

In an embodiment the results may be formatted as time series data. The time series data may be stored in any suitable data structures such as read sharable tables T. The read sharable tables T are incrementally visible to the clients as the results are staged in a step by step manner along with their generation.

Analytics may be applied on a continuous basis such as in per minute cycles or some other time reference . Accordingly time series data may be used for expressing the results of the analytics in a continuous manner. For purposes of illustration the traffic status for a particular road may be updated every minute for every road for every direction and so forth.

The results from the analytics may be maintained in a data structure for every hour generated in 60 per minute cycles such as a table T shown in . The data is maintained for 8 hours on line by the cloud service and can be accessed by the clients without having to access the archive.

In the example shown in nine tables T T are maintained e.g. on a fast disk or flash memory buffer pool etc. . The nine tables T T are implemented such that at a current time e.g. the current hour h in this example table T stores the current results of the analytics and is thus the target data structure. Table T stores the results of the prior hour h 1 and so forth. Table T stores the oldest results in this example and is thus archived asynchronously during the current hour h .

The metatag or label of each table T may represent a time boundary e.g. the hour in this example . For example the metatag or label for table T is h the label for table T is h 1 and so forth. For data staging the label is changed so that the target label h always points to the data structure having the current results without moving and or copying the content of the table to another table or file. This approach avoids read and or write overhead and archiving overhead.

When the hour changes as illustrated by arrow in so that the current hour is now h 1 the table T has already finished being archived. Table T can be moved up and used to store the current results at this new time h 1 . Table T is now assigned the label corresponding to the last hour h 1 and so forth in a round robin or table ring approach.

It is noted however that while the label changes e.g. table T now has the target label h and table T is now labeled h 1 the tables themselves have not been changed. That is table T is still table T although the contents have been archived and table T is still table T and includes all of the contents that table T has always had.

In an embodiment the metatags or labels in this example the timestamps h h 1 . . . h 8 may be associated with the corresponding table. For example an index e.g. a data dictionary or other suitable data structure may be used for this association. Accordingly if the client is seeking current data the query engine can access the appropriate table i.e. the target table . At the current time h the appropriate table or target table is table T. But when the current time changes to h 1 the appropriate table or target table is table T and so forth.

It is noted that the data staging as just described is not limited to the example shown in . Any suitable number of tables type of data structures time increments and or archiving schedule may be implemented.

In any event the data staging provides a stable interface for both the client side and server side queries. To illustrate the table holding a traffic status in the current hour may be named current road condition. This name in either the client side query for retrieving the results or the server side query for receiving the results remains the same at all times. That is table T is always table T and table T is always table T and so forth for all of the other tables . But the tables are renamed or otherwise associated with the table having the latest results e.g. the table labeled h or in this example the table labeled current road condition be that table T T . . . or T.

Such meta data manipulation has been described herein as changing labels. For example the cloud service may make available to the clients a table named current road condition. But the cloud service actually stores the current results in the tables internally identified by T T . . . T for the traffic status of the current hour h and h 1 . . . h 7 h8 . When a client connects to the cloud service and requests the current hour traffic status e.g. using an SQL API for access to the table named current road condition the cloud service internally converts the table name from current road condition to Table T if the analytics results of the current hour are stored in T.

However other embodiments are also contemplated and are not limited to changing labels. In another example a system utility may change other metadata for the table having the current results. Also for example the name of the table itself may be changed or the name of the table may be re associated with different tables e.g. using the index .

The server side may also be enabled to support continuous stream analytics by switching the name of the query destination while the query is still running. For purposes of illustration a cycle based continuous query that runs in the per minute 60 seconds cycle and persists the result in table T during hour 1 table T during hour 2 and so forth in the round robin manner described above.

In an embodiment the query may be specified as INSERT INTO T SELECT. However the into relation in this expression is substituted by the actual relations T T and so forth from one hour to the next hour. illustrates example operations including steps which may be used by the query engine for continuous staging e.g. by switching into relations . Informing the query engine of the time boundary for switching the into relation name can be accomplished for example by extending the SQL by extending the query or using SSF registration.

For purposes of illustration the SSF registration is utilized in the example of . In this example the hourly boundary for table switch is turned to 60 per minute cycles which is made recognizable by the query engine at run time.

The index e.g. data dictionary or specific system table maintains the metadata such as name ID etc of the set of actual into relations as well as the order of them in the round robin usage. A cycle based INSERT INTO SELECT query commits each cycle through the following example call sequence 

Between the complete transaction call and the reopen into relation call the number of execution cycles is checked and if the number reaches 60 in the above example the switching of into relations is executed.

For switching into relations the data dictionary or system table is used for look up and the next relation ID is obtained before the first cycle the initial relation ID is obtained and is passed to the reopen into relation . Thereafter another into relation serves as the query destination.

Staging real time analytics results using this approach is particularly desirable for supporting mobile applications due to the latency in connecting a mobile device to a cloud server. That is it is often more efficient to download a batch of information from the server for analytics purposes. HTML 5 enabled WebOS programs provide such data buffering capability e.g. as the localStorage function . Using the server side data staging approach the tables with the latest results remain relatively small and thus downloading these tables is efficient and readily managed.

In the example shown in a query plan is created at and then an into relation is opened at . At the query plan is executed. The query plan is rewound at . The into relation is closed at and . At the cycle number is checked and an index lookup is consulted at . The transaction starts at and the into relation is re opened at .

Before continuing it should be noted that the embodiments described above are provided for purposes of illustration and are not intended to be limiting. Other devices and or device configurations may be utilized to carry out the operations described herein.

In operation current results from the analytics are maintained in a first data structure. The first data structure has a label identifying first data structure as a target for queries. The label may represent a time boundary. In an example the current results for the hour h may be maintained in a table T with a label h . In operation prior results from the analytics are maintained in at least one other data structure. For example the results for the prior hour h 1 may be maintained in a table T with a label h 1 the results for 2 hours ago h 2 may be maintained in a table T with a label h 2 and so forth.

In operation the label of the first data structure may be changed after a predetermined time. For example at the next hour h 1 the first data structure T may be labeled h 1 . Each of the other tables may be updated as well e.g. T may be labeled h 2 . In operation the label may be assigned to one of the other data structures. The label now identifies one of the other data structures e.g. the oldest table T as the target for queries. For example the oldest table T may be relabeled as h .

The operations shown and described herein are provided to illustrate various embodiments for data staging for analytics analytics . It is noted that the operations are not limited to the ordering shown. Still other operations may also be implemented.

For purposes of illustration further operations may include archiving results for at least one of the tables e.g. the oldest table T before changing the label of the data structure e.g. from h 8 to h . Archiving the other data structures may be according to a round robin approach. Further operations may also include changing the other labels for each of the other data structures by incrementing based on time.

Further operations may also include maintaining an index with each data structure and corresponding labels for the first data structure.

Further operations may also include providing a stable interface for clients regardless of which of the data structures is the target for queries.

Further operations may also include changing labels while a query is running. For example changing labels while a query is running may be implemented by switching into relations.

It is noted that the exemplary embodiments shown and described are provided for purposes of illustration and are not intended to be limiting. Still other embodiments are also contemplated.

