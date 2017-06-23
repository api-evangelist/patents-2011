---

title: Closing a video stream object
abstract: Techniques are provided for facilitating processing of interlaced video images for progressive video displays. A method receives from a renderer a query for a graphics device driver to a graphics processing capability that can be performed by an associated graphics device in de-interlacing video data, communicating the query to the graphics device driver, receiving from the graphics device driver a response to the query that identifies the graphics processing capabilities to the renderer, and communicating the response to the renderer. The method includes receiving from the renderer a further query for the graphics device driver to at least one input requirement associated with the identified graphics processing capability, communicating the further query to the graphics device driver, receiving from the graphics device driver a further response to the further query that identifies the input requirement(s) associated with the graphics processing capability, and communicating the further response to the renderer.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08176500&OS=08176500&RS=08176500
owner: Microsoft Corporation
number: 08176500
owner_city: Redmond
owner_country: US
publication_date: 20110103
---
This Non Provisional Application is a continuation of co pending Non Provisional application Ser. No. 11 276 695 filed on Mar. 10 2006 titled Methods and Apparatuses for Facilitating Processing Interlaced Video Images for Progressive Video Displays which is incorporated by reference herein in its entirety. The application Ser. No. 11 276 695 is a divisional of Non Provisional application Ser. No. 10 273 505 filed on Oct. 18 2002 titled Methods and Apparatuses for Facilitating Processing of Interlaced Video Images For Progressive Video Displays now U.S. Pat. No. 7 219 352 which is incorporated by reference herein in its entirety. The application Ser. No. 10 273 505 in turn claims benefit of priority from U.S. Provisional Application Ser. No. 60 372 880 filed Apr. 15 2002 and titled Methods and Apparatuses for Facilitating De Interlacing of Video Images which is incorporated by reference herein in its entirety.

This invention relates generally to video processing and display and more particularly to facilitating processing of interlaced video images for progressive video displays.

Video image sequences can usually be categorized into two different types progressive and interlaced. With progressive video all the picture elements comprising a frame of video data are sampled at the same moment in time. With interlaced video alternative lines of the video image are sampled at alternate moments in time the resulting interlaced video frame is therefore made up of two fields each field being half the height of the video frame.

Examples of interlaced video sequences are TV signals and the output of DV camcorders. Examples of progressive video sequences are certain DVD s and computer generated video such as the output of the Windows Media Video encoder. Additionally some professional level video cameras also generate progressive video.

Computer monitors and other like display devices are examples of a progressive display system and are therefore able to display progressive video without any additional processing. Interlaced video cannot be displayed on a computers monitor unless it has first been de interlaced .

The current technique for de interlacing video in a conventional personal computer PC requires the use of a graphics overlay device by a graphics processor. There are several restrictions and limitations to the use of the graphics overlay devices and as a consequence of this their usage will likely be deprecated in the future. For example for most PCs there can only be one graphics overlay device. Additionally most graphics overlay devices only provide a crude de interlacing algorithm such as e.g. the BOB algorithm.

Consequently for these reasons and others there is a need for improved methods and apparatuses for facilitating the de interlacing of video.

In accordance with certain exemplary aspects of the present invention methods and apparatuses are provided for facilitating the de interlacing of video. By way of example interfacing methods and apparatuses are provided in certain implementations for instructing graphics processor logic i.e. hardware firmware and or software to de interlace a video field to produce a single video frame that can be displayed on a computer monitor and or other like display devices. This can be accomplished without the need for a graphics overlay device.

In accordance with certain implementations of the present invention a method is provided which includes causing a graphics device driver to identify to a renderer at least one graphics processing capability associated with a corresponding graphics device and causing the graphics device driver to identify to the renderer at least one input requirement associated with the identified graphics processing capability.

In other implementations of the present invention a graphics device driver is operatively configured to identify to a renderer at least one graphics processing capability associated with a corresponding graphics device and at least one input requirement associated with the identified graphics processing capability.

In accordance with still other implementations of the present invention a computer readable medium is provided which includes computer executable instructions for causing at least one processing unit to cause a graphics device driver to identify to a renderer at least one graphics processing capability associated with a corresponding graphics device and also cause the graphics device driver to identify to the renderer at least one input requirement associated with the identified graphics processing capability.

