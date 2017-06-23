---

title: System and method for a computerized learning system
abstract: There is a computerized learning system and method which updates a conditional estimate of a user signal representing a characteristic of a user based on observations including observations of user behavior. The conditional estimate may be updated using a non-linear filter. Learning tools may be generated using the computerized learning system based on distributions of desired characteristics of the learning tools. The learning tools may include educational items and assessment items. The learning tools may be requested by a user or automatically generated based on estimates of the user's characteristics. Permissions may be associated with the learning tools which may only allow delegation of permissions to other users of lower levels. The learning system includes a method for annotating learning tools and publishing those annotations. In-line text editors of scientific text allow users to edit and revised previously published documents.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08761658&OS=08761658&RS=08761658
owner: FastTrack Technologies Inc.
number: 08761658
owner_city: Edmonton
owner_country: CA
publication_date: 20110131
---
This patent document relates to managing information within an electronic learning system. In particular this patent document relates to generating learning tools and estimating characteristics of users and learning tools within an electronic learning system.

Increasingly more and more tests are being administered using electronic resources. Students may take examinations through online testing systems which may provide adaptive testing.

In one system U.S. Pat. No. 7 628 614 describes a method for estimating examinee attribute parameters in cognitive diagnosis models. The patent describes estimating for each assessment one or more item parameters and also describes tracking item responses by considering various examinee parameters. Although many systems determine a user s responses to an examination question item those systems do not consider user behavior that may be related to the user s responses within the examination or more importantly user s proficiency. By focusing on solely examination question item response data those systems fail to consider the wealth of information that may be collected within a computerized learning system.

Many assessment systems only track the ability of the user and neither consider nor attempt to improve the performance of the students. These systems also fail to recognize the potential uses for the vast amount of information that may be detected while a user accesses a learning system. Moreover some current methods of interpreting data are unable to cope with the high volume and plethora in types of traffic information that potentially may be collected during an educational or assessment session. Large amounts of data and types of activity traffic may prove to be difficult to effectively model and process in order to discover useful information. Many assessment systems therefore only track data associated with user s responses during examination.

Also it may be difficult and time consuming for instructors to create new examinations and furthermore prepare students by creating additional practice examinations. Traditional methods involve picking questions from a textbook or from past exam in an attempt to make a mock exams and even the examination themselves. Such methods are not only onerous to instructors but more importantly especially in a multi section course setup can lead to a bias in picking questions similar to an already known final in their instruction or mock exams. Some basic methods have been developed by other to generate random problem sets i.e. different questions but such methods are too primitive for actual use in creating a well balance exam in terms of distribution of difficulty and variety of questions contained thus have only be used in low stakes homework. Furthermore full solutions are almost never provided only the final solution. The lack of a method for simulation exam questions with full solution is detrimental in helping students prepare and study in an effective and smarter manner.

In any sizeable group of students typically students will struggle in different study areas or be at different proficiency levels for the same learning objective. An instructor will typically tailor instruction to the average student group leaving weaker students frustrated and lost and stronger students unchallenged. The traditional education system fails to tailor education items and examination items for the needs of each individual student.

Traditionally courses are designed by professors with experience on what topics must be covered during a semester and in what proportions. Information about student progress can only be found during examinations and in traditional systems this information is not easily presented and cannot be used to determine the effectiveness and quality of specific learning resources courseware textbooks activities and schedule.

In an embodiment there is method for updating and using a conditional estimate of a signal in a computerized learning system. Observations of user behavior are obtained through user interaction with the computerized learning system. A conditional estimate of a user signal representing a characteristic of a user is updated based on the observations. The conditional estimate of the signal is used to generate at least a learning tool and a report.

In an embodiment there is a method for updating and using a conditional estimate of a signal in a computerized learning system. Observations are obtained through user interaction with the computerized learning system. A conditional estimate of a signal representing a characteristic of a learning tool and a characteristic of a user is updated based on the observations using a non linear filter. The conditional estimate of the signal is used to generate at least one of the following the or a second learning tool and a report.

In an embodiment there is a method of storing data in a computer database. A plurality of learning objectives associated with at least one of a user and a learning tool is stored. For each learning objective a probabilistic distribution representing a characteristic rating for the learning objective is assigned.

In an embodiment there is a method of generating learning tools within a computerized learning system. A plurality of learning tools is stored within a database each one of the plurality of learning tools is associated with a plurality of characteristics. A request in the form of a distribution of desired characteristics is received. A subset of the plurality of learning tools having a plurality of characteristics satisfying the requested distribution of desired characteristics is generated.

In an embodiment there is a method of a generating learning tool for a user within a computerized learning system. A request for a learning tool satisfying a distribution of desired characteristics is submitted. A learning tool is received from a server the learning tool satisfying a distribution of desired characteristics for the learning tool.

In an embodiment there is a method for assigning rights associated with learning tools in a computerized learning system. For an action corresponding to a learning tool associated with a user a permission object is assigned. The permission object is capable of being assigned each one of the following permissions a super grant permission wherein the user is capable of performing the action and the user is capable of delegating any level of permission related to the action to a subsequent user a grant permission wherein the user is capable of performing the action and the user is capable of delegating a yes permission related to the action to the subsequent user the yes permission wherein the user is capable of performing the action and the user is unable to delegate any level of permission and a no permission wherein the user cannot perform the action and the user is unable to delegate any level of permission.

In an embodiment there is a computer program product comprising a non transitive computer readable medium having encoded thereon computer executable instructions for implementing the methods described herein.

In an embodiment there is a method of adapting an educational and assessment system for a user. Educational items and assessment items are stored in a database. The following is repeated for a plurality of users a plurality of assessment items and a plurality of educational items a updating a characteristic of a user of the plurality of users and a characteristic of an assessment item of the plurality of assessment items based on interaction between the user and assessment item b and updating the characteristic of the user of a plurality of users and a characteristic of a first educational item based on interaction between the user and the first educational item. At least one of an educational item of the plurality of educational items an assessment item of the plurality of assessment items is presented to a selected user of the plurality of users to generate a desired effect on the user based on the characteristic of the user.

