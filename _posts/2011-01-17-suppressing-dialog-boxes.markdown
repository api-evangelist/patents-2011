---

title: Suppressing dialog boxes
abstract: A method for browser software with a tabbed interface to suppress, or delay, the display of a dialog box that is initiated by an inactive, or background, tab. An indication may be provided to the user that a dialog box needing user attention may be provided. When that tab becomes active, and the web page on that tab becomes visible, the dialog box is then displayed. This suppression method may be applied to a variety of application programs.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09176646&OS=09176646&RS=09176646
owner: Microsoft Technology Licensing, LLC
number: 09176646
owner_city: Redmond
owner_country: US
publication_date: 20110117
---
This application is a continuation of and claims priority under 35 U.S.C. 120 to U.S. patent application Ser. No. 11 424 809 filed on Jun. 16 2006 and titled Suppressing Dialog Boxes the disclosure of which is incorporated by reference in its entirety herein.

This description relates generally to application programs and more specifically to browser software.

Browser application programs are often used to access information through the Internet or through company intranets. Users often have multiple pages displayed at any time. These pages may be from one web site or from multiple web sites. To facilitate switching between multiple pages tabbed browsers may be used.

Tabbed browsers generally allow programs on undisplayed web pages to continue processing while the tab holding that web page is inactive. This sometimes leads to items such as dialog boxes or other user interface elements to be presented to the user that are generated from web pages that are not currently being used thus interrupting the user from his or her browsing experience in the web page currently being viewed.

For example a page the user is not currently viewing may pop up a dialog box asking for a user name and password and the user may think the dialog box is from the currently active tab. This could lead to incorrect information being entered or worse a malicious site gaining access to valid username and password information for another site. Aside from those kinds of risks it typically leads to a poor user experience to have dialog boxes from inactive tabs displayed interrupting what the user is doing on the currently active and viewed web page. Alternatively a browser may switch tabs to one that is trying to display a dialog box. This may also lead to a poor user experience since the user may not notice that the active tab has changed.

The following presents a simplified summary of the disclosure in order to provide a basic understanding to the reader. This summary is not an extensive overview of the disclosure and it does not identify key critical elements of the invention or delineate the scope of the invention. Its sole purpose is to present some concepts disclosed herein in a simplified form as a prelude to the more detailed description that is presented later.

The present example may provide a way for browser software with a tabbed interface to suppress or delay the display of a dialog box that is initiated by an inactive or background tab. An indication may be provided to the user that a dialog box needing user attention may be provided. When that tab becomes active and the web page on that tab becomes visible the dialog box is then displayed. This suppression method may be applied to a variety of application programs.

Many of the attendant features may be more readily appreciated as the same becomes better understood by reference to the following detailed description considered in connection with the accompanying drawings.

First server computer may be coupled to wide area network which is conventionally constructed and may include the Internet or equivalent coupling methods for providing wide area networking. As shown wide area network is coupled to conventionally constructed second server computer . In this example second server computer is coupled to conventionally constructed computer over a conventionally constructed second local area network .

Local area networks and may include a plurality of conventional computers not shown and conventional peripheral equipment not shown coupled together utilizing topologies token ring star and the like and switching equipment known to those skilled in the art. Those skilled in the art may realize that other processor equipped devices such as televisions and VCRs with electronic program guides cellular telephones appliances and the like may be coupled to the networks utilizing conventional techniques known to those skilled in the art.

A typical local area network or may include a conventionally constructed ISP network in which a number or plurality of subscribers utilize telephone dial up ISDN DSL cellular telephone cable modem or the like connections to couple their computer to one or more server computers or that provide a connection to the wide area network via the Internet .

Client computers or may run a tabbed browser to access the Internet which may include a web page served by software running on second server computer . The web page may include script or other executable instructions that could cause a dialog box to be display on client computer . Those skilled in the art may realize that the computers may be any number of devices including a PC cell phone Internet appliance set top box hand held computers and the like.

Internet Browser without dialog box suppression may have a tabbed interface with multiple tabs. The example shows three tabs the currently active tab with the web page on the first tab having a title in its tab Title 1 displayed. The other tabs Tab and Tab are on web pages not currently visible having titles Title 2 and Title 3 in the tabs respectively. These pages could be viewed by clicking on the appropriate tab on the tabbed interface .