The above stated needs and others are also met by a method that includes causing a renderer to identify to a graphics device driver a description of interlaced video data to be processed by a graphics device associated with the graphics device driver. The method further includes causing the graphics device driver to identify to the renderer at least one graphics processing capability associated with the graphics device that may be used to provide de interlacing and or other applicable processes and causing the renderer to select at least one of the identified graphics processing capabilities and request input requirements from the graphics device driver for the selected graphics processing capability capabilities. The method also includes causing the graphics device driver to identify to the renderer the input requirements associated with the identified graphics processing capability capabilities.

In certain implementations an apparatus is provided which includes rendering logic graphics device logic and interface logic. The interface logic operatively couples the rendering logic and the graphics device logic such that the rendering logic can provide a description of interlaced video data to be processed by a graphics device associated with the graphics device logic the graphics device logic can identify at least one graphics processing capability associated with the graphics device the rendering logic can request input requirements from the graphics device logic for at least one selected graphics processing capability and the graphics device logic can identify at least one input requirement associated with the at least one selected graphics processing capability.

In accordance with yet another exemplary implementation a method is provided that includes receiving from a renderer a query for a graphics device driver as to at least one graphics processing capability that can be performed by an associated graphics device in de interlacing video data communicating the query to the graphics device driver receiving from the graphics device driver a response to the query that identifies the graphics processing capability capabilities to the renderer and communicating the response to the renderer. In other implementations the method also includes receiving from the renderer a further query for the graphics device driver as to at least one input requirement associated with the identified graphics processing capability communicating the further query to the graphics device driver receiving from the graphics device driver a further response to the further query that identifies the input requirement s associated with the graphics processing capability and communicating the further response to the renderer.

In still other implementations of the present invention a method of communicating between a rendering process and a graphics device driver process that is associated with a graphics device is provided. Here for example the method includes issuing by a rendering process a query call having at least one call parameter comprising a description of video data to be processed by the rendering process and a graphics device receiving by the graphics device driver process the query call and parsing the query call to retrieve the call parameter s and issuing by the graphics device driver process a query acknowledgment call having at least one acknowledgment parameter comprising an identifier for at least one supportive processing capability that the graphics device can provide based on the description of video data.

Another exemplary method includes issuing by a rendering process a query call having at least one call parameter comprising an identifier for a selected supportive processing capability that a graphics device can provide to process selected video data receiving by a graphics device driver process associated with the graphics device the query call and parsing the query call to retrieve the call parameter s and issuing by the graphics device driver process a query acknowledgment having at least one acknowledgment parameter comprising at least one input requirement associated with the selected supportive processing capability.

In accordance with still other aspects of the present invention a method for establishing a video stream object between a rendering process and a graphics device having an associated graphics device driver is provided. Here for example the method includes issuing by a rendering process an open stream call having at least two call parameters including an identifier for a selected supportive processing capability that a graphics device is to perform while processing streamed video data and a description of video data to be processed by the rendering process and the graphics device while processing the streamed video data. The method further includes receiving by a supporting process the open stream call and parsing the open stream call to retrieve the call parameters and issuing by the supporting process a stream identifier corresponding to a video stream object provided by the supporting process.

In still other implementations a method for closing a video stream object is provided. Here for example the method includes issuing by a rendering process a close stream call having at least one call parameter comprising a stream identifier corresponding to a previously established video stream object and receiving by a supporting process the close stream call and parsing the close stream call to retrieve the call parameter and causing the supporting process to close the previously established video stream object.

Some of the above stated needs and others are also addressed by a method for use in manipulating interlaced video data. The method includes accessing interlaced video data including top field data and bottom field data associated with a video surface having a width a height and a stride. The method further includes producing a reinterpreted video surface by isolating the top and bottom field data and configuring the isolated top and bottom field data in the reinterpreted video surface such that the reinterpreted video surface has a reinterpreted height that is less than the height and a reinterpreted stride that is greater than the stride.

Turning to the drawings wherein like reference numerals refer to like elements the invention is illustrated as being implemented in a suitable computing environment. Although not required the invention will be described in the general context of computer executable instructions such as program modules being executed by a personal computer. Generally program modules include routines programs objects components data structures etc. that perform particular tasks or implement particular abstract data types. Moreover those skilled in the art will appreciate that the invention may be practiced with other computer system configurations including hand held devices multi processor systems microprocessor based or programmable consumer electronics network PCs minicomputers mainframe computers and the like.

The improved methods and apparatuses herein are operational with numerous other general purpose or special purpose computing system environments or configurations. Examples of well known computing systems environments and or configurations that may be suitable include but are not limited to personal computers server computers thin clients thick clients hand held or laptop devices multiprocessor systems microprocessor based systems set top boxes programmable consumer electronics network PCs minicomputers mainframe computers distributed computing environments that include any of the above systems or devices and the like.

