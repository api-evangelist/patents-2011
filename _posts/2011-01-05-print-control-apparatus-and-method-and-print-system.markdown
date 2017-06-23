---

title: Print control apparatus and method, and print system
abstract: In this invention, a combined job obtained by combining a plurality of jobs is authenticated as a single job. According to the arrangement of this invention, when print jobs are to be spooled, these jobs are transferred from a dispatcher to a spooler where the jobs are combined. Upon reception of a print instruction, the print job is read out from a spool file, transferred from a despooler to a graphic engine again, and transferred from the dispatcher to a printer driver. At this time, the printer driver issues an authentication request in printing to a job accounting client. Thus, only one authentication request suffices for one combined job.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08035841&OS=08035841&RS=08035841
owner: Canon Kabushiki Kaisha
number: 08035841
owner_city: Tokyo
owner_country: JP
publication_date: 20110105
---
This application is a continuation of U.S. patent applicant Ser. No. 11 838 964 filed Aug. 15 2007 which is a divisional of U.S. patent application Ser. No. 09 840 894 filed Apr. 25 2001 both of which are incorporated by reference herein in their entirety as if fully set forth herein and which claim the benefit of priority under 35 U.S.C. 119 based on Japanese Patent Application No. 2000 128543 filed Apr. 27 2000 Japanese Patent Application No. 2000 128541 filed Apr. 27 2000 and Japanese Patent Application No. 2000 128540 filed Apr. 27 2000 which are incorporated by reference herein in their entirety as if fully set forth herein.

The present invention relates to a print control method and apparatus and a medium in a system including both a printer and an information processing apparatus such as a personal computer.

Recently a job accounting system for counting the number of sheets used for each user and performing accounting or the like on the basis of the data is being available for a network connected printer.

The job accounting system manages accounting information such as the number of sheets to be printed for each user. The user can use a printer belonging to the job accounting system only when he she is authenticated by the system. The user inputs authentication information such as an ID or password to the system before execution of a print job and is generally authenticated in units of jobs.

Also in a printer used in this accounting system various additional functions are realized for a printer driver of controlling the printer. A printer driver having among these functions a job combination function of temporarily spooling a plurality of jobs and printing them at once is available.

To print data by the printer driver using the job combination function in the job accounting system print jobs are not processed as a single job in authentication and the user must perform authentication processing for each of the combined print jobs. This degrades productivity and operability which is the first problem.

In the system in which authentication is done in units of print jobs authentication information must be confirmed even at a terminal dedicated to a single user every time a print request is issued to generate a print job. This is cumbersome and degrades operability. To print data in an environment where a plurality of pieces of authentication information are used e.g. at a terminal shared by a plurality of users accurate accounting information cannot be acquired unless authentication information is confirmed for each print job. Owing to the usage of the terminal operability and authentication reliability are difficult to be consistent with each other which is the second problem.

When authentication information is not confirmed for each print job authentication processing is performed without confirming authentication information in advance every printing. In this case authentication information must be confirmed to be correct prior to printing which is the third problem.

When the job accounting system is implemented by a computer it is implemented by the OS Operating System . Some types of OSs can define a plurality of authority levels but only a single job accounting setting method is provided. For example a given type of OS cannot provide the manager with a flexible operation method such as a function capable of changing whether to save authentication information which is the fourth problem.

The present invention has been made to solve the first problem and has as its object to improve the operability of authentication processing by providing a print control method and apparatus which enable printing by single authentication processing for combined print jobs in a printer driver having a function of combining a plurality of print jobs into a single print job and printing it.

The present invention has been made to solve the second problem and has as its object to provide a print control apparatus and method and a print system capable of flexibly changing authentication information confirmation procedures in accordance with the operation environment and causing the user to confirm authentication information in accordance with the operation environment.

The present invention has been made to solve the third problem and has as its object to provide a print control apparatus and method and a print system capable of determining correctness of authentication information prior to printing.

The present invention has been made to solve the fourth problem and has as its object to provide a print control apparatus and method and a print system that provide a method of saving a plurality of pieces of authentication information in an OS which can define a plurality of authority levels thereby providing a flexible operation method to a user having an authority with a high degree of freedom.

A print control apparatus for performing user authentication processing in print processing comprises

an authentication request unit for issuing an authentication request to an authentication server for the single print job combined by the job combination unit 