While the pages on inactive tabs and are not visible they may be continuing to execute any code such as initialization routines client side script and third party control executable code that are on those pages. In this example the page having tab has encountered code that has brought up a dialog box . This dialog box tends to pop up and distract the user. This can be confusing to the user since it may not be clear that the dialog box is not from the page he or she is currently viewing. It could also lead to security issues.

For example a page the user is not currently viewing may pop up a dialog box asking for a user name and password and the user may think the dialog box is from the currently active tab. This could lead to incorrect information being entered or worse a malicious site gaining access to valid username and password information for another site. Aside from those kinds of risks it typically leads to a poor user experience to have dialog boxes from inactive tabs displayed interrupting what the user is doing on the currently active and viewed web page.

Such a browser could be run on any number of different hardware and software platforms including but not limited to PCs cell phones Internet appliances set top boxes hand held computers etc.

The present example typically provides a way to prevent interruptions and provide a better user experience by tending to provide a way to suppress dialog boxes from web pages on inactive tabs until such time as those tabs become active or it is desired to access these pages.

Tab is displaying a web page on first tab with the title Title 1. Tabs and have web pages titled Title 2 and Title 3 respectively which are currently not visible. Any of the tabs could be activated causing the page loaded on that tab to be displayed by clicking on the appropriate tab in the tabbed interface . In order to suppress the dialog box as shown a method to suppress dialog boxes from view may be incorporated into the browser software. If Tab is clicked the suppressed dialog box would be displayed in the active window with the corresponding web page titled Title 3. 

Block dialog box suppression decision comprises several steps. First block intercepts the call to display the dialog box. Block determines if the dialog box should be displayed now. If the dialog box should be displayed now block may be executed and the dialog box is displayed.

If block determines that the dialog box should not be displayed now block is invoked suppressing the dialog box. Determining if the dialog box should or should not be displayed may be determined by examining the thread ID assigned to the tab in question and comparing it to known thread IDs. The known thread IDs may be maintained in a list table or their equivalent. Control may then be passed to block which may cue the user that a dialog box is waiting to be displayed. A cue may be made possibly by flashing the relevant tab from or other equivalent methods. One skilled in the art may recognize that other types of cues could be used indicate the suppressed dialog box including other visual displays or sounds such as audible beeps signals from other devices such as a Bluetooth enabled phone or combinations of various indicators or the like.

An example of determining where the call to display the dialog box came from involves using multiple threads within the browser. In such a case each tab would be given a thread as well as the browser or frame having one. The primary indicator may be the Thread ID of the thread that is attempting to show the dialog which can be compared against the known Thread IDs of the tabs and top level window . In addition to threads other indicators may include context such as the window handle being used to parent the dialog or a token previously assigned to the tab and passed along as context. These indicators may be used independently or in conjunction with threads or each other. The outcome of this evaluation may be Background Tab Active Tab Frame or Browser or Unknown Source.

If the source of the dialog is found to be a Background Tab then the dialog may be queued by adding it to an internal list along with an event for that dialog. After the dialog is queued the source s thread may be blocked waiting for the event to get signaled. The wait may use a modal message loop which is a method of blocking the thread while still processing a minimal set of Windows messages so that the UI thread is not completely hung which could hang the entire application.

Next a message may be sent to the Tab Band signaling a dialog was suppressed. The Tab Band may respond by blinking the correct tab. When a tab is selected to make it active the list may be checked to see if any dialogs have been suppressed from that tab. If so the event to unblock the thread may be signaled allowing the dialog to be shown and then removed from the list.

If the source of the dialog is found to be an Unknown Source meaning that the application is unable to associate the caller with any known tab the dialog may be shown or blocked entirely based on the security risk of showing that dialog on top of the wrong tab. For example if it is a script initiated dialog from a web page it would be blocked to mitigate UI spoofing attacks but if it is a dialog from an add on within the application it would be allowed.

If the source of the dialog is found to be the Active Tab Thread or Frame Thread then the dialog may be shown right away.

One way to intercept the call to the display dialog box is to capture the call directly. For example if a web page uses script to call an API within a browser to display a dialog box the browser can directly examine the information in the call to the API to determine the source. Another way is to hook operating system APIs for showing dialogs capturing any calls to the API and determine the caller before passing the call on to the original operating system routine.