As shown in computing environment includes a general purpose computing device in the form of a computer . The components of computer may include one or more processors or processing units a system memory and a bus that couples various system components including system memory to processor .

Bus represents one or more of any of several types of bus structures including a memory bus or memory controller a peripheral bus an accelerated graphics port and a processor or local bus using any of a variety of bus architectures. By way of example and not limitation such architectures include Industry Standard Architecture ISA bus Micro Channel Architecture MCA bus Enhanced ISA EISA bus Video Electronics Standards Association VESA local bus and Peripheral Component Interconnects PCI bus also known as Mezzanine bus.

Computer typically includes a variety of computer readable media. Such media may be any available media that is accessible by computer and it includes both volatile and non volatile media removable and non removable media.

In system memory includes computer readable media in the form of volatile memory such as random access memory RAM and or non volatile memory such as read only memory ROM . A basic input output system BIOS containing the basic routines that help to transfer information between elements within computer such as during start up is stored in ROM . RAM typically contains data and or program modules that are immediately accessible to and or presently being operated on by processor .

Computer may further include other removable non removable volatile non volatile computer storage media. For example illustrates a hard disk drive for reading from and writing to a non removable non volatile magnetic media not shown and typically called a hard drive a magnetic disk drive for reading from and writing to a removable non volatile magnetic disk e.g. a floppy disk and an optical disk drive for reading from or writing to a removable non volatile optical disk such as a CD ROM R RW DVD ROM R RW R RAM or other optical media. Hard disk drive magnetic disk drive and optical disk drive are each connected to bus by one or more interfaces .

The drives and associated computer readable media provide nonvolatile storage of computer readable instructions data structures program modules and other data for computer . Although the exemplary environment described herein employs a hard disk a removable magnetic disk and a removable optical disk it should be appreciated by those skilled in the art that other types of computer readable media which can store data that is accessible by a computer such as magnetic cassettes flash memory cards digital video disks random access memories RAMs read only memories ROM and the like may also be used in the exemplary operating environment.

A number of program modules may be stored on the hard disk magnetic disk optical disk ROM or RAM including e.g. an operating system one or more application programs other program modules and program data .

The improved methods and systems described herein may be implemented within operating system one or more application programs other program modules and or program data .

A user may provide commands and information into computer through input devices such as keyboard and pointing device such as a mouse . Other input devices not shown may include a microphone joystick game pad satellite dish serial port scanner camera etc. These and other input devices are connected to the processing unit through a user input interface that is coupled to bus but may be connected by other interface and bus structures such as a parallel port game port or a universal serial bus USB .

A monitor or other type of display device is also connected to bus via an interface such as a video adapter . In addition to monitor personal computers typically include other peripheral output devices not shown such as speakers and printers which may be connected through output peripheral interface . Video adapter typically includes a video graphics device.

Computer may operate in a networked environment using logical connections to one or more remote computers such as a remote computer . Remote computer may include many or all of the elements and features described herein relative to computer .

Logical connections shown in are a local area network LAN and a general wide area network WAN . Such networking environments are commonplace in offices enterprise wide computer networks intranets and the Internet.

When used in a LAN networking environment computer is connected to LAN via network interface or adapter . When used in a WAN networking environment the computer typically includes a modem or other means for establishing communications over WAN . Modem which may be internal or external may be connected to system bus via the user input interface or other appropriate mechanism.

Depicted in is a specific implementation of a WAN via the Internet. Here computer employs modem to establish communications with at least one remote computer via the Internet .

In a networked environment program modules depicted relative to computer or portions thereof may be stored in a remote memory storage device. Thus e.g. as depicted in remote application programs may reside on a memory device of remote computer . It will be appreciated that the network connections shown and described are exemplary and other means of establishing a communications link between the computers may be used.

As mentioned there is a need to de interlace certain types of video image data so that it can be correctly displayed on a computer s monitor or other like display device. Previous releases of Microsoft Windows operating systems for example have relied on a graphics overlay device to de interlace the video as it is displayed on the computer s monitor. There are several drawbacks to this and other similar techniques including for example 1 There is only one graphics overlay device in the computer therefore only a single video stream can be displayed correctly 2 The graphics overlay device has to be keyed to computers desktop display this means that if an end user presses the print screen key he only captures the key color not the video image currently being displayed 3 When the user drags a window to a new location there are occasional flashes of key color displayed where there should be video displayed 4 If a user drags a semi transparent window over the top of the video play back window key color is blended with the user s window not the video image.