The print control apparatus preferably further comprises a counting unit for counting a print amount including the number of prints to be printed by the combined print job and transmitting information about the counted print amount to a counting server.

It is preferable that the authentication server and the print control apparatus be connected via a communication network and that the communication network be connected to a plurality of printers.

A print control apparatus for performing user authentication processing in print processing comprises

an authentication request unit for transmitting the authentication information held by the holding unit to an authentication server and requesting authentication and

an output unit for transmitting the authentication information held by the holding unit to the authentication server and if authentication succeeds outputting print data to a printer.

The print control apparatus preferably further comprises a re input unit for re inputting the authentication information held by the holding unit if the authentication request from the authentication request unit fails.

The print control apparatus preferably further comprises a confirmation unit for causing a user to confirm the authentication information held by the holding unit before the authentication information is transmitted from the output unit to the authentication server.

It is preferable that the print control apparatus further comprise a setting unit for setting whether to cause the user to confirm the authentication information via the confirmation unit and that when the setting unit sets the authentication information so as not to confirm the authentication information via the confirmation unit the confirmation unit do not operate.

The print control apparatus preferably further comprises a counting unit for counting a print amount including the number of prints by the printer on the basis of print data output from the output unit and transmitting information about the counted print amount to a counting server.

It is preferable that the authentication server and the print control apparatus be connected via a communication network and that the communication network be connected to a plurality of printers.

It is preferable that the print control apparatus further comprise a designation unit for designating whether to hold the authentication information by the holding unit and that when the designation unit designates not to hold the authentication information the authentication information held by the holding unit be erased every authentication.

It is preferable that a user be assigned an identifier and an authority level corresponding to the identifier and that the print control apparatus further comprise a validating unit for validating the designation unit when the authority level assigned to the user is a predetermined authority level.

Other features and advantages of the present invention will be apparent from the following description taken in conjunction with the accompanying drawings in which like reference characters designate the same or similar parts throughout the figures thereof.

Prior to a description of the overall system a job accounting server application a job accounting client application and a printer having a job accounting function will be explained as hardware or software building components.

The printer having the job accounting function has not only the function of a general conventional printer but also a job accounting function of accumulating and managing the number of printed pages paper size double single side printing and color monochrome printing for each user and an authentication function of authenticating the user. In user authentication authentication information sent from the job accounting client application to be described later is collated with user unique information stored in advance and whether to authenticate the user is responded.

A conventional printer does not have any job accounting function and printing is done based on received print data.

The job accounting server application provides a conventional printer having no job accounting function with the same function as the job accounting function of the printer having the job accounting function. The job accounting server application is executed on a server computer functioning as a job accounting server and its functions are equivalent to the functions of the printer having the job accounting function except for a printing function.

The functions are roughly classified into two. The first function is a user authentication function and the second one is a job accounting function. The user authentication function is the same as that of the printer having the job accounting function. However the job accounting server application does not have any print function and thus cannot generate job accounting information while printing it. As for the job accounting function therefore job accounting information transmitted from the job accounting client application is accumulated and managed.

The job accounting client application roughly has two functions. The first function is a user authentication function. When a printer driver issues an authentication request the job accounting client application transmits authentication information received together with the request to the job accounting server application or printer having the job accounting function receives the authentication result and sends it back to the printer driver.

The second function is a job accounting information generation function. This function is executed only when a printer in use is a conventional printer having no job accounting function. The job accounting client application acquires print information in the following manner and generates from this information job accounting information such as the number of pages to be printed and the size. The job accounting client application transmits the generated job accounting information to the job accounting server application. The second function is enabled only when a computer having a job accounting server application exists on a network.

The authentication function and job accounting function are implemented in a single module in the first embodiment but may be implemented in separate modules.

The first type is a printer driver coping with the job accounting function. This printer driver has an authentication function of realizing a user authentication request UI on a computer display prior to printing and issuing an authentication request to the job accounting client application. Further the printer driver has a function of transferring to the job accounting client application original information of job accounting information such as the number of pages to be printed and the size on the basis of print data generated in accordance with a print request received from an application. Printers used are classified into a printer having the job accounting function and a conventional printer having no job accounting function. In the use of a printer having the job accounting function job accounting information or its original information need not be transferred to the job accounting client application. In this case the printer need not be equipped with the latter function.