In an embodiment there is a method of integrating scientific symbols in line with text in content within a computerized learning system. The method switches from text mode into scientific mode. Plain language text input is converted into scientific code. A graphical representation of the scientific code is displayed in line with the text. The plain language text input is adaptively predicted using context based prediction.

In an embodiment there is a method for annotating learning tools within a computerized learning system. A first user s annotation of a learning tool is stored in the computerized learning system the learning tool having a plurality of characteristic. At least a second user of a plurality of users is permitted to have access to the annotated learning tool. A learning tool object corresponding to the annotated learning tool is created the annotated learning tool having a plurality of characteristics. A subset of the plurality of characteristics of the annotated learning tool is set to be the same as the plurality of characteristics of the learning tool.

These and other aspects of the device and method are set out in the claims which are incorporated here by reference.

As shown in there is a method for updating and using a conditional estimate of a signal in a computerized learning system. Observations of user behavior are obtained through user interaction with the computerized learning system. A conditional estimate of a user signal representing a characteristic of a user is updated based on the observations. The conditional estimate of the signal is used to generate at least a learning tool and a report .

In an embodiment of the method the observations that are obtained through user interaction with the computerized learning system also include answers given by user in response to assessment items. The conditional estimate of the signal may represent both a characteristic of a learning tool and a characteristic of a user and the conditional estimate may be updated based on the observations using a non linear filter.

As shown in there is a method of storing data in a computer database . A plurality of learning objectives associated with at least one of a user and a learning tool is stored . For each learning objective a probabilistic distribution representing a characteristic rating for the learning objective is assigned .

As shown in there is a method of generating learning tools within a computerized learning system. A plurality of learning tools is stored within a database each one of the plurality of learning tools is associated with a plurality of characteristics. A request in the form of a distribution of desired characteristics is received. A subset of the plurality of learning tools having a plurality of characteristics satisfying the requested distribution of desired characteristics is generated .

As shown in there is a method of generating learning tools for a user within a computerized learning system. A request for a learning tool satisfying a distribution of desired characteristics is submitted. The learning tool is received from a server the learning tool satisfies a distribution of desired characteristics for the learning tool.

As shown in there is a method for assigning rights associated with learning tools in a computerized learning system. For an action corresponding to a learning tool associated with a user a permission object is assigned . The permission object is capable of being assigned each one of the following permissions at a super grant permission wherein the user is capable of performing the action and the user is capable of delegating any level of permission related to the action to a subsequent user a grant permission wherein the user is capable of performing the action and the user is capable of delegating a yes permission related to the action to the subsequent user the yes permission wherein the user is capable of performing the action and the user is unable to delegate any level of permission to the subsequent user and a no permission wherein the user cannot perform the action and the user is unable to delegate any level of permission to the subsequent user.

As shown in there is a method for adapting an educational and assessment system for a user. Educational items and assessment items are stored in a database . Repeating the following for a plurality of users a plurality of assessment items and a plurality of educational items a updating a characteristic of a user of the plurality of users and updating a characteristic of an assessment item of the plurality of assessment items based on interaction between the user and assessment item and b updating the characteristic of the user of a plurality of users and updating a characteristic of a first educational item based on interaction between the user and the first educational item. At least one of an educational item of the plurality of educational items an assessment item of the plurality of assessment items is presented to a selected user of the plurality of users to generate a desired effect on the user based on the characteristic of the user.

In there is a method of integrating scientific symbols in line with text in content within a computerized learning system. The method switches from text mode into scientific mode. Plain language text input is converted into scientific code. A graphical representation of the scientific code is displayed in line with the text. The plain language text input is adaptively predicted using context based prediction.

In there is a method for annotating learning tools within a computerized learning system. A first user s annotation of a learning tool is stored in the computerized learning system the learning tool having a plurality of characteristics. At least a second user of a plurality of users is permitted to have access to the annotated learning tool. A learning tool object corresponding to the annotated learning tool is created the annotated learning tool having a plurality of characteristics. A subset of the plurality of characteristics of the annotated learning tool is set to be the same as the plurality of characteristics of the learning tool.

In an embodiment there is a computer program product comprising a non transitive computer readable medium having encoded thereon computer executable instructions for implementing the methods described herein.

For ease of explanation consistent notations and symbols will be used to describe the system and method. The various notations and symbols used to describe the system are exemplary only and are intended to assist the reader in understanding the system and method.

Objects The notation used to describe data structure objects is presented in an object oriented format. A data structure object type will be labeled by a symbol where a symbol is either one or more italicized letters of the English or Greek alphabet. For the ease of recognition and meaning these symbols may be denoted as underscored or italicized words.

Time The italicized letter t will be reserved to indicate time which may further be indexed e.g. twhere k 0 1 2 . . . K and will be used to reference an instance of an object at a point in time using subscript notation e.g. object X at time t is denoted by X .

Collections Superscript position on an object will be reserved for indexing objects within a collection or set of objects of the same type. For example Xreferences the ith object in a collection Xat time t i.e. X Xwhere 1 i N .

Fields These data structure objects may have data member fields which are either references to instances of other object types a single numerical value an n dimensional array of numerical values or an n dimensional array of references to instances of other object types.

A particular field for an object will be labeled by the symbol where subscript i denotes the ith field for the object followed by either a single or n element list enclosed in round brackets.

For both a single and n element list the first element will denote the data structure object that the member data field belongs to whereas for the n element lists the remaining n 1 element s will indicate n 1 dimensional array indices. For example X means that the 2field for object X is a real numbered value and X l 4 23 0 1 2 . . . N means that the 6field for object X at array position l 4 23 is an integer value from zero to N.

User means any arbitrary individual or group who has access to the computerized learning system. For example a user may be

An individual may be a member of more than one of the user types listed above. For example a student learner may also be an author if the student publishes annotations relating to course material. Similarly an instructor in one course may be a learner in a different course.

A learning objective is a characteristic of a learning tool that represents an objective that an education tool is intended to achieve or which an assessment tool is intended to test. The learning objective may be specific such as testing a user s ability to answer a specific question or may be general such as describing a subject area which an educational item is intended to teach. For example the learning object may include the content relating to an assessment question. The activity refers to the type of activity associated with the learning tool. Using mathematics as an example a question may require a student to prove a statement provide a counter example solve for an equation or variable or perform some other activity which serves to test a user s understanding of mathematics.

