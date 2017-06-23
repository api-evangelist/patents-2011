---

title: Process for transforming and consulting directed and attributed multigraphs based on the use of maps and bitmaps
abstract: The present invention establishes a process for creating a set of structures that allows efficient storage and subsequent handling. The multigraph is represented using bitmaps with element counters and mappings between values and organized bitmaps to faciliate the handling of the multigraphs. The bits in the bitmaps represent two aspects of the multigraph: 1) indexing of all the objects of the multigraph as a function of their identifiers and 2) connectivity between objects of the multigraph, whether they are vertices or edges. Mappings allow, given a value, accessing the objects of the multigraph which contain such value. Multigraph operations are solved by accessing the mappings and applying logical operations on the bitmaps. This way of representing a graph allows efficiently performing graph operations such as: inserting a vertex or an edge, inserting an attribute, acquiring the incoming and outgoing edges of an attribute, etc.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08312052&OS=08312052&RS=08312052
owner: Universitat Politecnica de Catalunya
number: 08312052
owner_city: Barcelona
owner_country: ES
publication_date: 20110124
---
This application is a Continuation in Part of PCT International Application No. PCT IB2009 006271 filed Jul. 17 2009 which claims benefit of priority from Spanish Application No. P 200802251 filed Jul. 22 2008. The contents of these applications are incorporated herein by reference.

The present invention generically relates to a method for operating within networks or multigraphs in computational systems which allows the efficient resolution of various generic operations thereupon.

The analysis and the handling of multigraphs in an efficient manner is becoming a necessity given the growing volume of network or multigraph structured data.

Methods for managing data in multigraph form are known although they have limitations with respect to the efficient handling and storage capacity of this type of data. Specifically these methods do not allow efficiently managing data in multigraph form when the size of such data grows significantly. This occurs because the data structures used do not favor the efficient performance of some of the most common operations of multigraphs and specifically because 1 data structures do not allow quickly accessing information as is required by said operations and 2 data structures are not optimized to take into account that the memory capacity is limited. Examples of said operations are searching for patterns in a multigraph scanning the multigraph through the relationship of a vertex with its neighbors finding the diameter of the multigraph etc.

The use of systems based on traditional data models such as the relational model for the management of multigraphs does not meet the necessary requirements for constructing an efficient system which allows consulting and handling said multigraphs when they are very large. In the relational model it is considered that the data are stored in records which are organized in relationships. While this organization favors consultations in which the most important thing is the information stored in each record it does not favor some typical consultations of multigraphs relating to the analysis of the relationship between entities.

The use of specific representation systems for multigraphs such as incidence matrices allows efficiently handling multigraphs but they require that the entire multigraph can be handled in memory and have serious restrictions when the elements of the multigraph contain associated attributes or when more information besides the actual structure of the multigraph must be stored.

A system is therefore needed for representing generic multigraphs with attributes allowing the consultation and handling of said multigraphs in an efficient manner and without requiring that the entire multigraph fit in the memory available in the system.

The DEX High Performance Exploration on Large Graphs for Information Retrieval CIKM 07 Nov. 6 8 2007 Lisbon Portugal discloses a high performance graph database querying system that allows for the integration of multiple data sources. Features disclosed in this paper in common with the current invention are included in the preamble of claim .

A graph is a mathematical structure representing a network formed by vertices and edges. The objects of a graph are the set of its vertices and edges.

D2 An edge is a relationship between two vertices of a graph or network. Generally an edge is represented as a line between two vertices.

D3 a directed edge is a relationship between an outgoing or source vertex and an incoming or sink vertex. Generally a directed edge is represented as having its source in the outgoing vertex and sink in the incoming vertex.

D4 In a labeled graph all vertices and edges have a label. All the objects with the same label are said to belong to the same object type.

D5 In a graph with attributes each object can optionally have one or more attributes with an associated value for each of them. Each attribute of an object is identified with a different attribute name.