The second type is a printer driver for a conventional printer that does not cope with the job accounting function. This printer driver does not have the two functions.

The operations of respective units in the arrangement of will be described. Especially the operation of a job accounting client application will be explained with reference to the flow chart of .

A job accounting server application exists in the computer connected to a print network. OSs Operating Systems run on the server computer and the client computers and . OSs running on the client computers and will be called OS and OS.

In the client computer an application invokes an API Application Programming Interface from a GDI Graphic Device Interface system in the OS that performs graphic drawing of the OS.

The job accounting client application monitors hooks the API S in . With this operation the number of operations of invoking the API which designates page feed or sheet discharge is counted and the number of discharged sheets and the number of pages for a job issued by the application are acquired. Note that information obtained by hooking the API is used when a printer driver does not have a function of sending print job information. This function is adopted when the printer driver supports the job accounting function so that the job accounting client application checks whether the printer driver has the job accounting function step S .

If the printer driver has the job accounting function and the job accounting client application can be notified of print information the information acquired by hooking is discarded step S and the job accounting server application is notified of information acquired by the printer driver step S . If the printer driver does not support the job accounting function the information acquired by hooking the API is transmitted to the job accounting server application .

The GDI transfers print data generated based on a print request from the application to a spooler where the print data is accumulated. The spooler transmits the print data to the printer while monitoring the state of the printer .

In the client computer when an application invokes an API from a GDI and issues a print job a printer driver converts the API invoked by the application into print data and transfers the print data to a system spooler where the print data is accumulated. The system spooler monitors the state of the printer and if the printer is ready transmits the print data to the printer .

A job accounting client application monitors the system spooler on the basis of the API notification from the printer driver manages the print data and job accounting information in association with each other and acquires information such as the number of discharged sheets and the number of pages for the print job. An information acquisition method will be described later. Similar to the job accounting client application the job accounting client application notifies the job accounting server application of the information acquired by hooking the API or the job accounting information acquired from the printer driver

As described above in the first embodiment the job accounting server application exists in the network connected computer and job accounting information acquired by the client computer is accumulated and managed in the job accounting server application . The function of counting and managing pieces of print job information is realized by the printer having the job accounting function when print data is transmitted to the printer having the job accounting function. In user authentication authentication itself is done by the printer but a UI User Interface at that time is realized by the printer driver of the printer having the job accounting function.

More specifically when the user performs printing by using the printer the application transfers data to the GDI and then the printer driver of the printer generates print data based on the data similar to a conventional printer. The print data is temporarily accumulated in the system spooler and transmitted to the printer . The printer executes printing on the basis of the received data and generates accumulates and manages job accounting information for each user in accordance with the number of pages the paper size the type of printing such as double side printing or color printing.

The system shown in employs both the printer having the job accounting function and the conventional printer having no job accounting function. In this system even when the client computer prints data by using the printer having the job accounting function the job accounting client application hooks an API invocation from the application or the printer driver provides data thus acquiring job accounting information such as the number of discharged sheets or the number of pages for the print job. The job accounting information is transmitted to the job accounting server application which can centralize the job accounting information. In this case the printer may manage the job accounting information. In other words a plurality of job accounting systems may exist on a network.

The hardware arrangements of the client computers and and the server computer in will be briefly described with reference to .

In a computer comprises a CPU for processing a document containing graphics images characters tables including a spreadsheet and the like on the basis of a document processing program or the like stored in the program ROM of a ROM . The CPU integrally controls devices connected to a system bus . Also the CPU implements the above described functions by executing an OS including an application and GDI and programs such as a printer driver program system spooler and job accounting client application including the procedures of flow charts to be described later .

A RAM functions as e.g. the main memory and work area of the CPU . A keyboard controller KBC controls a key input from a keyboard or a pointing device not shown . A CRT controller CRTC controls display of a CRT display . A disk controller DKC controls access to an external memory such as a hard disk HD or floppy disk FD for storing a boot program various applications font data user files edit files and the like. A LAN interface LAN I F is connected to a local area network and executes communication control processing with devices on the network such as the printer printer and another computer. The CPU executes e.g. rasterizing processing of an outline font to a display information RAM set on the RAM and enables WYSIWYG What You See Is What You Get function of making display contents coincide with print contents on the CRT . Further the CPU opens various registered windows on the basis of commands designated with a mouse cursor not shown on the CRT display and executes various data processes.