We denote learning objective L L where 1 l L . In an embodiment each learning objective object Lhas the following attribute fields 

Learning tools or learning resources are content items within a computerized learning system which can be accessed by users to facilitate learning or to provide assessment. Learning tools may be provided to a consumer user directly through the system or via a link. Examples of learning tools include educational items such as eBooks readings audible lectures interactive examples follow up training sessions virtual tutoring sessions and assessment items such as assignments examinations laboratories and exercises.

Learning tools may be associated with one or more characteristics. Characteristics of a learning tool may include attributes of the learning tools such as the learning objectives the learning style the difficulty the effectiveness the motivation rating the popularity the format availability the time associated with and the type of the learning tool. The quality of a learning tool may include a variety of different types of quality ratings. The quality of the learning tool may be determined by the effectiveness of the learning tool to produce an improvement in a learner s proficiency from one level to a higher level. Quality may also be determined based on the clarity of communication within the learning tool. Quality may also be determined based on the teaching quality of the learning tool in producing a desired teaching result. Motivation includes the ability of a learning tool to motivate a user to learn material or respond to an assessment. For example a short educational video clip may improve a user s motivation in a subject area whereas a lengthy and complicated reading passage may correspond to a low motivation level. The popularity of a learning tool may be determined based on a user response to the learning tool. The format availability of a learning tool may include tools to enable auditory visual or tactile interaction with the learning tool for example to assist users with disabilities. The total time associated with the learning tool is a measure of the length of time a user is expected to require to consume an educational item or to complete an assessment item. The system may also provide scheduling related information for the learning tool for example including the time the learning tool is made available to a user and the amount of time a user has to consume the resource.

The resource type may be any type of resource which may provide educational to or assessment of a user such as eBooks audible lectures interactive lectures training sessions virtual tutoring homework assignments full solution to assessment items lecture notes algorithmic templated questions or exercises accessible for visually impaired for example with WAI ARIA 1.0 standards for screen readers courseware Learning Objective Map or Course Blueprints Questions Homework assignments Exams lab work eWorksheets algorithmic template SmartPlot Questions include graphics. The types of learning tools may include as subsets learning tools of a different type. For example a course blueprint learning tool may include various other learning tools such as homework assignments examinations lectures and training sessions.

A learning tool may be formed as a collection of various learning tools. The base atom or smallest indivisible unit is a paragraph. For example a course eBook may be formed from a collection of chapters each of which is formed from a collection of topics and each topic may be formed from a variety of paragraphs. Although smaller divisions than paragraphs may be possible it becomes increasingly difficult to determine a learning objective related to learning tools divided beyond a paragraph. By allowing learning tools to be made up of a series of nested resources the computerized learning system can provide a large number of permutations for content items. For example eBooks which cover similar topic areas may nonetheless include a great variety in terms of specific paragraphs or paragraph orders within the books. For example a professor may wish to use a course content item for a class that contains topics in various different areas and then generate course content items with different formats based on the motivation of individual students while teaching the same overall content.

An exemplary list of characteristics for learning tools is set out in Table 2. In some embodiments the computerized learning system may track one or more of the characteristics set out in Table 2.

In an embodiment we denote resources by R R where 1 r R . In an embodiment each resource Rhas the following attribute fields 

In an embodiment we define courseware as a scheduled resource which has within its R segments a variety of resource types. I.e. The kth segment R k R can be scheduled eBook readings activities audible lecture activities weekly homework labs and quizzes midterm exams and final.

In general the user is modeled as a collection of characteristics or attributes associated with a user. Features of users such as a user s level of LO proficiency mastery interpersonal skills e.g. teaching quality motivation and learning style learning type preference may all be modeled within the system. A user may be described using one or more of characteristics mentioned in Table 3.

Through interaction with the learning system a user may request the system to produce a learning tool with specific characteristics. The request may take the form of a distribution of desired characteristics of a learning tool. After the request for a distribution of desired characteristics is received by a database a subset of the learning tools in the database having a plurality of characteristics satisfying the requested distribution of desired characteristics is generated. The request may be coded within the system as a request object.

In general a user may create a request object via a command line or graphical interface or upload a request object file. A resource generation request object describes the characteristics of the user s ideal resource.

In another embodiment the system itself may create these request objects based on some action strategy see section ACTION STRATEGY below . For example if a student shows deficiency in certain subject matter areas the system may generate a request for remedial learning tools to be generated for the user. The system may create these request objects based on estimates of the characteristics of a user. For example a learning tool may be generated based on an updated conditional estimate of a user signal representing a characteristic of the user and a characteristic of a learning tool. This estimation process is described in more detail in the section ESTIMATION PROBLEM. Once the subset of the plurality of learning tools is generated it may be transmitted to at least one user such as a student who requested a learning tool.

The system stores characteristics of a request object corresponding to the characteristics of learning tools stored in the system. Characteristics of a request object may include one or more of the following characteristics the learning objective the learning style the difficulty the effectiveness the motivation rating the popularity the format availability the time and the type of the request object. Additional characteristics of request objects such as locked objects and black listed objects may also be recorded. A locked request object is a request object which specifies a fixed learning tool to be generated each time a particular set of learning tools is generated. For example if a high stakes examination is requested then the teacher user may desire certain questions within the examination to be the same for each student that writes the examination. In the context of an assessment that is not high stakes a professor may wish to generate subsets of the plurality of learning tools for each of the plurality of tools that are unique for example to gather data about questions to be asked in future courses or in order to prevent cheating. If the teacher user dislikes questions within the system the teacher user may blacklist a question in order that it does not appear on any examination produced for the students within that teacher user s course. This type of locking and blacklisting may be performed for any of the types of request objects.

The requested learning tool type may correspond to any type of learning tool within the system including eBooks audible lectures interactive lectures training sessions virtual tutoring homework assignments full solution to assessment items lecture notes algorithmic templated questions or exercises accessible for visually impaired for example with WAI ARIA 1.0 standards for screen readers courseware Learning Objective Map or Course Blueprints Questions Homework assignments Exams lab work eWorksheets algorithmic template SmartPlot Questions include graphics.

