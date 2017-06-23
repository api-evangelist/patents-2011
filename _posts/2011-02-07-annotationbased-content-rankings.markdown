---

title: Annotation-based content rankings
abstract: Techniques for ranking electronic content items include analyzing annotations made in the content items. Specifically, the number of annotations and the number of people making the annotations can be analyzed to produce a popularity ranking of different content items.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08954447&OS=08954447&RS=08954447
owner: Amazon Technologies, Inc.
number: 08954447
owner_city: Seattle
owner_country: US
publication_date: 20110207
---
Books are increasingly purchased electronically through online sources and consumed on electronic devices. When reading a book on an electronic device a user s experience can be enhanced by features such as annotations. Annotations may include highlighting underlining commenting editing and so forth and may be enabled by electronic book reader hardware and software.

In some environments users may have their annotations collected and reported to a central web service such as the service from which the users have purchased their electronic books. This enables the annotations to be archived on behalf of the users and for the users to transfer their annotations to different reader devices.

Users may also in some environments share their annotations with other users. In some situations the central web service may aggregate annotations from users and may share the aggregated annotations with other users so that people can see what others have found interesting or noteworthy in an electronic book.

For example an individual user may choose to share their personal annotations with one or more friends. Similarly users may subscribe to the annotations or notes created by another person. In addition a service may analyze collected annotations from different people identify the most popular annotations and distribute those annotations to users who choose to see them.

This disclosure describes systems and techniques in which electronic book annotations can be analyzed to determine relative popularity of electronic books and other content items. A ranking for a particular electronic book is calculated based on the number of users who have made annotations in the book and the number of annotations made by each user. In one embodiment the ranking is calculated as the product of two functions 

In the embodiment described herein the first function is a logarithmic function and the second function is an exponential function. The second function may be based on the geometric mean of the number of annotations made per user.

The contributions of annotations to the popularity rankings are made to decay over time so that more recently received annotations are emphasized relative to less recently received annotations. In the described embodiment the contributions of individual annotations are subject to an exponential decaying function that increasingly deemphasizes annotations as a function of the time since they were made.

Each electronic reader has a display upon which electronic content such as electronic books eBooks may be rendered. The terms content content item and eBook refer to essentially any form of textual data that may be consumed on a device such as digital books audio books electronic magazines papers journals periodicals documents instructional materials course content music movies and so on.

The electronic readers may be handheld devices or other small light weight portable devices upon which eBooks and other content can be rendered and conveniently viewed in a manner similar to viewing a paper book. Examples of other handheld electronic readers include flat form factor devices such as tablets pads smartphones personal digital assistants PDAs etc.

In some embodiments the electronic readers may comprise dedicated purpose eBook reader devices having flat panel displays and other characteristics that mimic the look feel and experience offered by paper based books. For example such eBook reader devices may have high contrast black and white or color flat panel displays that appear similar to a printed page and that persist without frequent refreshing. Such displays may consume very negligible amounts of power so that the eBook reader devices may be used for long periods without recharging or replacing batteries. In some instances these readers may employ electrophoretic displays.

In the example of the electronic readers have networking capabilities. For example the electronic readers may have wireless communication interfaces that allow communication though a network . The wireless communications interfaces may utilize WiFi cellular or other wireless data and networking technologies.

The network may be any type of communication network including a local area network a wide area network the Internet a wireless network a wide area network WWAN a cable television network a telephone network a cellular communications network combinations of the foregoing etc. Services sometimes referred to as cloud based services may be provided from the network . In the network is represented as a cloud and network based services relevant to this discussion are shown as blocks within the cloud.

In the described embodiment the electronic readers include nonvolatile storage capabilities so that electronic content items can be downloaded and stored in their entirety on the electronic readers. Once an eBook has been stored by an electronic reader it can be displayed and read at any time whether or not the electronic reader is connected to a network.

Each electronic reader may be configured with account information corresponding to a particular user . Each user may have multiple electronic readers which may synchronize with each other so that a user may stop reading on a first device and continue reading on a second device at the same location that the user left off in the first device.