In all the printers are network printers and the computer is connected to the printers via the LAN interface . The present invention can also be applied to an arrangement in which the computer has an interface such as a parallel interface or USB and is connected to a local printer.

An application GDI graphic engine printer driver and system spooler are program modules which exist as files saved in e.g. the external memory on the host computer and when being to be executed are loaded to the internal memory of the host computer by an OS or a module using these modules.

The GDI graphic engine loads the printer driver prepared for each printing apparatus to the internal memory of the computer and sets an output from the application to the printer driver . The GDI graphic engine converts print data received from the application into a printer driver readable format and outputs the converted data to the printer driver .

The printer driver issues an authentication request to a job accounting client application at the start of printing. The job accounting client application inquires authentication of the printer having the job accounting function acquires the result and notifies the printer driver of the result. If authentication succeeds the printer driver converts the drawing data received from the GDI graphic engine into a printer recognizable control command e.g. PDL Page Description Language . The converted printer control command is output as print data by the OS via the system spooler . When the print data is transmitted to the printer having the job accounting function authentication information to be described later is added and transmitted in the print data. As will be described later the authentication request destination may be the job accounting server application.

In job information includes information for identifying whether to transmit the job to a printer having the job accounting function or to a printer having no job accounting function and authentication information such as a user ID or password to be described later . This also applies to .

A job identifier includes an identifier for association with a print job when the job accounting client application spools the print job in the spooler.

In an API return value includes an argument received from the job accounting client application when the printer driver notifies the job accounting client application of information in by using an API at the start of printing.

A total sheet count includes the total number of discharged sheets for the job. Job accounting representing accounting or the like can be realized based on this information.

Block information includes information representing a block divided for sheets having common items when any of items of detailed information changes within one print job by designating the paper size paper type or N up printing function of printing N pages for each sheet . If these items do not change within one job one job is set as one block.

The detailed information includes for each block pieces of detailed information such as double single side printing paper type paper size color information the number of pages per sheet the number of copies and the total number of sheets per block.

As described above pieces of job accounting information shown in are transferred from the printer driver to the job accounting client application but are not used in the printer having the job accounting function.

A processing flow in the job accounting system by the printer driver will be explained with reference to and subsequent drawings. In this case the printer driver copes with the job accounting function i.e. is for the printer having the job accounting function. However the printer itself may be the conventional printer as far as the printer driver copes with the job accounting function.

If a check box in is checked the printer driver operates as part of the job accounting system. If the check box is not checked the printer driver transmits only print data regardless of the job accounting system.

A left icon is displayed in synchronism with the check box . This icon is displayed for all the sheets various windows displayed as GUIs of the printer driver and designed to allow the user to grasp the job accounting setting status at a glance.

A check box is displayed when a user who has a manager authority permitted to set the computer environment and the like sets the printer in an OS which permits each log in user to have a different authority. Depending on the check ON OFF state of this check box whether password information necessary for job accounting can be held is determined for a user who uses this printer driver.

More specifically dialogs displayed upon clicking an authentication information input button are different between the check ON and OFF states of the check box . If the check box is checked the dialog in is displayed. In this case the user can input an ID for specifying a department or user as authentication information and a password for the ID .

If the check box is not checked the dialog in is displayed. That is the user can input only the ID for specifying a department or user as authentication information.

In this manner the OS capable of setting a different authority for each user can provide security management variations by the manager.

A button on the authentication information input window in is used to inquire whether the input ID and password are correct as pieces of job accounting information. The user can click the button when the ID and password are input. If the user clicks the button the printer driver requests authentication information collation of the job accounting client application . The job accounting client application transmits the authentication information to the job accounting server application or the printer having the job accounting function and requests authentication. Authentication is performed by the job accounting server application and or the printer having the accounting function in accordance with the following three cases.

 Case 1 When the job accounting server application exists in the system authentication information is transmitted to the job accounting server application to request authentication.

 Case 2 When the printer driver is a printer driver for the printer having the job accounting function authentication information is transmitted to the printer to request authentication.

 Case 3 When the printer driver is a printer driver for the printer having the job accounting function and the job accounting server application exists in the system i.e. when two job accounting systems exist in one print system authentication information is transmitted to the printer to request authentication and at the same time authentication information is transmitted to the job accounting server application to request authentication.