Furthermore the typical method of de interlacing employed by contemporary graphics overlay device is of a very low quality it is at a level much lower than that of consumer device such as a television.

The novel methods and apparatuses presented herein enable graphics processors to de interlace the video image without the need of a graphics overlay device. The techniques presented also allow graphics processors to use more advanced de interlacing algorithms an in particular ones that offer a significant improvement in the visual quality of the video image displayed when compared to traditional arrangements.

At the top of an interleaved video surface is shown as having two interleaved fields namely a top field and a bottom field . Video surface has a width a height and a stride . At the bottom of a reinterpreted video surface is shown as having an isolated top field and bottom field . Here video surface has a height that is the height of the corresponding interlaced video surface and also a stride that is twice the stride of the corresponding interlaced video surface .

Apparatus includes transform logic which for example may include instructions performed by a central processing unit a graphics processing unit and or a combination thereof Transform logic is configured to receive coded video data from at least one source . The coded video data from source is coded in some manner e.g. MPEG 2 etc. and transform logic is configured to decode the coded video data. By way of example source may include a magnetic disk and related disk drive an optical disc and related disc drive a magnetic tape and related tape drive memory a transmitted signal or other like source configured to deliver or otherwise provide the coded video data to transform logic . In certain implementations the source may include a network and remote source such as represented by Internet and a remote source .

The decoded video data output by transform logic is provided to at least one renderer . Renderer is configured to aid the transform logic in decoding the video stream aspect ratio correct the video image so that it matches the display device s aspect ratio blend any other auxiliary image data such as closed captions or DVD sub picture images with the video image and then at the appropriate time submit the video image data to the graphics interface logic for display on the display device . The resulting rendered video data is then provided to graphic interface logic . Graphic interface logic may include for example DirectDraw Direct3D and or other like logic. Graphic interface logic is configured to provide an interface between renderer and a graphics device .

The data output by graphic interface logic is provided to a graphics device driver using a device driver interface . Here device driver interface is depicted as having at least one application programming interface API associated with it. Device driver interface is configured to support the interface between renderer and graphics device driver

As illustrated in in certain implementations device driver interface and graphics device driver may further be categorized as being either part of user mode logic or kernel mode logic with respect to the operating environment of graphics device .

In this example the video data output by renderer is eventually provided to a graphics processor unit GPU which is configurable to perform de interlacing logic frame rate converter logic optional and or other processing of the video data. In this example as their names suggest de interlacing logic is configured to de interlace the video data and frame rate converter logic is configured to modify the frame rate as needed desired.

The output from GPU is provided to video memory . When video memory is read the resulting data is then provided to a digital to analog converter DAC which outputs a corresponding analog video signal suitable for display by display device . In other configurations the display device may be configured to process the digital data from video memory without the need for DAC . As illustrated a graphics device may include GPU video memory and DAC . In certain implementations graphics device takes the form of a video graphic card that can be configured within a PC or like device.

The configuration shown in is but one example of a video data processing apparatus. Those skilled in the art will recognize that other possible configurations may also benefit from the methods and apparatuses of the present invention.

Attention is now drawn to the flow diagram in which depicts a method for interfacing renderer and graphics device . One or more APIs may be configured to perform or otherwise support method .

In act renderer provides a description of the video data to graphics device driver . Here the video data has been selected to be processed and eventually presented through display device . In response graphics device driver in act identifies applicable or otherwise available graphics processing capabilities of graphics device . The identified graphics capabilities are associated with GPU or other like logic. In certain implementations for example one or more de interlacing functions rate converter functions and or other applicable functions may be identified in some manner.

In act renderer or other associated logic selects at least one of the identified graphics processing capabilities. In act renderer requests any applicable input requirements for the selected graphics processing capability capabilities. In response to the request in act graphics device driver provides any applicable input requirements to renderer .

In act renderer opens a stream for the video data. In act renderer and graphics device process stream and eventually display the video. In act renderer closes the stream that was opened in act .

Apparatus is one example of a video processing system that can be arranged to provide de interlacing frame rate conversion and or other processing of video data. By way of further example in accordance with certain exemplary implementations of the present invention Microsoft DirectX VA can be extended or otherwise enhanced to support de interlacing and also frame rate conversion associated with the processing of image data that is to be rendered and displayed. Additional related information can be found in a Microsoft Windows Platform Design Note entitled DirectX VA Video Acceleration API DDI dated Jan. 23 2001 and which is incorporated herein by reference.