Templated questions are questions in which the parameters within the question may be stored as variables. For example in a reading question a single passage may include a character whose name is randomly generated for each examination and the answer key will also be updated with the same name. This may reduce cheating because the answer to a question such as who is the main character may result in a different correct answer for each test even though the knowledge being tested is the same. This principle can be used in mathematics where terms may be randomly generated with resulting solutions that test the underlying understanding of the user but may appear on its surface thereby reducing the potential for cheating. Templated questions may be treated as having the same characteristics since the variables within the question should not change the type or difficulty of the question.

The objects may be requested by different users. As described in the example of a teacher user requesting an examination teacher users may generate assessment items. Similarly a teacher user may request a complete coursepack based on a set of requirements determined through selection. A student user may also generate learning tools through a request object such as practice problems or lectures to assist with learning. The system may automatically generate learning tools based on a conditional estimate of the user s characteristics such as proficiency or learning style. For example if a user is poor in a subject area such as fractions then the system may generate practice problems that include a higher distribution of fractions than other subject areas where the user may be more proficient. Similarly the practice problems may be easier for areas where the user is deficient. This adaptivity allows content to be generated to suit the particular student s needs.

Once requested a learning tool which conforms to the request object may be sent to one or more users. The user may be the student who requested the request object or various requested learning tools satisfying the desired characteristics may be sent to the students studying in a particular course. The learning tools may be sent to the users in a variety of ways such as displaying the generated objects on a user s computer screen sending the generated objects to a user s email address or internal system messaging system or otherwise transferring the generated learning tools to the user.

Depending on the situation the requested learning tools may be generated at the time they are requested or at some future time. For example examination questions may be pre generated by a professor who wishes to vet all question before distributing the exam to his students. At other times examination questions may be generated simultaneously with an event for example where the student user begins an examination. In some cases the individual questions within a generated examination may be generated as the examination proceeds.

Also each of the desired characteristics of a learning tool may be set by a user or anticipated by the system to adapt to the characteristics of the user. Some characteristics may be user selected while others may be automatically chosen by the system. For example a student may desire the system to generate remedial learning tools that will optimally improve that particular student s proficiency in a subject area. The student user may select a time limit for the learning tool and ask the system to generate other parameters based on the particular user s characteristics. In another example a professor user may fix many of the desired characteristics for a high stakes examination to ensure fairness. In some cases a pre existing subset of a plurality of learning tools such as a chapter in a textbook may satisfy the distribution of desired characteristics of a learning tool and in those circumstances the learning tool may be re published in an unchanged form.

We denote a request object by RQ RQ where 1 rq RQ . In an embodiment each resource generation request RQmay have one or more of the following of fields described in Table 4. The characteristics of a request object will mirror the characteristics of a learning tool. Some features such as locked and black listed items do not have corresponding characteristics for learning tools as these features act to specifically exclude or include specific learning tools or classes of learning tools.

In an embodiment we define a course template as a scheduled resource generation request object RQwith the following properties for its attributes 

Another commonly used term is Learning Objective Maps or Course Blueprinting. Entire textbooks or courseware can be generated due to the flexibility of both the resource and resource request models and the system s utilization of the power of non linear filtering to estimate the most hidden user and resource attributes see ESTIMATION PROBLEM and ACTION STRATEGY section below .

In one preferred embodiment courseware may be customized to an institution s course blueprint. A user may create a course blueprint via command line interface file upload or graphical interface. Courseware may be produced as follows 

In general the system traffic is a hierarchal model where at the top level we describe user consumption or interaction of resources using the system tools and the lowest level the description is that at the level of the network i.e. TCP IP connection session . In this description we focus our attention to the higher levels of session traffic and define system traffic session object as S S.

In order to generate one or more learning tools which satisfy a plurality of characteristics of a requested distribution of desired characteristics a fitness function may be used to compare the characteristics of the requested learning tool with the distribution of desired characteristics. In an embodiment the fitness function is defined between the system s estimate of the resource characteristics denoted R for resource Rand a resource generation request RQ.

In general the fitness function quantifies attribute by attribute the difference or equivalently divergence between R and RQ. For clarity the smaller the score the closer R is to RQ.

These weights if zero nullify the corresponding subscore for segment k and if 0 serves as an importance or scaling factor.

In an embodiment we use for attributes 1 i 11 and i a variant of the Kullback Leibler divergence to measure difference between distributions x and y 

In an embodiment we further describe the comparison between two scheduled resource generation request objects x y RQ. In this case for attributes 13 i 19 we add to the overall weighted summation in 0098 .

In an embodiment we can present a method for a user to compare fitness of two course templates and any resource. For example if one wishes to answer the following How close does this eBook follow my course blueprint template the fitness function along with the systems filter estimates can answer such questions.

In an embodiment one can further compare exams to a course outline a course template without scheduling compare any two resources such as a series of homework questions and an eBook reading schedule.

In determining the similarity between a requested learning tool and the learning generated by the learning system the fitness function may place a higher emphasis on features such as fit or fairness. Fairness may measure similarity in difficulty between two or more generated examinations. For high stakes examinations the system should place heavy weight on fairness so that each student is evaluated on the basis of exams of the same difficulty. In other situations such as when the system may generate educations items such as eBooks it is more important for all topic areas to be covered and so there may be stronger weight on fit to ensure there are no topics are unrepresented. The scoring function may be used to encourage spread and encourage expected results for example by penalizing for a particular characteristic zero values in R for a candidate resource Rwhen RQdefined ideals with non zero weight on the same characteristic.

The system and method allow the creation auto generating representation and delivery of at least one of the following 

In an embodiment one may randomly generate a set of assessment item i.e. exams homework quizzes labs etc . . . each unique with controllable features on difficulty and length equivalence definable user inputs describing his her ideal set of assessment.

For example an instructor may request a weekly homework to be auto generated with 10 question slots randomly generated with a specified LO distribution taken from the current week s lecture notes and eBook readings with difficulty level 3 on average and total assessment length 90 mins.

In an embodiment the system allows users to define his her ideal characteristics of the end result by creation of a resource generation request object RQand requesting to the system to generate N unique segment assignment for R where 1 r N such that where N 1 is the theoretical maximum or total number of solutions to the problem 1 n N 0 is an acceptance threshold parameter for closeness i.e. good enough fit vs. optimal or best fit parameters as 0 and 0 is a threshold parameter for controlling the degree of fairness between any two assessments or acts as a threshold acceptance parameter for closeness when 0 and 0.