A peripheral drive may accept a computer readable media that includes a copy of the method to suppress dialog boxes from background tabs. The peripheral drive may be coupled to an I O interface along with an I O device .

The I O interface may be coupled to a bus structure which also may couple to a hard disk a processor system memory a video adapter and a network adapter .

Video adapter typically couples a display to the CPU . Network adapter typically couples a local area network to the CPU .

For example the computer can be implemented with numerous other general purpose or special purpose computing system configurations. Examples of well known computing systems may include but are not limited to personal computers hand held or laptop devices microprocessor based systems multiprocessor systems set top boxes gaming consoles consumer electronics cellular telephones PDAs and the like.

The computer includes a general purpose computing system in the form of a CPU display I O device and peripheral drive . The CPU can include one or more processors including CPUs GPUs microprocessors and the like a conventional system memory and a conventional system bus that couples the various system components. Processor processes various computer executable instructions including those to control the operation of computing device and allows communication with other electronic and computing devices not shown . The system bus represents any number of several types of bus structures including a memory bus or memory controller a peripheral bus an accelerated graphics port and a processor or local bus using any of a variety of bus architectures.

The system memory may include computer readable media in the form of volatile memory such as random access memory RAM and or non volatile memory such as read only memory ROM . A basic input output system BIOS is typically stored in ROM. RAM typically contains data and or program modules that are immediately accessible to and or presently operated on by one or more of the processors . Computing device may include other removable non removable volatile non volatile computer storage media.

A hard disk drive is also a type of computer readable media that may read from and write to a non removable non volatile magnetic media not shown . Such a hard disk may include a magnetic disk drive which reads from and writes to a removable non volatile magnetic disk e.g. a floppy disk or an optical disk drive that reads from and or writes to a removable non volatile optical disk such as a CD ROM or the like. In this example the hard disk drive and disk drive are each connected to the system bus by one or more data media interfaces . The disk drives and associated computer readable media provide non volatile storage of computer readable instructions data structures program modules and other data for computing device .

Mass storage devices or peripheral drive are also a type of computer readable media that may be coupled to the computing device or incorporated into the computing device by coupling to the bus . Such peripheral drive may include a magnetic disk drive which reads from and writes to a removable non volatile magnetic disk e.g. a floppy disk or an optical disk drive that reads from and or writes to a removable non volatile optical disk such as a CD ROM or the like . This mass storage device may be representative of those storing the image or those being backed up.

In the example described above the plurality of backups and process for restoring backups of restore OS of may be disposed on the hard disk or the system memory . Computer readable media CRM typically embody computer readable instructions data structures program modules and the like supplied on floppy disks CDs portable memory sticks and the like. Such CRM may be used to produce an initialization disk.

Any number of program modules or processes can be stored on the hard disk or peripheral drive including by way of example backup files an operating system one or more application programs other program modules and program data. Each of such operating system application programs other program modules and program data or some combination thereof may include an embodiment of the systems and methods described herein.

A display device can be connected to the system bus via an interface such as a video adapter . A user can interface with the CPU via any number of different input devices such as a keyboard pointing device joystick game pad serial port and or the like. These and other input devices are connected to the processors via input output interfaces that are coupled to the system bus but may be connected by other interface and bus structures such as a parallel port game port and or a universal serial bus USB .

Computer can operate in a networked environment using connections to one or more remote computers through one or more local area networks LANs wide area networks WANs and the like. The computer is connected to a network via a network adapter or alternatively by a modem DSL ISDN interface or the like.

The browser with method to suppress dialog boxes from background tabs may be disposed on Hard Disk or on computer readable media disposed on Peripheral Drive or the like. Browser could also be disposed in System Memory or any other type of computer readable media.

The context of the dialog may be inspected to determine the source of the call. This may be done by comparing the thread ID to known thread IDs by comparing the window handle to known window handles or an equivalent method. If it is determined that it is an active tab the dialog box may be displayed . Otherwise if it is a background tab the dialog box may be queued in a pending list . The thread for that dialog may then be paused via a modal message loop until an event is triggered . When the event is triggered then the dialog may be shown . If the context is not a background tab the source may be unknown . If the dialog is allowed from unknown sources the dialog box may be displayed . Otherwise the dialog may be blocked .