This following describes APIs that advantageously extend Microsoft DirectX VA to support de interlacing frame rate conversion and or other processing capabilities for video content in graphics device drivers. This description provides driver developers and others skilled in the art with a clear understanding of the exemplary APIs and methods and apparatuses provided herein.

While the methods and apparatuses are described herein in terms of APIs that are applicable to the current evolution of Microsoft Window operating systems for PCs it should be understood that the methods and apparatuses are also applicable to other operating systems and or other devices.

Video that is interlaced can for example be de interlaced using the DirectX Video Acceleration and Direct3D 9 APIs for video. The graphics engine e.g. GPU and a hardware overlay if present should support a minimum of BOB and weave de interlacing functionality.

The output of the de interlacing or frame rate conversion process is a progressive frame. The de interlaced and frame rate conversion interface described in this document is independent of all video presentation mechanisms. In the following examples the de interlaced output is provided in the target DirectDraw surface. Doing so precludes the need for conventional hardware overlay solutions.

De interlacing as used herein means to generate a progressive video frame at a given time t by reconstructing the missing lines from a field at time t. Frame rate conversion as used herein means generating a new progressive video frame at any arbitrary time t from a sequence of fields or frames.

A video sample can be for example a DirectDraw surface that contains one or two video fields. Flags are associated with the sample to indicate the number of fields contained in the surface and the temporal order of the fields. The video can arrive in this surface through many possible routes such as the output of a DX VA video decoder process the output of a video port or the output of a host based video decoder etc.

Most graphics adapters that can perform a StretchBlt can also perform a simple BOB style de interlacing. This is essentially simply a matter of reinterpreting the memory layout of the video within a DirectDraw surface. After the surface has been reinterpreted to isolate the two fields for example each line within a field is doubled e.g. by interpolation to generate in between lines . A single frame line offset may be required to prevent the de interlaced video from displaying vertical jitter.

When a video surface contains two interlaced fields as shown e.g. in the memory layout of the surface can be reinterpreted in order to isolate each field. This can be achieved for example by doubling the stride of the original surface and dividing the height of the surface in half as illustrated. After the two fields are isolated in this way they can easily be de interlaced by stretching the individual fields to the correct frame height. Additional horizontal stretching or shrinking can also be applied to correct the aspect ratio for the pixels of the video image.

Graphics device driver can be configured to identify the graphics device s ability to do this to renderer e.g. a DirectX Video Mixing Renderer VMR or the like through a Query Capabilities API e.g. DeinterlaceQueryModeCaps described in greater detail below.

The height of the individual field can be stretched vertically by line replication or through the preferred method of a filtered stretch for example. If the line replication method is used the resulting image may have a blocky appearance. If a filtered stretch is used the resulting image may have a slight fuzzy appearance.

The exemplary APIs described herein can be divided into two functional groups of methods. The first group includes a set of methods and apparatuses that can be used to determine the de interlacing capabilities of the graphics device. The second group includes a set of methods and apparatuses that are used for creating and using a de interlace stream object.

The APIs are designed to be part of a device driver interface supporting a graphic interface and interfacing with a graphics device driver . In accordance with certain implementations of the present invention the APIs are not necessarily user mode APIs that are accessible by applications. However in other implementations they may be.

A DeinterlaceQueryAvailableModes method can be used to query the de interlacing frame rate conversion modes and or other functions modes capabilities that are available for a particular input video format. Here for example a globally unique identifier GUID or other suitable identifier is provided for each mode returned by the graphics device. The GUIDs can for example be returned in some particular order such as e.g. in order of descending or ascending quality. Thus for example the highest quality mode may occupy the first element of the GUID array that is returned. Thus by way of example consider 

In this example the 1pVideoDescription parameter is a description of the type of video to be de interlaced rate converted and or otherwise processed. The 1pVideoDescription parameter is passed to the graphics device driver so that it may tailor the graphics device to support the resolution and format of the source video. For example the graphics device might be able to perform a three field adaptive de interlace of 480i content but it might only be able to BOB 1080i content.

In accordance with certain implementations the graphics device should be able to at least support BOB for example using the existing Blt ter hardware. Thus consider the following example 

The DXVA VideoDesc data structure passes to the driver the intention of the de interlacing or frame rate conversion to be performed as further shown in the following examples.

