---

title: Method and system for installing applications
abstract: A method for installing an application according to an exemplary embodiment downloads an application purchased by a client and installs the application in a terminal in an asynchronous manner. The method includes transmitting a request to download at least one application to the server, downloading an application from the server in response to the request to download at least one application and storing the downloaded application, and installing the stored application in the terminal in an order of completion of downloading of the application.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08935690&OS=08935690&RS=08935690
owner: Samsung Electronics Co., Ltd.
number: 08935690
owner_city: Yeongtong-gu, Suwon-si, Gyeonggi-do
owner_country: KR
publication_date: 20110201
---
This application claims priority from Korean Patent Application No. 2010 0072852 filed in the Korean Intellectual Property Office on Jul. 28 2010 the disclosure of which is incorporated herein by reference. In addition this application claims the benefit of U.S. Provisional Patent Application No. 61 304 017 filed in the U.S. Patent and Trademark Office on Feb. 12 2010 the teachings of which are incorporated herein by reference.

The present invention relates to a method and a system for installing applications and more particularly to a method and a system for installing applications on a terminal using a personal computer PC .

Recently as a smart phone is widely recognized and becoming prevalent applications are increasingly downloaded and installed using an application store by users of all types.

In order to download applications in a terminal such as a mobile phone a PC is typically used to install the applications. However a conventional method of installing applications using a PC employs synchronization method which has drawbacks.

For example while an application is synchronized no operation can be performed in an application store and thus a user has to wait until the synchronization is completed.

In addition if an additional application is installed it is not possible to install only the newly added application. Instead the entire applications must be synchronized causing inconvenience to the user.

The present invention overcomes the above described problems and provides additional advantages by providing a method and an apparatus for installing applications using an asynchronous method.

In accordance with another aspect of the invention a method for installing an application that is purchased by a client and downloaded from a server in a terminal includes transmitting a request to download at least one application to the server downloading an application from the server in response to the request to download at least one application and storing the downloaded application and installing the stored application in the terminal in an order of completion of downloading of the application.

A protocol between the client and the server may be a Hypertext Transfer Protocol over Secure Socket Layer HTTPS protocol.

The storing may include downloading the application through a one time URL address transmitted from the server.

The one time URL address may be generated as random characters are combined and may be discarded after being used one time.

The storing may include storing an application downloaded from the server in the client in a form of package.

The installing may include receiving a response to a request for availability of installation of the application from the server transmitting a command to side load the application to the terminal and side loading the application on the terminal and if a side loading completion call back is received from the terminal transmitting a command to install the application.

In accordance with another aspect of the invention a method for installing an application that is downloaded from a server and stored in a client in a terminal includes if a command to side load the stored application is received from the client side loading the stored application from the client if the side loading is completed transmitting the side loading call back signal to the client and if a command to install the side loaded application is received from the client installing the side loaded application in the terminal wherein the application stored in the client is downloaded from the server and stored in an order of completion of downloading of the application.

The side loading command and the installing command may be transmitted to the terminal using object exchange OBEX .

In accordance with another aspect of the invention a system for installing an application that is purchased by a client and downloaded from the server in a terminal includes an application downloading request transmitting unit which transmits a request to download at least one application to the server an application storage unit which downloads an application from the server in response to the request to download at least one application and stores the downloaded application and an application installing unit which installs the stored application in the terminal in an order of completion of downloading the application.

A protocol between the client and the server may be a Hypertext Transfer Protocol over Secure Socket Layer HTTPS protocol.

The application storage unit may include a first queue which downloads the application from the server and stores the downloaded application in an order of purchasing the application a local storage unit which stores the application downloaded from the server in a form of package and a second queue which stores the application stored in a form of package in an order of completion of downloading.

The application storage unit may download the application through a one time URL address transmitted from the server.

The one time URL address may be generated as random characters are combined and may be abolished discarded after being used one time.

The application installing unit may include an installation availability request receiving unit which receives a response to a request for availability of installation of the application from the server a side loading unit which transmits a command to side load the application to the terminal and side loads the application on the terminal and an installation command transmitting unit which transmits a command to install the application if a side loading completion call back is received from the terminal.

