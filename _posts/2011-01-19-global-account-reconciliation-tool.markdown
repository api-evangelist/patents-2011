---

title: Global account reconciliation tool
abstract: A global reconciliation software tool is provided to standardize reconciliation processes across various corporate lines of business. The reconciliation tool provides standard templates for entering transaction and account data. In this manner, open accounting items are more readily identified and reconciled. The software tool includes a plurality of components allowing for greater scalability and operability across various computer systems and accounting programs.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08150746&OS=08150746&RS=08150746
owner: American Express Travel Related Services Company, Inc.
number: 08150746
owner_city: New York
owner_country: US
publication_date: 20110119
---
This application is a continuation of claims priority to and the benefit of U.S. Ser. No. 10 736 181 filed Dec. 15 2003 now U.S. Pat. No. 7 895 094 and entitled Global Account Reconciliation Tool which is hereby incorporated by reference.

This invention generally relates to financial data processing and in particular it relates to the reconciliation of financial accounts and transactions.

Reconciliation is a common financial process by which debit and credit transactions are matched for a plurality of accounts. Typically any unmatched or open transactions are researched and cleared by marking them for write off and the like in corporate reconciliation processes.

In large corporate organization having many lines of business it is common for various departments to have adopted different computer accounting systems. Such accounting systems may differ in the computer operating system OS that is used and or in the software applications that are employed.

While this does not pose a hardship for an individual department in reconciling its transactions internally it frequently hampers reconciliations between departments having different accounting systems and likewise for a corporate entity as a whole. One reason for this is because input financial data must be converted between the different data formats. Frequently such conversions lead to further human or computer errors which tend to increase un reconciled transaction amounts. Also a larger number of databases need to be used in corporations with disparate accounting systems thus adding to the complexity of the task as well as the time it takes to complete reconciliations.

Another challenge faced with the multiple sources and formats of data is the difficulty in reconciling this data. Defining business rules logic for allowing the system to automatch the data also becomes difficult. This leads to manual matching reconciliation of data which in turn causes further human errors and unmatched unreconciled data. The burden of research and clearance increases with an increase in the volume of unreconciled data.

Replacing every accounting system in every department with a system of the same format would solve these recurring problems. However particularly with respect to large corporations this solution would entail extreme financial burdens. In addition it may not be possible to find one available software solution that can be implemented within every department.

Accordingly there is a need for a global reconciliation tool that addresses certain problems in existing technologies.

It is an object of the present disclosure therefore to introduce a globally deployable financial reconciliation tool for reconciling debit and credit transactions and improving Balance Sheet hygiene. The tool includes standardized templates for entering financial data. The standardized templates are operable on a plurality of operating systems and or may interface with a plurality of accounting software applications. The capture functionality ensures flexibility to accept any input format of data. The tool also provides a plurality of functions for generating customized templates that may be used by individual corporate departments. The standardized templates and template generating functions are then distributed to a plurality of remote terminals across all departments within a corporation.

All transaction and account data are captured and stored in one or more master financial databases. The captured financial data is then reconciled with the master financial data. Reconciliation of data is performed within the tool by an auto match functionality defining business rules to auto match data or by manual reconciliations. The user defined business rules can be reused for auto matching across a plurality of data and accounts which leads to higher auto match by the tool and the need to manual reconciliation decreases. This ensures lesser manual errors and improved Balance Sheet hygiene. Any un reconciled amounts are identified and the tool may generate reports of all reconciled and un reconciled transactions. The tool may also be used to update corporate balance sheets and the like based on the reconciled and unreconciled data.

In certain embodiments the reconciliation tool has a component based architecture in which each component implements a particular set of functions for accomplishing reconciliations. Such components may include a master component for storing master financial data for a plurality of accounts a capture component for receiving and storing account and transaction data from a plurality of remote terminals a matching component for matching the account and transaction data with the master financial data either auto match creating business rules for auto match or manual reconciliations a clearance component for identifying reconciled and un reconciled accounts or transactions and an account component for updating account information and reporting reconciled and un reconciled data.