To de interlace 720 480i content that is sourced as two fields per sample at a frequency of 29.97 Hz the DXVA VideoDesc data structure may contain the following 

If the intention is to de interlace and perform frame rate conversion the OutputFrameFreq field can be as follows 

If the intention is to just de interlace a single field to a progressive frame for later MPEG encoding the OutputFrameFreq field can be as follows 

To perform frame rate conversion on 480p content for example to match the monitor display frequency the DXVA VideoDesc structure may contain the following 

Note that de interlacing and frame rate conversion may also be performed together using the above exemplary structures.

BOB line doubling using the Blt ter for example. In certain implementations this mode should always be available.

Simple Switching Adaptive. Here for example either a blend of two adjacent fields if low motion is detected for that field or BOB if high motion is detected.

Advanced 3D Adaptive. Here for example the missing lines are generated through some adaptive process that is likely proprietary to the graphics device. The process may for example use several reference samples to aid in the generation of missing lines. The reference samples may be temporally in the past or future. For example three dimensional linear filtering would fall into this category.

Motion Vector Steered. Here motion vectors of the different objects in the scene are used to align individual movements to the time axis before interpolation takes place.

Those skilled in the art will recognize other possible de interlacing capabilities that can also be supported by the methods and apparatuses of the present invention.

Frame repeat drop. This may not be a recommended mode because it tends to consume extra memory bandwidth by copying the selected source sample into the destination surface.

Linear temporal interpolation. Here a future and a previous reference field are Alpha blended together to produce a new frame.

Motion vector steered. Motion vectors of the different objects in the scene are used to align individual movements to the time axis before interpolation takes place.

Those skilled in the art will recognize other possible frame rate conversion and or other processing capabilities that can also be supported by the methods and apparatuses of the present invention.

After renderer has determined the de interlace modes available for a particular video format it queries the graphics device driver again to determine more detailed information related to the input requirements of a particular de interlace mode and or any other applicable video processing that has been selected. Thus consider the following example 

By way of further example graphics device driver can be configured to report the capabilities of GPU for a selected mode in an output DXVA DeinterlaceCaps structure for 1pDeinterlaceCaps. For example consider the following 

Here the NumPreviousOutputFrames field indicates the required number of frames that have previously been output by the de interlace algorithm. This parameter can be used by recursive de interlace algorithms.

The InputPool field indicates the memory pool from which the interlaced source surfaces should be allocated. See for example the Direct3D and DirectDraw documentation in the above referenced text for a description of valid memory pool locations.

The NumForwardRefSamples field indicates the required number of additional reference samples that are temporally in the future for this de interlace mode none for BOB and line blending and possibly several for adaptive de interlacing and frame rate conversion.

The NumBackwardRefSamples field indicates the required number of additional reference samples that are temporally in the past for this de interlace mode none for BOB one for line blending and possibly several for adaptive de interlacing and frame rate conversion.

The OutputFrameFormat field indicates the Direct3D surface format of the output frames. Usually a de interlace algorithm would likely output frames in a surface format that matches the input sample format. This field ensures that renderer will be able to supply the correct output frame surfaces to the de interlacing hardware logic. Note that if the DXVA Deinterlace YUV2RGB flag is returned in the VideoProcessingCaps field renderer may assume that the valid output formats are specified by this field as well as an RGB32 format.

The VideoProcessingCaps field identifies other operations that can be performed concurrently with the requested de interlace. The following flags identify some exemplary operations 

DXVA VideoProcess SubRects. The de interlace hardware logic can operate on a sub rectangle region of the video image. This is useful for example if the video image needs to be cropped before being processed further as the size of the output frames is reduced.

DXVA VideoProcess YUV2RGB. The de interlace hardware logic can convert the video from the YUV color space to the RGB color space. In certain implementations the RGB format used will have at least 8 bits of precision for each color component. If this is possible a buffer copy within renderer can be avoided.

Note that in certain implementations the graphics device driver should be able to support this operation for the BOB de interlace mode. Color space conversion is particularly useful within renderer if it can be combined with any and ideally all of the following flags 

Note that in this exemplary implementation there is not a requirement to convert from the RGB color space to the YUV color space.

DXVA VideoProcess StretchX. If the de interlacer is able to stretch or shrink horizontally aspect ratio correction can be performed at the same time as the video is being de interlaced. This flag can be supported for the BOB de interlace mode.