For example One such random algorithm is a genetic algorithm comprising a preparation phase then an assignment initialization phase and then followed by iterations of a series of steps each iteration comprising the following steps the selection and reproduction phase 

The following section is broken into several parts. In the first part some background discussion of the relevant non linear filter theory and the overall estimation process is provided. In the second part three signal and observation model pairs the architecture and model classes are discussed.

Simply put the problem is to estimate some object herein called the signal given a series of distorted corrupted partial data observed information concerning the signal herein called the observation . The signal has some state that contains all the pertinent information that one wishes to know.

For example in order to provide student learning resources e.g. remedial homework readings lectures problem sets forums tutoring review sessions etc . . . the learner s strengths and root deficiencies and learning style e.g. visual vs. auditory vs. kinesthetic tactile would be examples of what could be contained within the signal state.

The change of the learner s state over time or the learner s state s evolution typically contains some sort of random dynamics. This randomness is usually included in the model to handle the uncertainty concerning what development observable or not might occur next due to imperfect knowledge.

For instance the development of a learner s knowledge and skills currently taking place is not exactly known and thus the change in the state of the signal may be modeled with the appropriate randomness involved.

Within an eLearning eAssessment ePublishing eTutoring Platform environment various types of traffic data generated from a learner interacting with the Platform can be observed observation . This Platform traffic data can be used in an attempt to observe and or infer the state of the signal however such traffic generated can only give probabilistic information of the signal s state since the information is partial and distorted by some sort of noise e.g. a leaner guessing on a multiple choice question .

In order for a filter to be able to handle these types of problems a coupled mathematical model of the signal and observation is required. The mathematical model for the signal captures the key dynamics that govern the evolution of the signal state e.g. the evolution of the signal state in the positive direction i.e. knowledge acquisition for a given learning objective can be seen as the activity of learning . The observation needs to be modeled in terms of a sensor function for a given observation i.e. what information the traffic data derives from the signal based on its state as well as the noise that corrupts the data.

Depending on the type of filter to be used these models signal and observation pair must meet certain mathematical conditions. These conditions for today s most advanced filters are fairly general meaning that nearly every situation of importance can be effectively modeled.

Based on the mathematical model for the signal and observation a filter will output information based on the probability distribution of the signal state given the sequence of observations taken up until that point sometimes called the back observations . The probability distribution is usually referred to as the filter s conditional probability given the back observations or conditional estimate . Typically the information provided by the filter is the signal state itself although information which can be derived mathematically from the signal s state can also be presented. The estimate is optimal in the sense that it minimizes the error between the estimate of the signal state and the actual signal state in a least squares sense given the observation information.

The filter can provide the optimal probability of the signal state being within a certain range which can be extremely useful in determining the best course of action to take in many circumstances.

For example if the conditional distribution for a user is highly localized on the low mastery level for a particular LO i.e. proficiency level 1 or 2 and is highly localized on the kinesthetic tactile learning style i.e. learns by doing or trial and error or problem solving type then the optimal action strategy may create an individualized remedial solution by compiling for the user a set of interactive practice problems with full detailed solutions with starting with difficulty level 2 and 3.

However if the conditional distribution is spread out over a larger region of space then the optimal action strategy may wish to either wait until the next homework or quiz to occur to gain more information or suggest the learner to try out the adaptive assessment feature described in the next section ACTION STRATEGIES to help localize on the signal s state.

Detection involves identifying and characterizing a signal and is typically the initial task that a filter performs i.e. such as initial or a priori knowledge motivation intelligence and attitudes .

Once detected the tracking mode involves estimating the state of a signal and updating it in real time as new observation data arrives. Tracking mode could involve the tracking of a signal s learning. By updating in real time the system may conserve system resources because other methods of tracking data such as data mining may consume increasingly more data as time increases.

Prediction involves estimating the future state of a signal given the current conditional distribution of a filter and a course blueprint i.e. course outline and scheduled learning activities . Prediction is very useful in many areas such as giving early feedback to instructors or course administrator before it is too late i.e. the final exam .

In general we want to optimally estimate both the user s characteristics and resource characteristics. Herein we describe the signal observation model pair.

In general the signal is composed of users resources and parameters that govern both user and resource signal dynamics. The signal may represent characteristics of the user and characteristics of the learning tools.

In an embodiment the signal of a user is modeled as a collection of characteristics representing a learner s level of LO proficiency mastery interpersonal skills e.g. teaching quality motivation learning style learning type preference overall participation work ethic attitude personality and any parameters that need to be estimated to evolve the signal SEE USER OBJECT above . The signal of a resource is modeled as a collection of characteristics representing a resource object or learning tool. Note that the learning tool can be either an educational item or an assessment item SEE RESOURCE OBJECT above .

In an embodiment the signal state of a user is further evolved by external session events. For example a leaner user consuming and interacting with a section of eBook resource surely has some effect typically positive to his her proficiency for the LOs covered in the section. These external session events may drive the user behavior. User behavior is data collected about a user that is not the answers to questions i.e. question item response or other assessment items. Observations of user behavior may be obtained through user interaction with the computerized learning system.

Another example a user taking an exam creates session objects other than just the submission of his or her answers. In an embodiment the system evolves the state of the user and resource by external session events generated during an assessment e.g. traffic generated during exam or any assessment that is not just the answers to questions presented .

Below we first describe the signal dynamics of a user then followed by a description of the resource signal dynamics.

Signal evolution describes the dynamics which may be inherent to the signal e.g. in the negative direction knowledge degradation in the case of long periods of inactivity or it may come from external influences directly observed by the learning tools consumption traffic e.g. in the positive direction i.e. learning or acquiring knowledge or LO competency when an user watches an online lecture participates in a blog about a homework assignment question joins a virtual tutoring session or simply is reading and annotating an eBook .

Markov Chain model In preferred embodiment we may wish to artificially add randomness. For example one way of doing this is to use a Markov Chain model and describe transition probabilities for going from level j 1 to j for attribute and in the reverse direction. For example in the case of proficiency we can define the probabilities 1 and 1 for each LO 1 m L and j 0 1 . . . 6. Further we may wish to have p and p depend on j. An example of where this may be useful is to differentiate randomness in lower levels of proficiency j 0 1 2 or 3 as compared to the higher levels where j 4 5 or 6.