In the configuration illustrated by the electronic readers may obtain content items from an online reader service . The reader service may be accessed using the networking capabilities of the electronic readers . The reader service may be accessible through other means as well such as by connection to intermediary devices like personal computers different types of mobile devices and so forth. In the reader service is illustrated as a network based or cloud based service available over a public network such as the Internet. The electronic readers may be configured to allow the users to conveniently browse for content and content items from the reader service and to purchase and download selected content items from the reader service .

Various applications and user interfaces may be used in conjunction with the electronic readers to interact with the reader service such as Internet browser programs that allow a user to interactively engage different online services. In addition the reader service may expose lower level interfaces or APIs application programming interfaces through the network through which devices and programs can access the underlying functionality of the reader service without direct user interaction. For example a user may interactively purchase an eBook or other content item using a personal computer or some device other than the electronic reader device . The electronic reader may periodically communicate with the reader service to perform background synchronization or other housekeeping and may automatically without specific user intervention download any content that has been purchased.

The reader service might be implemented in some embodiments by an online merchant or vendor. Electronic books and other electronic content might be offered for sale by such an online merchant or might be available to members or subscribers for some type of periodic or one time fee. In some circumstances eBooks or other content might be made available without charge.

The reader service may include a client interface through which electronic readers and other client interact with the reader service . The client interface may include a virtual storefront or other type of online interface for interaction with consumers and or devices. The client interface may expose a graphical web based user interface that can be accessed by human users to browse and obtain e.g. purchase rent lease etc. content items such as eBooks. The client interface may also expose programmatic interfaces or APIs that entities and devices can use to obtain digital content items and related services.

In the configuration of the reader service includes or utilizes the services of other functional components illustrated as blocks within the larger dashed block representing reader service . These functional components which will be described in more detail below may be implemented and provided by way of a single installation and or service provider or may exist as independent services that communicate with each other using various means. Note that the illustrated configuration represents a logical organization of services and functionality intended to facilitate description and explanation. However the services and functionality represented in may be implemented in many different ways with various different divisions of responsibilities.

In the described embodiment the reader service provides an annotation service . The reader service may also implement or support additional services.

In addition the reader service provides and or has access to support components and services including storage . The storage may include repositories databases cloud based storage services electronic memory and so forth. The storage may be utilized by the reader service as a content repository to store eBooks and other electronic content for consumption on the reader devices . The storage may also be utilized by other services including the annotation service .

The annotation service can be accessed through the reader service to provide various types of annotation services to users . Depending on the capabilities of the electronic readers users may annotate different items of electronic content. Annotations may include highlights underlining comments ratings tags corrections and other items of information relating to specific locations within the electronic content. The annotations can be stored locally on the electronic readers but may also be transmitted to the annotation service . User annotations might be archived for various reasons such as for backup and sharing. For example a user may at some point delete an annotated eBook from his or her electronic reader and at some later time may re obtain the same eBook from the reader service . Using the annotation service the annotations may have been archived and may be available for restoration when the user re obtains the eBook or reloads the eBook onto his or her electronic reader . As another example the annotation service may implement annotation sharing where annotations from one or more users are shared with one or more other users.

The reader service may implement or utilize an annotation ranking component or module which is configured to rate or rank the popularity of electronic content items based on annotations within those content items. Rankings such as this may be shown to users in conjunction with other information about content items as being relevant to users decisions whether or not to purchase particular content items. For example some users may only be interested in content items having relatively high annotation rankings. Rankings based on annotations may also be used for other purposes such as for determining recommendations for particular users based on their previous histories of purchases ratings and annotations.

The annotation ranking component communicates with the annotation service to obtain data or statistics regarding annotations. In particular the annotation ranking may obtain with respect to any particular content item the number of users who have made annotations within the content item and the number of annotations made by each user. This annotation data may also indicate a time or time period for each annotation or the annotation data may be grouped or summarized by time period. For example the data may be grouped by day week or month. For each time period the annotation data might indicate the number of users who made annotations in the content item during that time period and how many annotations each user made during that time period. Note that instead of indicating the number of annotations made by each user the data may indicate an average or mean of the number of annotations made by each user. In the embodiment described herein the data may indicate the geometric mean of the number of annotations made by each user. Thus for each period such as a day and for each content item the annotation data may indicate the number of users who made annotations and the geometric mean of the number of annotations made by the individual users.