D6 In a multigraph any two vertices can be related by more than one edge of any edge type directed or not.

D7 A labeled directed multigraph with attributes is a graph which is defined from the previous definitions D3 D4 D5 and D6.

D8 Mapping is a non injective and surjective mathematical application between two sets the source set of unique codes and the image set with associated values. In a non injective application the elements of the image set can have two or more sources. In a surjective application all the elements of the image set have at least one source.

D9 A bitmap or bit vector is a data structure compactly storing sequences of true and false logic values wherein true or presence is represented with the value 1 and false or absence with the value 0. A bitmap of n bits represents a subset of 1 2 . . . n wherein the value i belongs to the subset if the bit in position i of the bitmap is marked 1. Accordingly the cardinality of said subset is equal to the number of bits marked 1 in the bitmap.

The present invention relates to a method for representing and handling structured data in generic multigraph or network form as a result of which considerable improvements are achieved in the efficiency of access to and handling of this data in relation to other representations of this type of data known until now.

The present invention determines structures and methods for the access and manipulation of data for a multigraph representing a network of interest. The multigraph includes two types of objects vertices representing entities or points in the network of interest and directed edges linking pairs of vertices. Both vertices and edges have unique identifiers within the multigraph and can contain attributes to store characteristics thereof. The objects of a multigraph can optionally be organized in various types. The edges can optionally not be directed. The multigraph is represented using bitmaps with element counters and mappings between values and organized bitmaps for the purpose of facilitating the handling of said multigraphs. The bits in the bitmaps represent two essential aspects of the multigraph 1 indexing of all the objects of the multigraph as a function of their identifiers and 2 connectivity between objects of the multigraph whether they are vertices or edges. Mappings allow given a value accessing the objects of the multigraph which contain such value. Multigraph operations are solved by accessing the mappings and applying logical operations on the bitmaps.

An example of a multigraph operation is returning the number of objects of a certain type. Solving this operation involves accessing the corresponding bitmap and returning the value stored in the counter of the bitmap.

Another example of a multigraph operation is returning the objects of a certain type the attributes of which meet a series of restrictions as a function of given values. Solving this operation involves accessing based on the values provided in the restrictions through the mappings the bitmaps associated with that attribute. The result is obtained by iteratively applying bitwise logical operations on these bitmaps.

Yet another example of a multigraph operation is obtaining the degree of a vertex in a directed multigraph i.e. the number of edges going from any vertex to this vertex. Solving this operation involves accessing the bitmap of the particular vertex which contains information about the incoming edges using a direct mapping between the vertex identifier and the bitmap. The result is calculated obtaining the counter of said bitmap.

Yet another example of a multigraph operation is obtaining the vertices connected through at least one edge to a specific vertex. Solving this operation involves accessing the bitmaps of the particular vertex which contains information about the incoming and outgoing edges respectively and obtaining from the edges information about the vertices connected to the source vertex through these edges. The result is calculated obtaining the two corresponding bitmaps from the vertex identifier and a value bitmap mapping and finding the associated vertices from the acquired edge identifiers and logical operations.

Yet another example of a multigraph operation is obtaining a segmentation of the vertices of a multigraph clustered by their value in a certain attribute. Solving this operation involves iterating on the various values of said attribute and obtaining the bitmap associated with each value through the mapping acquiring the identifiers of the vertices already classified by their value in said attribute.

Generally even increasing the complexity of operation any operation can be performed based on applying simpler operations which end up being translated into the efficient handling of the structures presented in the present invention.

The present invention can be used for the analysis of various networks of interest such as for example social networks transactional activity networks communications and or transportation networks hospital networks networks with bibliographic information etc.

The present invention can be used in several ways including in industrial processes computer implemented methods computer programs IT systems and networks user interfaces application programming interfaces and the like.