Proficiency Knowledge and Intrinsic Motivation Degradation In another embodiment we may wish to add to the model the degradation of proficiency and motivation i.e. X m and X by 1 and 1 

Continuous time Markov Chain In another embodiment we may wish to model the state transitions using Continuous time Markov Chain or Semi Markov Chain model. For example 

It is often thought that soft skills are too subtle and complex to be captured or estimated by technology. However within the system much more information is available. Learning traffic observed may be used to evolve the signal estimate. For example the user s interaction with education items such as reading eBooks or watching online lectures may be modeled in the signal model. During assessment sessions the system may include assessment behavior such as the time to complete a question the order in which questions are answered or changes made to a response during an examination as data to be used when updating the signal model

Learning Activity Sessions driving user evolution In an embodiment the system receives a session Sof type learning activity i.e. not an assessment drives the signal state.

We may wish to update the user S U state by the adjusting the appropriate rate parameters during the learning session duration ie. S S base on the session completion level S and the system s estimates for attributes of the resource consumed S i.e. S .

A conditional estimate of a user signal representing a characteristic of a user may be updated based on these types of learning activity observations through the user evolution model.

Typical assessment systems are stand alone products therefore do not incorporate a user s long term history i.e. do not track proficiency learning etc . . . . In fact students are known to cram for a quiz test or high stakes exam and such cramming activities are known to store newly acquired temporary knowledge into short term memory. Decay of knowledge from short term memory is typically swift if without reinforcement .

In an embodiment one may wish to compensate for this phenomenon by muting the proficiency transitions and the increase rates for short term motivation level.

For example in an embodiment we decrease rates for proficiency transitions and increase rates in motivation transitions when near a scheduled high stakes event e.g. final or midterm exam .

A user s state may be driven by external session events generated during an assessment e.g. traffic generated during exam or any assessment that is not just the answers to questions presented . In an embodiment this may be accomplished by adjusting appropriate transition rates .

For example in an embodiment transition rates for a user s proficiency level may be based on the following user behavior information either available directly from the session object Sor derived through the analysis of the session segments 

In an embodiment one may wish to evaluate more than just proficiency and knowledge of learning objectives one may wish to add the possibility for direct learning in an assessment. For example after answer is submitted the system may show to the user the full solution for that answer. This especially works well in one by one adaptive assessment SEE section ACTION STRATEGY below .

In an embodiment one may wish to have the identity estimated using a filter. This is especially important in a high stakes exam. This may be accomplished by comparing biometric traffic profile trained from low stakes activity of the user s interaction with the system i.e. ground truth and using a non linear filter to estimate whether or not a high stakes session activity traffic is more likely generated by a different user or simply just an anomaly e.g. user s nervousness . In this case we would need to add to the attributes of a user U. If the user signal does not correspond to a conditional estimate of the identity of the user then a report may be generated that includes a notice that the conditional estimate of the identity of the user for a current session does not correspond to a conditional estimate of the identity of the user for a previous session. In this case a proctor or the course instructor may need to be notified.

In an embodiment one may with to have other user characteristics evolve based on session traffic. These include but not limited to 

Degradation Since old resources do degenerate in effectiveness popularity and motivation levels i.e. get dated by generational and or culturally differences over time in an embodiment we may want to degrade slowly these attributes by increasing the appropriate rates .

In an embodiment external session events such as an instructor or author editing a resource may drive resource dynamics typically in a positive way . For example the effect of a resources editing session traffic may be captured by adjusting appropriate rates that govern the resources transitions for at least one of Proficiency Transition Quality Teaching Quality Level Communication Quality Level English typo and rewording edits and Extrinsic Motivation Rating.

In an embodiment external session events such as a student or learner user interacting with a learning resource may drive resource state dynamics. For example the effect of learning activity session traffic to a resources state may be captured in the adjustment of appropriate rates that govern a resource s transitions for at least one of Proficiency Transition Quality Teaching Quality Level Communication Quality Level and Extrinsic Motivation Rating.

For example users interacting with a resource may annotate the resource and publish his her annotations so that others may benefit. In an embodiment a user may start a blog forum thread or simply a conversation within the system. For example a user starts a public virtual conversation on a chapter section or even paragraph of an eBook. Such activities in a sense evolves the original eBook in a positive way. The degree of adjustment for of the appropriate rates may further be dependent on the authors of such annotations forum entries or blogs linked to the resource.

Although the system and method are described using a single filter applied to both the users and resources the filter may also be applied to each of the users and resources separately. By applying an independent filter information contained in the user signal model may be used to estimate the signal model of a resource and information contained in the resource signal model may be used to estimate the user signal model.

By using two separate filters on the resource and signal models the system may apply a filter on the resource model by extracting data from the application of a historical filter of the user model. That is by historically smoothing the generated information from the user filter the system may more accurately estimate information for the resource model. For example if a student user answered a question incorrectly at time tbut the optimal tracker shows that the student was likely to have been at a low proficiency at the time tthen that additional knowledge may be applied when considering the difficult of the resource. By applying historical smoothing the system utilizes the maximum amount of data. By using historical smoothing more accurate signal models may be generated. Historical modeling may be used to determine other characteristics of the user other than simply proficiency such as for example motivation preferred learning environment and other characteristics.

The system and method may model signals relating both to educational items and assessment items. By estimating characteristics of students educational items and assessment items the system and method may not only have better estimates of the student s knowledge and ability but also information about how a student actually learns and which educational and assessment items are effective. This feedback of both educational items and assessment items allow the system or course administrator e.g. instructors to adjust the content of course materials and assessment items either manually or through new definitions of a course blueprint. Course resources and ordering of said resources may vary over time as new teaching tools and assessment tools are shown to improve key characteristics such as motivation and proficiency of a student but moreover the system may adapt the course material for the particular needs of individual students.

The complete signal with all parameters is composed of the all users U resources R model parameters P 

In an embodiment we decouple all users and resources and describe the signal per user and per resource. i.e. X U P and X R P .