The application installing unit may further include an installation completion call back receiving unit which receives an application completion call back from the terminal.

In accordance with another aspect of the invention a system for installing an application that is downloaded from a server and stored in a client in a terminal includes a side loading receiving unit which if a command to side load the stored application is received from the client receives side loading of the stored application from the client a side loading call back signal transmitting unit which if the side loading is completed transmits the side loading call back signal to the client and a terminal installing unit which if a command to install the side loaded application is received from the client installs the side loaded application in the terminal wherein the application stored in the client is downloaded from the server and stored in an order of completion of downloading of the application.

The side loading command and the installing command may be transmitted to the terminal using object exchange OBEX .

According to the various exemplary embodiments an application may be downloaded and installed in an asynchronous manner and thus user convenience may be enhanced.

In the following description like drawing reference numerals are used for the like elements even in different drawings. The matters defined in the description such as detailed construction and elements are provided to assist in a comprehensive understanding of exemplary embodiments. However exemplary embodiments can be practiced without those specifically defined matters. Also well known functions or constructions are not described in detail as they would obscure the application with unnecessary detail.

Herein the sever refers to a server which runs an application store for selling applications to users and the server stores a plurality of applications to be transmitted to a client. The client refers to a PC which transmits a request for downloading a plurality of applications available in an application store to a server and stores applications downloaded from the server. The terminal refers to a mobile phone which executes purchased applications and may include various multimedia apparatuses such as a smart phone a cellular phone an MP3 player and a PMP.

In operation the download request transmitting unit transmits a request for downloading at least one application to the server . The server transmits an application to the client in response to the download request of the client .

Herein the protocol between the client and the server may be a Hypertext Transfer Protocol over Secure Socket Layer HTTPS protocol. The HTTPS protocol is employed for security reasons since the HTTPS protocol may be protected from eavesdropping while an HTTP protocol is vulnerable to eavesdropping when contents are transmitted through a specific program.

Herein the HTTPS is an upgraded version of the HTTP which is a worldwide web communication protocol. The HTTPS is developed by Netscape Communications Corporation for authentication and encryption of communication and is widely used in e commerce.

The HTTPS encrypts a session data through an SSL protocol or a TLS protocol instead of using a general text in socket communication. Accordingly an appropriate level of security for the data should be guaranteed. The basic TCP IP port of HTTPS is 443. The level of security depends on accuracy of configuration of a web browser and an encryption algorithm supporting the software of the server . The URL of a web page using HTTPS starts with https instead of http .

The application storage unit downloads an application corresponding to a request for downloading at least one application from the server and stores the downloaded application.

Herein the application storage unit may download an application from the server in an asynchronous manner.

Accordingly as an application installing system according to an exemplary embodiment downloads an application from the server in an asynchronous manner the client may navigate other applications that is make inquires into or search for other applications in an application store while an application available in the application store is being downloaded or installed. In addition only one application may be installed without synchronizing and thus user convenience may be enhanced.

In an exemplary embodiment the application storage unit comprises a first queue a local storage unit and a second queue as illustrated in .

Once applications are downloaded on the client from the server the first queue downloads the applications from the server in the order of purchase and stores them.

The local storage unit stores applications which are downloaded and stored in the first queue in the form of package. Herein storing applications in the form of package means downloading not only one program but also other related programs together. For example when downloading MS OFFICE not only MS OFFICE but also other MS OFFICE related programs such as Word PowerPoint and Excel are downloaded and stored.

Specifically the local storage unit stores applications downloaded from the server in the form of application binary. Herein the application binary interface ABI covers details regarding how functions control and pass parameter and retrieve return values. In computer software the ABI describes the low level interface between an operation program and an operating system or another application an operating program and the library of the operating program or between application components. Herein the ABI is distinct from an application programming interface API which defines interface between a source code and a library.

The second queue stores applications stored in the local storage unit in the form of package in the order of completion of downloading.