The annotation ranking component uses the annotation data to calculate a ranking for each content item. The ranking for a particular content item can be based at least on a the number of users who have made annotations in the content item and b the geometric mean of annotations made by the users in the content item.

In the embodiment described herein the ranking for any particular time period is a combination of two functions 

In some embodiments such as the one described herein the ranking comprises or is some based at least in part on the product of the first and second functions.

As a specific example the ranking for any particular time period for a given content item may be calculated as follows ln exp annotations user in which

In some embodiments it may be desired to calculate rankings in such a way as to reflect current popularity to emphasize more recent annotations relative to less recent annotations. This can be done by weighting the contributions of annotations based on their age. Specifically the contributions of annotations can be calculated so that they decay over time. Specific examples of how to implement this will be described below.

At the reader service applies a time decay to the annotations. More specifically the value or contribution of each annotation is decayed by a fractional factor that decreases over time. Some embodiments may use an exponentially decaying function so that annotation contributions decay exponentially with time. For example annotations may be multiplied by the following time decay function 

At a positive decreasing slope function is applied to the number of annotators . As will be described below this may be a natural logarithm function.

At the mean of the number of annotations per annotator is calculated. In certain embodiments the mean is calculated as the geometric mean.

At a positive increasing slope function is applied to the mean of the number of annotations per annotator. As will be described below this may be an exponential function.

At the results of the decreasing slope function and the increasing slope function are multiplied. This results in a ranking for each content item. At the reader service may list content items ordered in accordance with their popularity rankings or may utilize the calculated rankings for other purposes.

In practice rankings may be calculated for different time periods and summed to produce a cumulative ranking with older rankings being weighted less than newer rankings. Before being summed older rankings may be multiplied by a decay factor so that their contribution to the cumulative ranking decrease with time. In the described embodiment older rankings are factored by an exponential function of the negative of the age of the rankings. For example the decay factor may be calculated as exp in which

This is an exponentially decaying function which causes the contributions of annotations and rankings to decay exponentially with time. In the described embodiment K may have a value of 1 25 0.04 . The value of K may of course be manipulated to result in more or less rapid decay with age.

Using the techniques described above an individual ranking based on annotations from time periods Tthrough Tmay be calculated as follows 

Rather than calculating rankings over all time a current ranking can be calculated as a function of an old or existing ranking summed with the ranking for the current time period as follows exp ln exp annotations user in which 

At a decaying function is applied to the previous ranking. As described above the decaying function may impose an exponential decay with time. In the described embodiment the decaying function comprises exp K T in which K is a fractional constant and T is the time since the last time period.

At the geometric mean of the annotations per annotator value is calculated and at an exponential function is applied to the result of .

At the result of the logarithmic function at is multiplied with the result of the exponential function at . The resulting product is then summed at with the result of the decaying function . This produces a ranking value .

Note that the techniques described above may be applied to many different types of content items. For purposes of this discussion a content item can be defined as an entire work or book as a collection of works or as a portion of a work. For example a content item may comprise a single chapter of a book and the chapters may be ranked separately based on their annotations to determine relatively popularity of the chapters.

In a very basic configuration the electronic reader includes a processing unit composed of one or more processors and memory . Depending on the configuration of the eBook reader the memory may be a type of computer storage media and may include volatile and nonvolatile memory. Thus the memory may include but is not limited to RAM ROM EEPROM flash memory or other memory technology or any other medium which can be used to store media items or applications and data which can be accessed by the electronic reader .

The memory may be used to store any number of functional components that are executable on the processing unit . In many embodiments these functional components comprise instructions or programs that are executable by the processing unit and that implement operational logic for performing the actions attributed above to the electronic reader . In addition the memory may store various types of data that are referenced by executable programs.