The system and method relates to analyzing observations obtained from a measurement device to obtain information about a signal of interest.

Typically the observation model is comprised of a series of sessions of type answering i.e. S Answering .

The assessment session object with u S U r S R S 21 Yes and S 13 Yes means that the session is of type assessment question and user u answering a question correctly i.e. full marks at time tcan be denoted by Y S grade 1.

Assessment observation typically observe the user s ability or proficiency on a LO which are typically information facts concepts figures ideas or principles and highly dependent on memory and recall.

The probability of observing Y 1 is based on the state of the signal. Specifically both the user and resource uand r.

In an embodiment we use the classical question item response function. i.e. given uand r we describe the probability of observing the response Y 1 as 

In an embodiment we include more signal information to use in the question item response observation model. These included the following signal attributes 

Attributes for users and resources can be observed and assessed in both technical and content support session traffic. Although this involves a human element in one preferred embodiment the system may allow the support user to adjust at least one of user or resource attribute estimates based on his her opinion. The degree of adjustment allowed may be a function of the support user s role and subject matter expertise.

In an embodiment such adjustment will need to be verified by other roles such as instructor teacher or original author.

An example the system updates the Communication Quality Level of resource and student user i.e R and U characteristic based on support technical or content messages. The system s support staff may make the distinction between the resources being unclear and the student s communication skill weakness. Illustrative scenario if question is unclear or if student is weak in reading.

In an embodiment resource s motivation popularity and estimated total time attributes may be observed in learning activity sessions. Such observations are modeled using a standard sensor functions with appropriate noise. Similar to the case in the question item response such sensor function may be dependent on a characteristic of the user involved.

An illustrative example why updating a resource based on user learning session traffic would makes sense Suppose a particular eBook chapter section was assigned to users for reading and not one out of hundreds of users who have started a session went past page two. In this case the eBook chapter section is likely an ineffective learning tool which should not be used in future years for similar types of students.

In the standard filtering theory one has that the observations are a distorted corrupted partial measurement of the signal according to a formula such as where tis the observation time for the kobservation and V is some driving noise process or some continuous time variant.

The requirement is to construct a device which can efficiently determine the conditional distribution of the state of the signal given all observations up to the current time that is 0 

Generally this device is referred to as an optimal tracker. Also the device should provide smoothers to estimate past signal states and predictors to estimate future signal states that is 0 and 0 where 

In an embodiment we utilize a non linear filter optimal tracker for estimating a conditional probability distribution for current signal states which contain both the user and resource characteristics.

In an embodiment the overall estimation process involves the set of two filters objects F U P and F R P .

F U P for estimating user Ucharacteristics we utilize a non linear filter for estimating a conditional probability distribution for current signal states optimal tracker and for past user signal states smoother U P . This filter will be updated in real time or near real time using filter estimates of resources F R P to process observations.

F R P for estimating resource Rcharacteristics we utilize non linear filters for estimating a conditional probability distribution. This filter may be updated upon the request by an author user or other administration user using filter estimates of smoothed users U P to process observations.

In order to implement a non linear filter approximations must be made so that the resulting non linear filtering equations can be implemented on a computer architecture. Different approximations are made and along with these approximations different data structures and algorithms are developed in order to use a particle filter or a discrete space filter. These approximations are highlighted in the following two examples 

In one preferred embodiment we implement the filtering process with the following iterations at every c time increments 

In one preferred embodiment we implement the filtering process with the following iterations at every time increments 

As mentioned before the filter s output is very useful in taking advantageous actions based on the information provided. In many circumstances the action to be taken can best be chosen via an optimal action strategy. An optimal action strategy uses mathematics to determine the best course of action given the filter s output. This can reduce human errors in the interpretation of the filter s output and calculation or execution of action.

We use the term residual over an attribute between A and B to mean the normalized probability distribution resulting in taking the point by point difference between distributions A and B.

In an embodiment we use at least one of the following to set the desired or optimal resource generation request object i.e. setting ideal attribute distributions 

In using residuals the choice in which attribute to consider is system feature or end result dependent. Once the generation request object is created the system s resource generation feature or some other higher level object using the generation feature will solve and present to the user the final desired product. A report of the user s deficiencies may also be generated for the user. The following are examples of how the above mentioned action strategy settings may be implemented.

In another embodiment the system may further generate a report with suggestions to other users of the system for tutoring purposes that have root deficiencies in areas in which this learner has strong proficiency.

The signal and observation model of this system and method may also be employed to estimate the identity of users who access the learning system. Ensuring the identity of test takers and the integrity of online home invigilated exam test results is a key challenge with online education. We see there being two aspects to home invigilation for high stake assessments student identification and proctoring. The heart of the problem in both aspects lie in the fact that in an online home invigilated exam both the computer and exam environment are uncontrolled thereby making it un trusted .

In order to track user identity the signal model may also include user patterns and tendencies when using software such as Graphical User Interface traffic vs. keyboard shortcuts and keystroke rates. For example if a user has throughout a semester not used any keyboard shorts within the system then a sudden increase of the use of those shortcuts during a final examination that demonstrate a much higher technological proficiency than was previously observed may indicate that the user is not the same user. In this example if the event in which the increase in use of shortcuts for a given session given a user s profile is sufficiently improbably the system may flag the user as masquerader. Moreover if the proficiency of the user has increased at a highly improbable rate or if the biometrics of keystrokes when the user typed his password are not consistent with the user s signal profile from throughout the year then again the system may flag the user as a potential masquerader. Flagging the user as a potential masquerader may also mean that a report or notice is generated for a proctor or instructor that will confirm the identity through other means e.g. such as government issued photo identification .

In an embodiment the system allows users student authors instructors etc . . . to author and create new resources Rin a collaborative system.

Default Due to the recursive nature of system resources once a permissions and rights object is created all resource segments inherit the same permissions object.

In another embodiment the grantor may give a separate write permissions object for any segment of the resource .

Permission Type R C W in English means Read Copy and Write. In an embodiment copy means to create a copy of write means to write or author the original resource directly and read means to read or load with system tools resource .