Alternatively authentication information input in accordance with a setting to be described later may be saved cached and the saved authentication information may be transmitted to request authentication. Saving authentication information can shorten the authentication information inquiry time.

If the authentication information is determined to be correct by the inquiry the message shown in is displayed. If the authentication information is determined to be incorrect the message shown in is displayed.

A check box is a button for enabling selecting whether to confirm authentication information in printing. When the check box is checked a dialog shown in is displayed immediately before the application issues a print instruction printing by the printer driver starts and print data is transmitted. When the check box is not checked printing is done by using the saved authentication information without displaying the dialog .

Even if the check box is not checked and no authentication information is saved the dialog is displayed without displaying the password as shown in in order to request input of authentication information.

In this way input authentication information can be held by designating the check box which can eliminate cumbersome input and can shorten the authentication time.

There can be provided a method capable of confirming in advance whether authentication information to be saved is correct by clicking the button and saving correct authentication information for the user.

As a supplemental explanation when it is set in the check box not to hold password information necessary for job accounting the password is not held the check box need not be displayed and the dialog is always displayed.

In the first embodiment authentication information to which saving non saving can be designated is limited to the password and the ID is unconditionally saved. However whether to save both the password and ID may be designated.

By checking the check box in the dialog is displayed for each print job the user can edit authentication information and printing using a different ID for each printing can be realized. For example when the printer driver is used in an environment where printing is done using a plurality of IDs authentication can be reliably performed for each ID by causing the user to confirm authentication information at the start of a print job and to input authentication information again. When the printer driver is used in an environment where only single authentication information is used the operation steps can be decreased by eliminating confirmation of authentication information at the start of printing.

The check box enables setting whether to confirm authentication information in printing which decreases the operation steps in job accounting. Authentication information can be easily changed for each print job which improves convenience.

When the dialog is displayed at the start of printing the user clicks an OK button to transmit authentication information immediately before transmission of print data. If the authentication information is correct printing is determined to be enabled and the print data is transmitted. If the authentication is incorrect the message in is displayed and the user clicks an OK button to display the dialog . The user inputs authentication information again and clicks the OK button to transmit the authentication information.

In transmitting saved authentication information the dialog is not displayed. If the authentication information is incorrect the message in is displayed and the user clicks an OK button to display the dialog . The user inputs authentication information again and clicks the OK button to transmit the authentication information. The user can stop printing by clicking a cancel button . In this case the printer driver application is notified of the printing failure from the printer driver and does not transmit subsequent print data.

In step S the printer driver displays the UI window of on a display monitor e.g. the CRT in . In step S the printer driver determines whether the operating user is a manager user permitted to set the print environment. If NO in step S the check box setting for saving authentication information is erased or grayed out in step S so as to prevent input of any information to this check box. If YES in step S the check box is kept displayed.

After the UI window is displayed the printer driver waits for a user input in step S. Upon reception of an input the printer driver checks the contents in step S. If the input is OK the printer driver saves print settings input in step S and ends the processing. In this case save of authentication information is set. If therefore authentication information has been input it is also saved. If the input is cancel the printer driver discards the input print settings and ends the processing.

Assume that the clicked button is the verify button on the window of which is opened upon clicking the setting button of the printer setting window. Similar to step S in to be described later the printer driver transfers the input authentication information to the job accounting client application to request authentication. If receiving the authentication result from the job accounting client application the printer driver checks the result. If authentication succeeds the window of is displayed otherwise the window of is displayed. The printer driver notifies the user whether the authentication information is correctly set.

For another input the printer driver updates the display window in accordance with the input and waits for an input in step S.

In this way only the manager can change the setting for saving authentication information and can confirm the authentication information prior to printing.

In step S the printer driver determines whether job accounting check button in is ON. If YES in step S the printer driver advances to step S if NO to step S.

In step S the printer driver determines based on the check button whether to display the authentication information confirmation dialog of in printing. If YES in step S the printer driver shifts to step S if NO to step S.

In step S the printer driver determines whether authentication information has been held. If YES in step S the printer driver shifts to step S if NO to step S. For example in step S the printer driver checks the check button in and if the check button is ON determines that authentication information has been held. Alternatively the printer driver may check the authentication information storage area and if data other than specific data such as null data is stored may determine that authentication information has been held.