DXVA VideoProcess StretchY. Sometimes aspect ratio adjustment is combined with a general picture re sizing operation to scale the video image within an application defined composition space. This is probably quite rare and will not be an essential feature n certain implementations. This flag can be supported for the BOB de interlace mode. Typically it is better if the scaling needed for resizing the video to fit into the application window can be done at the same time as the scaling needed for de interlacing. For example doing so avoids cumulative artifacts.

DXVA VideoProcess AlphaBlend. Again this can avoid a buffer copy with renderer . Typically it is very rare that applications alter the constant alpha value associated with the video stream so in certain implementations this may be considered a low priority feature for system.

In certain implementations other capabilities may also be identified. For example other color gamma modifying information may be identified. Rotation sheering and or other similar processes may also be identified using the above techniques.

The DeinterlaceTechnology field identifies the underlying technology used to implement this particular de interlacing algorithm. The following flags identify some exemplary operations the flags may be combined as necessary to most closely match the algorithm s implementation 

DXVA DeinterlaceTech Unknown indicates that the algorithm is unknown or proprietary to the hardware manufacturer.

DXVA DeinterlaceTech BOBLineReplicate indicates that the algorithm creates the missing lines by repeating the line either above or below it this method will look very jaggy and therefore may not be adequate for some uses.

DXVA DeinterlaceTech BOBVerticalStretch wherein the algorithm creates the missing lines by vertically stretching each video field by a factor of two for example by averaging two lines or using a 1 9 9 1 16 filter across four lines. Slight vertical adjustments may be made to ensure that the resulting image does not bob up and down.

DXVA DeinterlaceTech MedianFiltering wherein the pixels in the missing line are recreated by a median filtering operation.

DXVA DeinterlaceTech EdgeFiltering the pixels in the missing line are recreated by an edge filter or the like. In this process for example spatial directional filters may be applied to determine the orientation of edges in the picture content and missing pixels created by filtering along rather than across the detected edges.

DXVA DeinterlaceTech FieldAdaptive the pixels in the missing line may be recreated for example by switching on a field by field basis between using either spatial or temporal interpolation depending on the amount of motion.

DXVA DeinterlaceTech PixelAdaptive the pixels in the missing line may be recreated for example by switching on a pixel by pixel basis between using either spatial or temporal interpolation depending on the amount of motion.

DXVA DeinterlaceTech MotionVectorSteered Motion Vector Steering identifies objects within a sequence of video fields. The missing pixels are recreated after first aligning the movement axes of the individual objects in the scene to make them parallel with the time axis.

After a suitable de interlace mode GUID has been found a DeinterlaceStream object can be created. Creation of a DeinterlaceStream object allows graphics device driver to reserve any hardware resources e.g. associated with GPU or the like that are required to perform the requested de interlace or other selected operations.

The DeinterlaceOpenStream method creates a DeinterlaceStream object. For example consider the following 

Here the HDXVA DeinterlaceStream output parameter is a handle to the DeinterlaceStream object and can be used to identify the stream in all future calls. Thus consider the following example 

Note in the exemplary case above that the end time of the first field is the start time of the second field.

The DeinterlaceBlt method performs the de interlace or frame rate conversion operation by writing the output to the destination surface. Hence consider this 

In the DeinterlaceBlt method the rtTargetFrame parameter identifies the location of the output frame within the sequence of input frames. If only de interlacing is being performed then the target time will coincide with one of the rtStart times of a reference sample. If a frame rate conversion is being requested the rtTargetFrame time may be different from any of the rtStart times of the reference samples.

Here the source and destination rectangles are required for either sub rectangle de interlacing or stretching. Support for stretching is optional and can be reported by Caps flags for example . Support for sub rectangles may not be needed in certain implementations.

The destination surface can be a Direct3D off screen plain Direct3D render target a Direct3D texture or the like that is also a render target. In accordance with certain exemplary implementations the destination surface will be allocated in local video memory.

The pixel format of the destination surface will be the one indicated in the DXVA DeinterlaceCaps structure unless a YUV to RGB color space conversion is being performed as part of the de interlace procedure. In this exemplary case the destination surface format can be an RGB format with at least 8 bits of precision for each color component.

The DeinterlaceCloseStream method closes the DeinterlaceStream object and instructs the device driver to release any hardware resource associated with this stream. For example consider the following 

For compatibility with the DDI infrastructure for Windows operating systems the proposed APIs described earlier in this description and others like them can be mapped to the existing DDI for DirectDraw and DirectX VA. This section describes an exemplary de interlace interface mapping to the existing DirectDraw and DX VA DDI.