The application installing system according to an exemplary embodiment may install applications which are stored in the second queue in the order of downloading completion on the terminal by the application installing unit which will be explained later.

Referring to the application storage unit may download applications through a one time URL address transmitted from the server and store them. Herein the one time URL address is generated as random characters are combined and may be abolished discarded after being used one time.

As the application installing system according to an exemplary embodiment accesses and uses a one time URL address once and abolishes the URL address applications may be downloaded through the one time URL address only one time.

The application installing unit installs on the terminal applications which are stored in the application storage unit in the order of completion of downloading. In other words the application installing system according to an exemplary embodiment does not install applications on the terminal in the order of purchase in a synchronous manner. Instead the application installing system according to an exemplary embodiment downloads applications in asynchronous manner and stores the applications on the terminal in the order of completion of downloading.

In an exemplary embodiment the application installing unit comprises an installation availability request receiving unit a side loading unit an installation command transmitting unit and an installation completion call back receiving unit as illustrated in .

The installation availability request receiving unit receives a response to a request for application installation availability from the server . In other words the installation availability request receiving unit transmits a request for installation availability of an application which is purchased downloaded and stored from the server to the server and receives a response to the request from the server . This is to prevent for example an application X which is purchased by a user A and installed in the terminal of the user A from being installed in the terminal of a user B. The server stores information regarding a user terminal such as a type of apparatus or a phone ID of the user terminal which purchases an application and may transmit a response to the request for installation availability of an application to the client using stored information regarding the user terminal.

The side loading unit transmits a side loading command of an application to the terminal and side loads the application on the terminal . Herein the side loading represents transmitting contents for a personal computer to a terminal for example copying and sending a music file or video which is contents for a personal computer to a terminal such as a cellular phone via a USB cable or wirelessly. In other words the side loading unit transmits a side loading command to a terminal and actually performs side loading of an application on the terminal.

If the installation command transmitting unit receives a side loading completion call back from the terminal the installation command transmitting unit transmits a command to install an application to the terminal . That is if the installation command transmitting unit receives a side loading completion call back indicating that side loading is completed from the terminal the installation command transmitting unit transmits a command to install an application to the terminal .

The installation completion call back receiving unit receives an installation completion call back indicating that installation of an application is completed from the terminal . That is if the terminal completes installing a side loaded application the installation completion call back receiving unit receives an installation completion call back transmitted from the terminal .

Referring back to if the side loading receiving unit receives a command to perform side loading of an application stored in the application storage unit of the client the side loading receiving unit receives side loading of the stored application from the client .

If side loading is completed the side loading call back transmitting unit transmits a side loading call back to the client to inform the client of completion of side loading.

If the terminal installing unit receives a command to install a side loaded application from a client the terminal installing unit installs the side loaded application in a terminal.

Herein applications stored in the client may be downloaded and stored from the server in the order of completion of downloading. That is in an application installing system according to an exemplary embodiment applications are not downloaded in the order of purchase in a synchronous matter but instead applications are downloaded in an asynchronous manner.

Herein a side loading command and an installation command may be transmitted to a terminal using object exchange OBEX . The OBEX is a communication protocol between a terminal and a client and may be regarded as a kind of MODEM communication. The OBEX is used mostly when a command is transmitted to a terminal. The OBEX is originally developed to exchange data object through an infrared link and refers to a set of protocols which facilitate exchange of objects such as vCard contact information or vCalendar schedule information using IrDA or Bluetooth.

In addition applications may be side loaded on a terminal using a media transfer protocol MTP . The MTP is a protocol used mostly when a media file is transmitted to a terminal and may be used in compatible with the OBEX. Although the MTP is relatively slow in comparison with a UMS it provides an enhanced robust security protection by preventing possibilities of virus or malicious code infiltration.

As illustrated in an application store web browser displays a plurality of applications and if an application is purchased and requested to be downloaded on a client an application list is displayed on a download status window to show applications being downloaded and the download status of each application is also displayed on the window.

In an application installing system according to an exemplary embodiment applications are not downloaded in the order of purchase in a synchronous matter and instead applications are downloaded in an asynchronous manner. Therefore it is possible to navigate other applications that is make inquires into or search for other applications in an application store.