In step S confirmation of authentication information at the start of printing has been set or no authentication information is saved. Thus the printer driver displays the authentication information confirmation dialog and waits for a user input.

If the user event input is a print execution request OK button is clicked in step S the printer driver advances to step S if NO to step S.

In step S the printer driver executes user authentication on the basis of the input authentication information and starts printing. At this time when save of authentication information has been set the printer driver saves the information in a predetermined area of a nonvolatile medium.

In step S the printer driver executes authentication processing. More specifically the printer driver notifies the job accounting client application of the information shown in . The job accounting client application transmits the acquired information to the job accounting server application or the printer having the job accounting function and obtains the authentication result.

The printer driver receives the authentication result from the job accounting client application. If authentication succeeds the printer driver advances to step S if NO in step S to step S.

In step S the printer driver displays an authentication failure message waits for a user input and returns to step S when the OK button is clicked.

In step S the printer driver determines whether a user event input is a print stop request cancel button is clicked . If YES in step S the printer driver shifts to step S if NO waits for the next event.

In step S data transmission to the system spooler starts. After the end of transmission the printer driver determines in step S whether job accounting is ON. If YES in step S the printer driver notifies the job accounting client application of the job accounting information shown in at the end of printing in step S. The job accounting server application receives the job accounting information from the job accounting client application and performs job accounting based on the received information. Note that when no job accounting server application exists in the network system this information need not be transmitted.

The printer having the job accounting function counts a numeric value such as the number of prints for each paper size serving as the origin of job accounting information in the printer along with print processing.

If YES in step S the printer driver reads out saved authentication information from the cache area to the authentication information area of the RAM in step S and advances to step S to execute authentication processing by using the authentication information.

The printer driver receives graphic data data of an image or document to be printed transferred from the graphic engine in step S and determines in step S whether a new block need be generated. In this case a new block is generated upon newly starting generation of print data or upon changing any of double single side printing paper type paper size color information the number of pages per sheet and the number of copies that are included in the detailed information in .

In step S a new block is generated. If the newly generated block is at the start of a new print job the printer driver ensures in the memory an area starting from the printer name to block information in and writes the information determined at this time in the area.

In step S the printer driver ensures an area used for detailed information of the new block in the format of and writes the currently determined information such as double single side printing paper type paper size color information the number of pages per sheet and the number of copies.

In step S the printer driver generates from the graphic data e.g. a PDL command to be transmitted to the printer. The printer driver checks in step S whether the command generated in step S is a sheet discharge command and if YES in step S counts the number of sheets in the detailed information of the block in step S.

The printer driver determines in step S whether to end the print job and if YES in step S transmits the print data via the OS and ends the processing.

In this manner the printer driver generates detailed job accounting information while generating print data.

If authentication information is transmitted from the printer driver to the job accounting client application in step S it is sent from the job accounting client application to the printer having the job accounting function. Then the flow in starts. In step S the printer collates the received authentication information with a database of correct authentication information stored in advance. The printer determines the result in step S. If collation succeeds the printer sends an authentication success message to the job accounting client application in step S if NO in step S sends an authentication failure message to the job accounting client application in step S. The job accounting system of the first embodiment implements the following characteristic functions.

 1 User authentication can be done prior to printing to prevent a situation in which authentication information is found to be incorrect when user authentication is done in printing.

 2 The manager user can set whether to save authentication information. Hence the manager can change this setting in accordance with the usage of the printer and the situation of the overall network system connected to the printer. For example the manager can strictly manage a color printer whose print cost is relatively high by inputting authentication information every time a user uses the printer and can simplify the operation of a monochrome printer which is used with a relatively low cost at the highest frequency by saving authentication information. Further the manager can cause a user to input authentication information every printing in order to accurately grasp account information of each department for a printer shared by a plurality of departments having different account management units.

 3 When save of authentication information is set the saved authentication information is used the user need not input authentication information and the print time can be shortened.

 4 Setting of inputting authentication information every print job can be selected. At a terminal shared by a plurality of users authentication information is input every print job regardless of whether authentication information has been saved. At a terminal dedicated to a single user if authentication information has been saved printing is executed by using the saved authentication information. This can realize efficient processing for a terminal dedicated to a single user and accurate account management for a terminal shared by a plurality of users.

 5 Accurate account management can be achieved because the printer driver can generate job accounting information in accordance with not only the number of sheets but also double single side printing paper type paper size color information and the number of pages per sheet.