The present invention applies to a labeled directed multigraph see definition D7 formed by vertices and edges of different types wherein each type has associated therewith its own set of attributes such as that represented in . The case in which the multigraph is not directed is a simplified case of the case presented herein and in any case the principles of the present invention can also be applied directly to non directed multigraphs. The same occurs for the case in which the vertices or edges have no type or in other words they have a unique type or the case in which vertices or edges do not contain attributes.

Each element or entity of the multigraph is a vertex see D1 . In the vertices are represented in rectangular boxes.

Each relationship or link between two vertices of the multigraph is an edge see D2 . A directed edge see D3 starts from an outgoing or source vertex and ends in an incoming or sink vertex. In the edges are arrows going from the outgoing vertex to the incoming vertex indicated by the tip of the arrow.

All objects in a multigraph i.e. vertex or edge belong to a unique object type see D4 . In the object type is indicated in the heading of the object. In said example there are two types of vertices and two types of edges.

All objects in a multigraph can have a set of associated attributes see D5 . An attribute is made up of an attribute label also referred to as the name of the attribute and an associated value also referred to as value of the attribute. In the attributes of each object vertex or edge are represented by the name of the attribute the equal sign and the value of the attribute.

A bitmap see D8 is a data structure in vector form for storing collections of logical variables in bit form in a compact manner as represented in .

In the present invention bitmaps are used to represent vertices or edges of a multigraph and the relationships between them. Furthermore in the proposed representation it is considered that a bitmap includes a presence counter which counts the number of bits of the structure which have a value of 1. The length of a bitmap depends on the position of the last bit which has a value of 1. In bitmaps with different contents and lengths including the empty bitmap are represented.

There are basic processes or operations for handling a bitmap such as marking a bit setting to 1 true or present unmarking a bit setting to 0 false or absent and asking if a bit is at 1 true or present or not.

There are set theory operations which can be performed from bitwise combinations of bitmaps. For instance given two bitmaps the bitwise operations of union or logical operation OR wherein the resulting bitmap has all the bits which are marked 1 in any of the operated bitmaps marked 1 and the intersection or logical operation AND the resulting bitmap of which has all the bits which are marked 1 in all of the operated bitmaps marked 1 can be directly calculated. contains an example of the union of two bitmaps and of their subsequent intersection with another bitmap.

All objects in a multigraph are identified from a unique natural number greater than 0 referred to as object identifier. An object with identifier i 0 belongs to a collection of objects represented by a bitmap only if the position i of the bitmap is marked with 1. Otherwise the object does not belong to the collection.

A mapping see D8 is a data structure which relates elements in a source set of unique codes and an image set of data. The present invention uses mappings between object identifiers and values and between values and bitmaps . In the figure the unique codes are represented on the left and their mapped associated data or values on the right.

The set of values for each of the objects vertices or edges of one and the same attribute of an object type is represented with two mappings one between the object identifier and its associated value and the other between each different value and a bitmap specifying the object identifiers of all the objects of that type containing said value in that attribute.

For each object type in a directed multigraph there is a bitmap indicating which object identifiers correspond to objects of the specific type as shown in . The counters of said bitmaps allow immediately knowing how many objects of each type exist in the multigraph.

In each vertex or edge attribute is represented by its two mappings in a box the title of which contains the name of the attribute.

For each vertex having outgoing edges there is a bitmap in the mapping of outgoing edges specifying the object identifiers of all the outgoing edges from that vertex as can be seen in within the right mapping of the box outgoing edges.

For each vertex having incoming edges there is a bitmap in the mapping of incoming edges specifying the object identifiers of all the incoming edges from that vertex as can be seen in within the right mapping of the box incoming edges.

There is a mapping relating each edge identifier with its outgoing vertex identifier and another mapping relating each edge identifier with its incoming vertex identifier as can be verified in in the left mappings of the boxes outgoing edges and incoming edges.

To add a new vertex to the multigraph the position corresponding to the unique vertex identifier is marked in the vertex bitmap of its vertex type and the marked bit counter which is equal to the total number of vertices of said type is updated action A .