Subsequently the client downloads an application from the server in response to the download request from the server S and stores the downloaded application in a storage unit S .

Herein the applications may be downloaded stored in the storage unit in the order of completion of downloading from the server .

In an exemplary embodiment of downloading applications S applications may be downloaded from the server in asynchronous manner.

When applications are downloaded S applications may be downloaded through a one time URL address transmitted from the server .

Herein the one time URL address is generated as random characters are combined and may be abolished discarded after being used one time.

In an exemplary embodiment of storing applications S the applications downloaded from the server may be stored in a storage unit of the client in the form of package.

Subsequently in order to see if it is possible to install an application stored in the client in a terminal the client transmits a request for installation availability of application to the server in the order of completion of downloading of applications S .

In other words the client transmits to the server a request for installation availability of an application purchased and downloaded from the server in the terminal which is connected to the client and receives a response to the request from the server . This is to prevent for example an application X which is purchased by a user A and installed in the terminal of the user A from being installed in the terminal of a user B. The server stores information regarding a user terminal such as a type of apparatus or a phone ID of the user terminal which purchases an application and may transmit a response to the request for installation availability of an application to the client using stored information regarding the user terminal.

Subsequently the client receives a response to the request for installation availability of an application from the server S . If the client receives a response that it is possible to install an application the client transmits a command to side load the application to the terminal and performs side loading of the actual application stored in the client on the terminal S .

Herein the side loading represents transmitting contents for a personal computer to a terminal for example copying and sending a music file or video which is contents for a personal computer to a terminal such as a cellular phone via a USB cable or wirelessly.

Herein a side loading command and an installation command may be transmitted to the terminal using object exchange OBEX . The OBEX is a communication protocol between a terminal and a client and may be regarded as a kind of MODEM communication. The OBEX is used mostly when a command is transmitted to a terminal.

In addition applications may be side loaded on a terminal using a media transfer protocol MTP . The MTP is a protocol used mostly when a media file is transmitted to a terminal and may be used in compatible with the OBEX. Although the MTP is relatively slow in comparison with a UMS it provides a better security protection by preventing possibilities of virus or malicious code infiltration.

If the client receives a side loading completion call back from the terminal S the client transmits a command to install an application to the terminal S .

In other words if the client receives a side loading completion call back indicating that side loading is completed from the terminal the client transmits a command to install an application to the terminal .

Subsequently the terminal installs the application side loaded from the client in the terminal S and if installation of the application is completed transmits an installation completion call back to the client S .

Accordingly in an application installing system according to an exemplary embodiment applications are downloaded from the server in an asynchronous manner. Therefore the client may navigate other applications that is make inquires into or search for other applications in an application store while an application available in the application store is being downloaded or installed. In addition only one application may be installed without synchronizing the entire applications and thus user convenience may be enhanced.

Meanwhile the above mentioned application installing method may be embodied as a program command executable through various computer means and recorded in a recording medium readable by a computer. In this case the recording medium readable by a computer may include a program command a data file and data configuration alone or in combination. Meanwhile the program command recorded in the recording medium may be exclusively designed and configured for the present invention or may be known to and commonly used by those skilled in the field of computer software industry.

The recording medium readable by a computer includes magnetic media such as a hard disk a floppy disk and a magnetic tape optical media such as a CD ROM and a DVD magneto optical media such as a floptical disk and a hardware apparatus specially designed to store and perform a program command such as ROM RAM and a flash memory. Meanwhile such a recording medium may be a transmission medium such as an optical or metal strip and waveguide including carrier wave which transmits a signal designating a program command data configuration and so forth.

In addition the program command includes a machine code composed by a compiler and a high level language code executable by a computer using an interpreter. The above described hardware apparatus may be configured to operate as more than one software module to perform operations of the present invention and vice versa.

Although a few embodiments of the present invention have been shown and described it would be appreciated by those skilled in the art that changes may be made in this embodiment without departing from the principles and spirit of the invention the scope of which is defined in the claims and their equivalents.