Referring now to wherein similar components of the present disclosure are referenced in like manner various embodiments of a global reconciliation tool will now be described in detail.

The global reconciliation tool was developed to address the problem of reconciliations being performed among various corporate departments using disparate computer accounting systems. Typically responses to various technology implementation requests from these departments would have resulted in numerous disparate enhancements to each of the departments systems thus forcing the systems to evolve in increasingly different directions. This in turn would lead to further complications in handling reconciliations among the departments.

However by applying the Integrated Technology Quality Model developed by the assignee of the present application the present global reconciliation tool has been developed and implemented as a corporate wide solution. ITQM is described in detail in co pending U.S. patent application Ser. No. 10 682 705 entitled Integrated Technology Quality Model filed in the name of Huang et al. In accordance with ITQM the global reconciliation tool provides a component based architecture that supports the general principles of enhanced revenue generation technology consumption management and optimization of technology investments.

The global reconciliation tool is a scalable flexible globally deployable reconciliation preparation and reporting system. Its multi tier component based architecture provides scalability to accommodate large volumes of financial data and flexibility to adapt to changing business needs. It ensures financial control in business areas by capturing the financial transactions at a common place and reconciling and scrutinizing the transactions being captured. It enables rapid identification and reporting of any imbalance or un reconciled data that may expose the business to undue financial losses. It also enables stronger balance sheet updating and reporting.

In various embodiments the global reconciliation tool provides a plurality of standardized templates for entering transactional and account data. When developed appropriately the standardized templates provide a standardized means for entering and submitting such financial information in format that complies with a corporation s general reconciliation policy in place of or in conjunction with each department s data format required by their individual computer accounting system. These implementations in turn reduce the need for manual intervention in data input and review thus enhancing corporate control of multi department reconciliations.

The solution is designed in a very generic manner so that it can be deployed in any business area requiring reconciliation processes. The global reconciliation tool is operable on all popular computer operating system and thus facilitates moving and consolidating account data from existing disparate formats such as NCR MICROSOFT EXCEL and MICROSOFT ACCESS to a single common platform without requiring additional hardware replacement. The global reconciliation tool may serve as a replacement for departmental accounting software or may be developed to interface directly with a variety of accounting systems to convert financial data to a standard format. Thus reconciliation preparation and reporting processes may be readily accommodated across various lines of business while minimizing technology replacement costs.

Flexible reporting capabilities provided by the global reconciliation tool reduces reconciliation turn around time thereby also lowering costs associated with this business process. It provides automated global transaction search and match capabilities in addition to manual matching capabilities resulting in faster research and clearance of open items.

As a result of the foregoing it should be readily appreciated that the global reconciliation tool is a cost effective solution for upgrading corporate accounting software architecture and providing other accounting system enhancements.

Turning now to there is depicted an exemplary embodiment of a computer network through which the global reconciliation tool may be deployed and implemented. The exemplary computer network may include the following components.

A accounting server may be provided for deploying or hosting the global reconciliation tool across the network . The server may store and process the various components of a global reconciliation tool as described below with respect to and

The server may be any enterprise server or group of servers of the type manufactured by IBM SUN and the like. The accounting server may also cooperate with one or more other servers to accomplish the functionality described herein.

For example one or more database servers may be provided to store master financial data in one or more databases . The master financial data may thus be captured and recorded in any location for a large corporate entity. However the master data may also be mirrored or otherwise maintained among several distributed databases and servers where desirable.

The accounting server may also operate in conjunction with a backup server that archives critical data and programming and with a file and print server that allows output of a variety of electronic or printed accounting reports.

The network may also include one or more network gateways for allowing communications between the servers and a plurality of remote terminals . The communication may be performed over a secure communications layer to ensure security and prevent unauthorized access to financial data. The remote terminals may be geographically or globally dispersed and may operate as interface points with various corporate departments. The remote terminals may also include point of sale terminals that conduct financial transactions. The remote terminals may be operated by any corporate personnel including authorized corporate users and administrators who may enter transaction data to the system or receive reports therefrom.