To add a new edge to the multigraph first the position corresponding to the unique edge identifier in the bitmap of edges of its vertex type is marked and the marked bit counter which is equal to the total number of edges of said type is updated action A . Then the association between the edge and the outgoing vertex is updated action B in the mapping of outgoing edges the position corresponding to the unique edge identifier in the bitmap of outgoing edges of the outgoing vertex is marked and is updated the marked bit counter which is equal to the number of outgoing edges from said vertex is updated action C . Likewise the association between the edge and the incoming vertex is updated action D in the mapping of incoming edges the position corresponding to the unique edge identifier in the bitmap of incoming edges of the incoming vertex is marked and the marked bit counter which is equal to the number of incoming edges to said vertex is updated action E .

To add a new attribute to a vertex of the multigraph the association between the unique vertex identifier and the value of the attribute in the mapping of object identifiers and values of the corresponding attribute is updated action A . Then the position corresponding to the unique vertex identifier in the bitmap of vertices associated with the value of the attribute is marked and the marked bit counter which is equal to the number of vertices having said value for said attribute is updated action B .

To add a new attribute to an edge of the multigraph the previous steps for the attribute of the corresponding edge type must be repeated.

To eliminate an attribute from a vertex or edge of the multigraph the previous steps must be undone in the same order.

To acquire the set of outgoing edges of a vertex the bitmap associated with the unique vertex identifier in the mapping between outgoing vertices and bitmaps of outgoing edges is selected action A .

To acquire the set of incoming edges of a vertex the bitmap associated with the unique vertex identifier in the mapping between incoming vertices and bitmaps of incoming edges is selected action B .

To acquire the complete edge set of outgoing and incoming edges of a vertex first the bitmap of outgoing edge identifiers is acquired subsequently the bitmap of incoming edge identifiers is acquired and finally the bitmap with the incoming and outgoing edges of the vertex is acquired as a result of the bitwise union operation of the two previously selected bitmaps action C .

To acquire the incoming and outgoing vertices of an edge first the value associated with the unique edge identifier in the mapping between outgoing edges and outgoing vertices is acquired action A . Then the value associated with the unique edge identifier in the mapping between incoming edges and incoming vertices is acquired action B .

To acquire the vertices of a certain vertex type the bitmap of vertices of said vertex type is selected action A .

To acquire the vertices of a certain vertex type which have a particular value for an attribute the bitmap of vertex identifiers associated with said value in the mapping between unique vertex identifiers and values of said attribute of the corresponding vertex type is selected action A .

To acquire the edges of a certain edge type which have a particular value for an attribute the procedure in the previous paragraph is repeated for the corresponding edge type.

To acquire the value of an attribute of a given vertex the value associated with the vertex identifier in the mapping of identifier to value of the attribute of the object type of the vertex is returned action A .

To acquire the value of an attribute of a given edge the procedure in the previous paragraph is repeated for the corresponding edge type.

The present invention generically applies to the handling of any set of organized data in network form.

Although the application on multigraphs such as that of is preferably carried out through a computer program it can also be alternatively presented as a digital circuit following the same logic an industrial design or any combination of the previous three alternatives.

Although a specific modular design is presented by way of example the same invention can be presented in a different design with a different number of larger or smaller vertices and or different names for each module.

Although bitmaps are used in the description of the preferred application described in this document the present invention can be applied for other alternative data structures which allow saving information about the presence of objects such as for example compressed bitmaps bitmaps changing the interpretation of zeros for ones and ones for zeros any representation of sets of true or false values etc.

Although mappings are used in the description of the preferred application described in this document the present invention can be applied for other alternative data structures which allow establishing a univocal association between a code and its value such as for example hash tables binary trees balanced binary trees associative matrices etc.

Although directed labeled multigraphs with attributes are used in the description of the preferred application described in this document the present invention can be applied even if the multigraph is reduced to a graph if the multigraph is not directed if the multigraph is not labeled if there are no attributes or any combination of the foregoing.