The purpose of the DX VA container DDI group is to determine the number and capabilities of the various DX VA devices contained by the display hardware. Therefore a DX VA driver need only have a single container while still supporting multiple DX VA devices.

It is not possible to map the de interlace device query calls on to any of the DDI entry points in the DX VA container group because unlike the rest of DX VA the container methods use typed parameters. However the DX VA device DDI group does not use typed parameters so it is possible to map the proposed de interlace interface to the methods in that group. The rest of this section describes how the new interfaces described herein can be mapped to the DX VA device DDI.

The DX VA device methods do not use typed parameters so the methods can be reused for many different purposes. However the DX VA device methods can only be used in the context of a DX VA device so it is necessary to first define and create a special de interlace container device . As used herein the DX VA de interlace container device is a software construct only and it does not represent any functional hardware contained on a device. The de interlacing sample device driver code later in this specification shows how the container device could be implemented by a driver.

This exemplary method maps directly to a call to the RenderMoComp method of the de interlace container device. The DD RENDERMOCOMPDATA structure can be completed as follows 

Note that the DX VA container device s RenderMoComp method can be called without BeginMoCompFrame or EndMoCompFrame being called first.

This exemplary method maps directly to a call to the RenderMoComp method of the de interlace container device. The DD RENDERMOCOMPDATA structure can be completed as follows 

Here 1pOutputData will point to a DXVA DeinterlaceCaps structure. Note that the DX VA container device s RenderMoComp method can be called without BeginMoCompFrame or EndMoCompFrame being called first.

This exemplary method maps directly to a CreateMoComp method of the DD MOTIONCOMPCALLBACKS structure where the GUID is the de interlace type requested pUncompData points to a structure that contains no data all zeros and pData points to a DXVA VideoDesc structure.

If a driver supports accelerated decoding of compressed video renderer may call the driver to create two DX VA devices one to perform the actual video decoding work as defined by the DirectX VA Video Decoding specification and the other to be used for de interlacing.

The exemplary sample code below illustrates how the driver may map the CreateMoComp DDI call into calls to DeinterlaceOpenStream. The sample code shows only how the CreateMocComp function is used for de interlacing. If the driver supports other DX VA functions such as decoding MPEG 2 video streams the sample code below can be extended to include processing of additional DX VA GUIDs.

In addition to the CreateMoComp DDI function the driver can also implement the GetMoCompGuids method of the DD MOTIONCOMPCALLBACKS structure. The following exemplary sample code shows one possible way of implementing this function in the driver.

This exemplary method maps directly to a RenderMoComp method of the DD MOTIONCOMPCALLBACKS structure where 

1pBufferInfo points to an array of surfaces. The first surface is the destination surface and the remaining surfaces are the source surfaces.

Note that for the DX VA device used for de interlace RenderMoComp will be called without calling BeginMoCompFrame or EndMoCompFrame.

The exemplary sample code below shows how the driver may map the RenderMoComp DDI call into calls to DeinterlaceBlt. The sample code only shows how the RenderMoComp function is used for de interlacing. If the driver supports other DX VA functions such as decoding MPEG 2 video streams the sample code can be extended to include processing of additional DX VA GUIDs.

This exemplary method maps directly to a DestroyMoComp method of the DD MOTIONCOMPCALLBACKS structure.

The following exemplary sample code shows how the driver may map the DestroyMoComp DDI call into calls to DeinterlaceCloseStream. The sample code shows only how the DestroyMoComp function is used for de interlacing. If the driver supports other DX VA functions such as decoding MPEG 2 video streams the sample code below can be extended to include processing of additional DX VA GUIDs.

In accordance with the various exemplary implementations presented herein the present invention addresses the problem of de interlacing of video image data so that it displays correctly on a computer monitor or other like display device. As noted conventional de interlacing techniques typically require the use of a graphics overlay device by the graphics processor which has several restrictions and limitations. With the various methods and apparatuses described herein for example a graphics processor can be instructed as to how to de interlace a video field to produce a single video frame that can be displayed on a computer monitor so that interlaced video is displayed correctly in real time. By way of further example various APIs have also been shown some of which specifically extend Microsoft DirectX VA to support de interlacing and or frame rate conversion for video content in graphic device drivers.

Although the description above uses language that is specific to structural features and or methodological acts it is to be understood that the invention defined in the appended claims is not limited to the specific features or acts described. Rather the specific features and acts are disclosed as exemplary forms of implementing the invention.

