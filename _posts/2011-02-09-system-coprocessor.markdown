---

title: System co-processor
abstract: Embodiments of the invention provide assigning two different class identifiers to a device to allow loading to an operating system as different devices. The device may be a graphics device. The graphics device may be integrated in various configurations, including but not limited to a central processing unit, chipset and so forth. The processor or chipset may be associated with a first identifier associated with a graphics processor and a second device identifier that enables the processor or chipset as a co-processor.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08203557&OS=08203557&RS=08203557
owner: Intel Corporation
number: 08203557
owner_city: Santa Clara
owner_country: US
publication_date: 20110209
---
This application is a continuation of U.S. patent application Ser. No. 11 648 305 filed on Dec. 29 2006 now U.S. Pat. No. 7 907 138.

Implementations of the claimed invention generally may relate to the field of video and more particularly to media acceleration of video streams for implementation in the short term however is applicable to a broader range of application fields like cryptography audio acceleration etc.

Integrated chipsets may include functionality dedicated for graphics that is either removed or disabled in a discrete graphics environment. A graphics core in an unified memory architecture integrated environment may operate in a discrete mode when there is an attached discrete graphics card. In particular the graphics core may be disabled when a discrete card is detected in an interconnect port and graphics logic in the chipset is not used. As graphics cores have evolved graphics gates in some of the current and upcoming configurations have moved from fixed functionality to more general purpose which can be programmed via code for example via kernels .

The following detailed description refers to the accompanying drawings. The same reference numbers may be used in different drawings to identify the same or similar elements. In the following description for purposes of explanation and not limitation specific details are set forth such as particular structures architectures interfaces techniques etc. in order to provide a thorough understanding of the various aspects of the claimed invention. However it will be apparent to those skilled in the art having the benefit of the present disclosure that the various aspects of the invention claimed may be practiced in other examples that depart from these specific details. In certain instances descriptions of well known devices circuits and methods are omitted so as not to obscure the description of the present invention with unnecessary detail.

Embodiments of the invention provide assigning two different class identifiers to a device to allow loading to an operating system as different devices. The device may be a graphics device. The graphics device may be integrated in various configurations including but not limited to a central processing unit chipset and so forth. The processor or chipset may be associated with a first identifier associated with a graphics processor and a second device identifier that enables the processor or chipset as a co processor.

In operation integrated graphics chipset including graphics engine may enable a second device identifier ID or a different class code that would enable chipset as a separate device in addition to being a graphics processing core. The second device ID is used to identify the coprocessor rather than the graphics processor. This second device may be enabled if external device is detected in interconnect port. For illustrative purposes interconnect port may be a PCI Express port. One skilled in the art will recognize that the port may be any port that allows operability between chipset and external device .

In addition to the device ID capability in chipset there may be an additional support requirement from the driver system basic input output system BIOS such as pre allocated memory setup and memory mapped input output MMIO setup. In particular a device driver may be associated with the second device ID. The driver sets up and configures unified memory architecture UMA system co processor as an accelerator device. It is possible for this general purpose capability to be a single or multi function.

The raw bit stream may be provided to an encoder for example to transfer to write combining space on a codec act .

The codec kernel takes the driver in the graphics non co processor mode act and programs the hardware to do any pre processing act . The kernel pre processes the input video and then encodes the bit stream. In particular the hardware will have an encode kernel that will run. The output is data such as MPEG 2 MPEG 4 and so forth. For illustrative purposes output data may be identified as MPx data although one skilled in the art will recognize that embodiments of the invention may be adapted to other configurations as well.

The encoded data may be stored and accessible through the unified memory architecture memory such as system memory act .

The encoded bit stream may then be transferred to cacheable memory act . This encoded bit stream uses the normal decode process for playback in this case on the discrete graphics add in card . In particular the data from memory may be blitted and stored in cacheable memory such as write back memory. The encoded bit stream may then be executed using a conventional playback process. For example play back is executed by a discrete graphics card.

DxVA refers to the Microsoft s DirectX API that may be used to define an interface that the player uses to hardware accelerate playback of the compressed stream on the discrete graphics device.

Acts illustrate the normal flow executed by a discrete add in card. Normally without an add in card acts would be executed by an integrated graphics engine. A discrete add in card would handle functions such as display and so forth.

In a typical implementation an encoder is located on a tuner card. The CPU handles the PVR operation. The encoder encodes that data. The CPU sends the encoded data to a discrete card. The discrete card decodes and displays it. The same functionality except the encode function may be performed by the chipset rather than the tuner card. The unified memory architecture may be directed to the system functions that the CPU carries out and the additional functions that the chipset does.

If a discrete card is detected it is determined whether the system co processor is enabled step . In a typical implementation a fuse on the chipset indicates whether the co processor mode is activated.

If an integrated co processor mode is activated the new device mode in the integrated chipset is enabled step . The discrete graphics mode is enabled as well.

If the integrated co processor mode is not activated the chipset only mode is selected. In this case the unified memory architecture for graphics to general purpose capability is not enabled.

Embodiments of the invention assist the host processor in accelerating media or other workloads across multiple product lines. Media is representative of one such implementation of embodiments of the invention. One skilled in the art will recognize that embodiments of the invention may be used in other implementations including but not limited to MPEG2 encode transcode video pre processing such as progressive interlace detection 3 2 pulldown transcale noise filter etc. encryption engine and so forth.

Embodiments of the invention enable a system co processor capability utilizing the engines in the chipset and using the driver model to extend the unified memory architecture model to cover more than the current graphics solution. By enabling the system co processor capability the base platform will be able to perform various functions. In particular the general purpose capability may be used to enable a selectable device type different personalities based on the system configuration. Conventionally this capability was limited to enable disable of integrated graphics. Embodiments of the invention allow other capabilities beyond graphics such as media encode game physics and so forth. Additionally the system unified memory architecture model is used for assisting the host processor for other functions such as hardware acceleration rather than being limited to graphics. Furthermore a faster memory transfer protocol is provided in terms of dual mapped memory surfaces.

The foregoing description of one or more implementations provides illustration and description but is not intended to be exhaustive or to limit the scope of the invention to the precise form disclosed. Modifications and variations are possible in light of the above teachings or may be acquired from practice of various implementations of the invention.

Moreover the acts in need not be implemented in the order shown nor do all of the acts necessarily need to be performed. Also those acts that are not dependent on other acts may be performed in parallel with the other acts. Further at least some of the acts in this figure may be implemented as instructions or groups of instructions implemented in a machine readable medium.

No element act or instruction used in the description of the present application should be construed as critical or essential to the invention unless explicitly described as such. Also as used herein the article a is intended to include one or more items. Variations and modifications may be made to the above described implementation s of the claimed invention without departing substantially from the spirit and principles of the invention. All such modifications and variations are intended to be included herein within the scope of this disclosure and protected by the following claims.