That is detailed counting processes coping with various print forms from applications can be performed by counting the number of sheets for each print setting. Further accounting or the like can be accurately done based on detailed information.

In a print system according to the second embodiment in addition to the print system comprised of the printer and host computer shown in print data from an application may be temporarily spooled by intermediate code data as shown in .

For these purposes the system of is extended to spool print data by intermediate code data as shown in . Note that processing of print data is generally set from a window provided by the printer driver .

Basic processing in the extended system of will be explained. A dispatcher receives a print instruction from the graphic engine . If the print instruction received by the dispatcher from the graphic engine is one issued from the application to the graphic engine the dispatcher loads the spooler stored in an external memory and transmits the print instruction to not the printer driver but the spooler .

The spooler converts the received print instruction into an intermediate code and outputs the code to the spool file . The spooler acquires from the printer driver processing settings concerning print data set for the printer driver and saves them in the spool file .

The spool file is generated as a file in the external memory but may be generated in an internal memory. The spooler loads a spool file manager stored in the external memory and notifies the spool file manager of the generation status of the spool file . The spool file manager determines whether printing is possible in accordance with the contents of the processing settings concerning the print data stored in the spool file .

If the spool file manager determines that printing is possible by using the graphic engine the spool file manager loads a despooler stored in the external memory and instructs the despooler to execute print processing of the intermediate code described in the spool file .

The despooler processes the intermediate code included in the spool file in accordance with the contents of the processing settings included in the spool file and outputs the processed code via the graphic engine again.

If the print instruction received by the dispatcher from the graphic engine is one issued from the despooler to the graphic engine the dispatcher sends the print instruction to not the spooler but the printer driver .

To perform print preview change of print settings and combination of a plurality of jobs Edit and Preview is designated on a pull down menu serving as a means for performing Designate Output Destination in the properties of the printer driver as represented by a menu box of .

The contents set by the properties of the printer driver are stored in a structure provided by an OS as a setting file called DEVMODE in Windows OS . In this structure for example processing settings included in the spool file contain a setting representing whether to store data in the spool file manager . When the spool file manager reads the processing setting via the printer driver and finds that store has been designated a page drawing file and job setting file are generated and stored in the spool file as described above. The window of the spool file manager is popped up and a list of jobs spooled to the spool file is displayed as shown in . shows an example in which four jobs are spooled. Jobs can be processed by clicking the menu bar or the menu icon immediately below the menu bar.

The menu bar and menu icon are the same in the numbers of operations. The types of operations are 11 operations Print while a job is selected Proof Print for performing printing while a spool file of an intermediate code is left Print Preview for allowing the user to see an output preview of a job considering print settings Delete for deleting a spool file of an intermediate code Duplicate for forming a copy of a spool file of an intermediate code Combine for combining jobs of spool files of intermediate codes into one job Separate for separating a combined job into a plurality of original jobs Change Print Settings for changing the print settings layout setting finishing setting and the like of a single or combined job Move to Top for changing the print order of a given job to the top Move to Previous for changing the print order of a given job to an immediately preceding job Move to Next for changing the print order of a given job to an immediately succeeding job and Move to Last for changing the print order of a given job to the last.

When preview of a single or combined job is designated on the window of the spool file manager the previewer is loaded and instructed to perform preview processing for a job of an intermediate code described in the spool file .

The previewer sequentially reads out page drawing files PDF of intermediate codes included in the spool file processes the files in accordance with the contents of processing setting information included in a job setting file SDF stored in the spool file and outputs a GDI function to the graphic engine . The graphic engine outputs drawing data to the client area and then the data can be output on the screen.

The graphic engine can execute appropriate rendering in accordance with a designated output destination. From this similar to the despooler the previewer can be implemented by processing an intermediate code included in the spool file in accordance with the contents of processing settings included in the spool file and outputting the processed data by using the graphic engine . The processing settings set by the printer driver are stored as a job setting file in the spool file and data of a page drawing file is processed and output on the basis of the job setting file. The user can be provided with how to print actual drawing data and with a print preview close to a printer output in accordance with a case wherein N up printing processing of reducing and laying out N logic pages into one physical page and printing the physical page is designated a case wherein double side printing is designated a case wherein booklet printing is designated and a case wherein a stamp is designated. Note that the preview function of conventional application software such as document preparation software draws print data on the basis of the page settings of the application the print settings of the printer driver are not reflected and the user cannot recognize a preview of an actual printout.