The memory may store an operating system and a content store to store one or more content items. A user interface module may also be provided in the memory and executed on the processing unit to provide for user operation of the electronic reader . The UI module may provide menus and other navigational tools to facilitate selection and rendering of content items. The UI module may further include a browser or other application that facilitates access to sites over a network such as websites or online merchants or other sources of electronic content items or other products.

A communication and synchronization module is stored in the memory and executed on the processing unit to perform management functions in conjunction with one or more services such as the reader service discussed above. In some embodiments the communication and synchronization module communicates with the reader service to receive eBooks and other content items.

The electronic reader may also include an annotation module allowing a user to enter annotations and to communicate annotations with the annotation service in accordance with the techniques described above.

The electronic reader may further include a display upon which electronic books are rendered. In one implementation the display uses electronic paper display technology. In general an electronic paper display is one that has a high resolution 150 dpi or better and is bi stable meaning that it is capable of holding text or other rendered images even when very little or no power is supplied to the display. The electronic paper display technology may also exhibit high contrast substantially equal to that of print on paper. Some exemplary electronic paper displays that may be used with the implementations described herein include bi stable LCDs MEMS cholesteric pigmented electrophoretic and others. One exemplary electronic paper display that may be used is an E Ink brand display. Touch sensitive technology may be overlaid or integrated with the electronic paper display technology to enable user input via contact or proximity to the screen.

The electronic reader may further be equipped with various input output I O components . Such components may include various user interface controls e.g. buttons joystick keyboard etc. audio speaker connection ports and so forth.

A network interface may support both wired and wireless connection to various networks such as cellular networks radio WiFi networks short range networks e.g. Bluetooth IR and so forth. The network interface facilitates receiving electronic books and other content as described herein.

The electronic reader may also include a battery and power control unit . The power control unit operatively controls an amount of power or electrical energy consumed by the electronic reader. Actively controlling the amount of power consumed by the electronic reader may achieve more efficient use of electrical energy stored by the battery.

The electronic reader may have additional features or functionality. For example the electronic reader may also include additional data storage devices removable and or non removable such as for example magnetic disks optical disks or tape. The additional data storage media may include volatile and nonvolatile removable and non removable media implemented in any method or technology for storage of information such as computer readable instructions data structures program modules or other data.

In a very basic configuration an example server may comprise a processing unit composed one of one or more processors and memory . Depending on the configuration of the server the memory may be a type of computer storage media and may include volatile and nonvolatile memory. Thus the memory may include but is not limited to RAM ROM EEPROM flash memory or other memory technology.

The memory may be used to store any number of functional components that are executable by the processing unit . In many embodiments these functional components comprise instructions or programs that are executable by the processing unit and that when executed implement operational logic for performing the actions attributed above to the reader service . In addition the memory may store various types of data that are referenced by executable programs including content items that are supplied to consuming devices such as electronic reader .

Functional components stored in the memory may include an operating system and a database to store content items annotations maps etc. Functional components of the server may also comprise a web service component that interacts with remote devices such as computers and media consumption devices.

The server may of course include many other logical programmatic and physical components generally referenced by numeral of which those described above are merely examples that are related to the discussion herein.

Note that the various techniques described above are assumed in the given examples to be implemented in the general context of computer executable instructions or software such as program modules executed by one or more computers or other devices. Generally program modules include routines programs objects components data structures etc. for performing particular tasks or implement particular abstract data types.

Other architectures may be used to implement the described functionality and are intended to be within the scope of this disclosure. Furthermore although specific distributions of responsibilities are defined above for purposes of discussion the various functions and responsibilities might be distributed and divided in different ways depending on particular circumstances.

Similarly software may be stored and distributed in various ways and using different means and the particular software storage and execution configurations described above may be varied in many different ways. Thus software implementing the techniques described above may be distributed on various types of computer readable media not limited to the forms of memory that are specifically described.

Although the subject matter has been described in language specific to structural features and or methodological acts it is to be understood that the subject matter defined in the appended claims is not necessarily limited to the specific features or acts described. Rather the specific features and acts are disclosed as illustrative forms of implementing the claims. For example the methodological acts need not be performed in the order or combinations described herein and may be performed in any combination of one or more acts.