The computer network may be implemented in any useful configuration and is not limited to that configuration shown in .

Turning now to and there is depicted various exemplary software components of a global reconciliation tool . As described above the tool includes various OS independent software components for accomplishing the functions described herein. Accordingly in certain embodiments the various components of the global reconciliation tool may be implemented as ENTERPRISE JAVABEAN EJB components that allow the tool to be interoperable on every OS and within any application environment. This is because JAVABEAN architecture connects via bridges into other widely used computer component models such as ACTIVE X. The JAVABEAN specification defines a set of standard component software application programming interfaces APIs for the JAVA platform. Software components that use JAVABEAN APIs are thus compatible with a variety of containers including but not limited to INTERNET EXPLORER VISUAL BASIC MICROSOFT WORD LOTUS NOTES. Formats other than JAVA which are similarly OS and application independent may also be used.

One embodiment of a global reconciliation tool implemented as EJB components is shown in and . In such an embodiment the global reconciliation tool may include the following exemplary components.

A base session component may be provided to coordinate computing sessions and data transfers among the plurality of components described herein. The base session component may be implemented as a series of computer controlled session initiation and maintenance processes.

A login component may be provided to receive and validate authorized user login and password data to allow access to stored financial data.

A template component may be provided to provide a plurality of standardized templates to the remote terminals . The standardized templates may provide various fields for entering financial transaction and account data that may be captured and stored for later reconciliation at the accounting server . These templates are re usable and assist in extracting relevant data from various remote files.

The template component may also provide a plurality of functions that allow individual departments to generate department specific or other customized templates for entering such data. The fields in such customized templates may be implemented such that they correspond to standard corporate transaction data types.

An capture review component may be provided to review transaction data captured from various remote terminals and to immediately identify any errors therein. Such errors may include un reconcilable transaction amounts or the like. Errors may thus be immediately reported to appropriate remote terminals to avoid later reconciliation errors. This component may be provided with various functions for capturing financial data transmitted by various remote terminals . This component offers flexibility to accommodate capture of data from standardized templates and also facilitates customized templates for different types of files. This component also facilitates scheduling capture activities using templates including the sequencing of capture as well as capturing data manually.

A user maintenance component may be provided to maintain add modify or delete authorized users or user information of authorized users that may access the global reconciliation tool .

A matching component may be provided for matching reconciling the data being captured in the system. This component facilitates both manual and scheduled reconciliations. Scheduled reconciliation can be performed either using the pre defined rules or by customized rules that may be defined by an authorized user.

A research and clearance component may be provided with various functions for tracing the details of open un reconciled items and facilitates generating clearing entries for those open items.

A master reference data component may be for assembling and maintaining master financial data for a plurality of accounts.

An account reporting component may be provided for publishing reconciliation activities in any desired manner. It may generate a set of predefined reports as an output of the data captured and reconciled within the system. Authorized users may be provided with further functions for designing customized reports for reporting the available data.

Turning now to there is depicted an exemplary reconciliation process performed by the accounting server in conjunction with the global reconciliation software tool .

The process includes transmitting a plurality of standardized templates and tools for generating customized templates to remote terminals step . The remote terminals in turn transmit financial transaction data for one or more accounts back to the accounting server step . The financial data received either on a scheduled basis or upon each transaction or by manual implementation from the remote terminals is reconciled with stored master financial data step . Any un reconciled amounts are identified step and are reported in a desired output format step . Un reconciled transactions may then be researched and or written off and corporate balance sheets and other accounting reports may be automatically updated step . The process may be repeated in various sessions on a recurring basis with a variety of remote terminals during the continuing operation of a business entity.

Although the best methodologies of the invention have been particularly described in the foregoing disclosure it is to be understood that such descriptions have been provided for purposes of illustration only and that other variations both in form and in detail can be made thereupon by those skilled in the art without departing from the spirit and scope of the present invention which is defined first and foremost by the appended claims.