In an embodiment we expand the space to allow for more actions. For example an execute action denoted by E such that the new space E R C W. An example where an execute action may be used is in the example where a user typically an instructor user shares a scheduled request objects e.g. homework . In this case the previously stated three actions read copy and write do not make much sense. The request object for the end user i.e. receiving student is only executed by the resource generation object to produce a resource wherein the student will have read permissions to the newly created learning tool.

Granting Level In an embodiment we define Y G SG in English means Yes Granting and Super Granting. This set is ordered or ranked in the sense where Granting status can only grant a Yes status for the Permission Type in which it belongs and Yes can only grant an implicit No.

In the example scenario above we map all users and the minimum permission tuple they need in the table below 

In an embodiment we expand the space to allow for more levels of grants Y G G G . . . SG. This is especially useful the SuperGranter wants to control the distance in which derivative works can branch.

Permissions may be important where the system and method employs authoring tools in creating and modifying potentially copyright materials e.g. including annotations scientific and mathematical equations and formulae graphs eBooks questions solutions worksheet questions etc . . . . Allowing users to seamlessly create and edit content containing text web components such as tables lists as well as scientific equations and expressions requires the computerized learning system to track which users have permission to use which resources and at what times.

In an embodiment the system and method may implement an integrated symbol writing system which does not require any additional plug ins or software in order to run so that information may be updated within an ordinary web browser. For example for documents that have a copy grant then the future users may be the ability to change and updated the document.

Within an eLearning eAssessment ePublishing eTutoring platform environment system authoring tools may allow users to do the following 

In an embodiment the system may have predictive capabilities to optimally reduce user number of keystrokes on scientific equations and expressions. This means students learners will be able to enter online mathematical scientific symbols and expressions quickly and with minimal frustration.

In an embodiment the system integrates scientific symbols in line with text SmartType in content within a computerized learning system comprising 

In this description in line means for each user keystroke there is at least one of the following responses 

In an embodiment the system uses a Markov Chain model by describing the transition probabilities from a sequence of n key strokes to the next m key strokes.

In another embodiment we describe transition probability for key stroke entropy ee within a time segment.

Such a model is used for predictive text i.e. SmartType . In an embodiment transition probabilities can be initialized by the various documents and learning tools e.g. questions solutions subject matter content audible lectures worksheets chatter box forum discussions etc . . . .

In an embodiment a new bio metric signal for each user is measured and for each session a filter object is created in order to predict the users typing preferences and styles.

Particle filters are essentially sophisticated Monte Carlo methods that approximate the optimal nonlinear filter by somehow fitting Monte Carlo trials to the observations received. These filters utilize copies of the signal model entitled particles to yield its conditional estimate and distribution. Initially particle filters distribute the particles in a manner that approximates the initial guess as to the likelihood of the state of the signal. Each particle is also assigned an initial relative worth or weight. This weight is typically the same for all particles initially since there is no information from any data. The particles then evolve using the mathematical model for the signal as shown in . When new observation data arrives a particle s weight is updated based on how well the particle s state conforms to the information from the observation as demonstrated visually in . This process continues as new information arrives. In particle evolution is shown with initial locations on the right shown with the filled in circles.

Particle filters calculate a conditional estimate based on a weighted average of all particles states. As the number of particles tends towards infinity the computed estimate becomes ever closer to the value provided by the optimal filter.

The basic algorithm presented above presents the standard particle filter typically known as the Weighted Particle Filter. Subsequently adaptive particle filters were developed which added a resampling step after the weight update step. Resampling modifies the filter by copying adding and or removing particles in order to increase both the computational efficiency and the estimation fidelity.

Discrete space filters are a distinctly different type of approximate solution. Discrete space filters operate in circumstances when the domain of the signal that is the range of values for the variables that make up the state of the signal is closed. This means that the domain cannot have values that reach infinity. Despite this restriction discrete space filters can work on most interesting applications.

The premise behind discrete space filters is that the domain is broken up into a number of blocks or cells each representing a distinct area of space within the domain. For instance if the domain is a two dimensional area then the cells can form a cross section grid the domain. Similar grids can be constructed in higher dimensional spaces. These grids do not have to be uniformly refined some dimensions can be broken into smaller blocks while others can have larger blocks. shows a discrete space grid with particles.

Discrete space filters place a weight usually called a point mass in each cell. This point mass represents the relative likelihood that the signal s state currently exists within the region of the domain. The point mass value within the cell is usually called the cell s particle count and is shown in . Unlike the particles used in particle filters these particles are not copies of the signal.

In between observations discrete space filters evolve their particles by transferring particles between neighbouring cells creating new particles within the cell and destroying particles within the cell. These changes in the particle counts occur at certain rates over time and are based on the mathematical function that dictates the evolution of the signal. The effect of these rates is to mimic the potential movement of the signal.

When new observation information arrives the point masses for each cell are re calculated based on the new information in a manner similar to particle filters. The conditional distribution is formed by normalizing the point masses for each cell.

There are many challenges that are addressed when implementing a discrete space filter. For instance the number of cells to be stored can become quite large should a fine grid be required for precise estimates. In addition accessing and modifying the cells based on the observation information can become exponentially large without an effective indexing scheme. Moreover the rate calculations can be cumbersome resulting in redundant computations. In order for discrete space filters to be able to perform well many sophisticated implementation techniques are used to deal with these issues.

Furthermore well designed discrete space filters also have the ability to automatically refine the size and consequently number of the cells based on the current conditional distribution. This is extremely useful particularly when tracking signals. When a particular area of the domain has a high relative weight the cells can be refined in order to obtain a more precise distribution. Conversely should a filter with a highly refined grid receive several observations that reduce the preciseness of its estimates the filter can automatically combine cells to reduce the computational load while attempting to re acquire a good estimate of the signal s state. This type of automatic grid refinement is demonstrated in .

The methods described in this patent document may be carried out on any type of processor or computer system and may be stored on a computer program product comprising a non transitive computer readable medium having encoded thereon computer executable instructions for implementing any of the methods described.

Immaterial modifications may be made to the embodiments described here without departing from what is covered by the claims.

In the claims the word comprising is used in its inclusive sense and does not exclude other elements being present. The indefinite article a before a claim feature does not exclude more than one of the feature being present. Each one of the individual features described here may be used in one or more embodiments and is not by virtue only of being described here to be construed as essential to all embodiments as defined by the claims.