By this preview processing a large preview of print processing settings included in the spool file are displayed on the screen by the previewer as shown in . The previewer is closed by a display stop instruction from the user and the control shifts to the window of the spool file manager.

If the user performs printing in accordance with the contents displayed by the previewer he she issues a print request by designating Print or Proof Print on the spool file manager . In accordance with the print request the despooler processes a page drawing file on the basis of a job setting file to generate a GDI function the GDI function is transmitted to the graphic engine and a print instruction is sent to the printer driver via the dispatcher to execute printing as described above.

In this manner when spool is designated in Edit and Preview settings generated print data is stored in the spooler in units of jobs. If a plurality of spooled print jobs are selected and Combine is designated for the selected jobs the spooler combines the selected print jobs into one job.

Processing after print data is spooled when job accounting is done in the spool system will be described with reference to .

If the event is a print instruction in step S the spool file manager advances to step S if NO to step S.

In step S the spool file manager activates the despooler and issues a print instruction. In this case the despooler functions as the application in . Authentication information is inquired in printing when a print request is issued to the printer driver via the dispatcher again. The subsequent processing is the same as in step S and subsequent steps in .

If the event is a job combination request in step S the spool file manager advances to step S if NO to step S.

In step S the spool file manager processes a plurality of selected jobs as a combined job. More specifically the single despooler issues a print request processing in step S for the spool file of these jobs at once.

Print data from the application is transferred to the spooler via the dispatcher . At this time no data is transmitted to the printer driver .

Even when a plurality of jobs are combined and printed as shown in authentication is requested for not each job before combination but one combined job.

The processing method of the spool system when the cancel button is clicked on the authentication information input window shown in similar to the operation described in the first embodiment will be explained with reference to . The processing procedures are almost the same as those in and shows only different procedures from those in .

More specifically processing in step S and subsequent steps in are different. In step S a print stop instruction in step S is sent to not the application but the despooler .

In step S the despooler notifies the spool file manager of the stop of printing and is unloaded from the internal memory.

In step S the spool file manager deletes the spool file generated by the spooler and is unloaded from the internal memory. As a result job accounting is performed without holding any spool file in the external memory even when the spool system is added to the job accounting system.

With these procedures the job accounting system of the second embodiment implements the following characteristic function in addition to functions 1 to 5 implemented by the system of the first embodiment.

 6 As for a print job obtained by combining a plurality of print jobs by combination operation authentication processing is performed once for the combined job as a single print job. This can realize simple user operation and fast printing.

The present invention may be applied to a system constituted by a plurality of devices host computer interface device reader printer and the like or an apparatus comprising a single device copying machine printer facsimile apparatus or the like .

The object of the present invention is also achieved when the computer or the CPU or MPU of a system or apparatus reads out and executes program codes stored in a storage medium which stores software program codes for realizing the functions of the above described embodiments i.e. the procedures in or .

In this case the program codes read out from the storage medium realize the functions of the above described embodiments and the storage medium which stores the program codes constitutes the present invention.

As a storage medium for supplying the program codes a floppy disk hard disk optical disk magnetooptical disk CD ROM CD R magnetic tape nonvolatile memory card ROM or the like can be used.

The functions of the above described embodiments are realized not only when the computer executes the readout program codes but also when the OS Operating System running on the computer performs part or all of actual processing on the basis of the instructions of the program codes.

The functions of the above described embodiments are also realized when the program codes read out from the storage medium are written in the memory of a function expansion board inserted into the computer or the memory of a function expansion unit connected to the computer and the CPU of the function expansion board or function expansion unit performs part or all of actual processing on the basis of the instructions of the program codes.

As has been described above the present invention can perform detailed counting processes coping with various print forms from applications and can accurately perform accounting or the like based on detailed information.

As many apparently widely different embodiments of the present invention can be made without departing from the spirit and scope thereof it is to be understood that the invention is not limited to the specific embodiments thereof except as defined in the appended claims.

