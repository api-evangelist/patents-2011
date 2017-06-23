---

title: Method for regulating a valve
abstract: 


is used to determine when to close the steam bypass valve. The steam bypass value is closed when tis smaller than a value Δt. An actual volume of water {dot over (m)}, a desired volume of water {dot over (m)}and a maximum water-volume deficiency FBmax are used in the equation.

url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08857455&OS=08857455&RS=08857455
owner: Siemens Aktiengesellschaft
number: 08857455
owner_city: Munich
owner_country: DE
publication_date: 20110215
---
This application is the US National Stage of International Application No. PCT EP2011 052185 filed Feb. 15 2011 and claims the benefit thereof. The International Application claims the benefits of European Patent Office application No. 10001533.8 EP filed Feb. 15 2010. All of the applications are incorporated by reference herein in their entirety.

The invention relates to a method for regulating a valve wherein the valve is arranged in a steam line wherein the steam line has a device for spraying water.

During starting or ramping up of a fossil fired power plant a boiler of the power plant which is designed for producing steam is initially operated at minimum load which usually lies between 30 and 40 load. The live steam which is produced during this ramping up phase is in this case customarily initially routed past the steam turbine directly to the condenser in so called bypass mode. In the case of plants with a reheater the live steam in this case is conducted via a high pressure bypass station spray cooled to a low temperature level and then directed into the cold line of the reheater. The steam which leaves the hot line of the reheater is conducted via an intermediate pressure bypass station and cooled by means of spraying with water and directed into the condenser. As a result of a high pressure level in the reheater which customarily lies between about 20 bar and 30 bar effective cooling of the reheater tubes which are impinged upon by flue gas is ensured.

For the operation of steam turbine plants high demands are to be placed upon the purity of the steam. In particular it is necessary to avoid particulate solids being entrained in the steam. Such solid body particles can lead to damage to the steam turbine and other plant components. Damage is incurred especially on the blading of the turbine.

In order to achieve slight superheating it is necessary that the steam volume which is conducted via the intermediate pressure bypass steam line is cooled to a low temperature level. This means that the bypass steam in the bypass steam line has to be spray cooled with water. However this requires a reliable and direct availability of the volume of water which is to be sprayed. Furthermore a fast acting spray water valve and a reliable measuring technique are required.

If the water which is to be sprayed is totally absent precautions have to be taken so that no damage occurs. At present the existing water spray protection devices are designed in such a way that only a total absence of spray water is taken into consideration.

Even temporarily falling short of the necessary volume of water is considered to be a malfunction which in the worst case can lead to a total closing of the bypass steam line and could even lead to a trip that is to say a shutdown of the entire power plant would be the consequence.

An initiated emergency shutdown of the bypass station can lead to repercussions upon the inspection interval or upon the service life of the gas turbine in the event of a gas turbine trip.

With the present precautions it is quite possible that an emergency shutdown of the bypass station is carried out even though a volume of water of more than 90 of the desired value has already been achieved and an emergency shutdown as such would not be necessary.

The invention comes in at this point the object of which invention is to disclose a method for regulating a valve with which method an emergency shutdown of the bypass station is executed in such a way that a premature closing of the valve is avoided.

This object is achieved by a method for regulating a valve according to the claims. In this case the valve is arranged in a steam line wherein the steam line has a device for spraying water wherein an actual volume of water dot over m and a desired volume of water dot over m and a maximum water volume deficiency FBare determined and a quotient tbetween the maximum water volume deficiency FBand the difference between the desired water volume dot over m and the actual volume of water dot over m is formed according to the equation

The invention is based on the idea that the currently existing precautions allow an operation of the bypass station without sufficient volumes of spray water for a specific time t. The aforesaid precaution applies independently of the steam volume and the volume of spray water in the bypass station i.e. that even for the maximum steam volume and totally absent volumes of spray water the precautions are possible.

If a volume of spray water is absent as a result of a malfunction this results in a lack of cooling. The lack of cooling is referred to as deficiency FB with regard to the enthalpy difference of the evaporating water and is produced by an integration of a deficient quantity over time which is specified by the following equation dot over m dot over m . In this case dot over m refers to the water flow rate and dot over m refers to the actual volumes of water.

The maximum permissible deficiency is produced by the following equation FB dot over m t wherein dot over m represents the maximum volume of spray water and trepresents the maximum time without water spraying. The deficiency which is accumulated until initiation of an emergency shutdown is calculated according to the following 

It is necessary that the maximum time allowed for reaching the maximum permissible deficiency is reached when the integrally determined deficiency is equal to the maximum permissible deficiency. This is achieved if the following equation is satisfied 

If this equation is solved according to t the maximum time allowed can be determined. However in this case the precondition must be fulfilled that the determined volumes of water mand mare in compliance with the following equation 

In a first advantageous development the maximum water volume deficiency FBis formed from a multiplication between a maximum volume of spray water and a maximum time according to the equation FB dot over m t.

In a further advantageous development the actual volume of water dot over m and the desired volume of water dot over m are determined according to each cycle rate t. This cycle rate can be optionally selected according to the invention which leads to more accurate control than control with a longer cycle rate t.

According to an advantageous development according to each cycle rate t a residual time is determined and the valve is closed if the residual time tis less than the value t wherein i is to represent a counting of a loop starting at zero according to which the residual time tis calculated in each case. This has the advantage that an integration is carried out which integration leads to not just a criterion having to be fulfilled in order to achieve closing of the valve.

Downstream of the high pressure turbine the outflowing steam makes its way to a reheater and from there into an intermediate pressure turbine section . The outlet of the intermediate pressure turbine section is fluidically connected to an inlet of a low pressure turbine section . The steam which discharges from the low pressure turbine section is fluidically connected via a low pressure line to the condenser .

In the condenser the steam condenses forming water and via a pump is directed again to the boiler as a result of which a water steam cycle is completed.

During starting or during shutting down of the steam power plant the live steam is routed via a bypass line past the high pressure turbine and conducted directly into the cold reheater line . The hot reheater line which is constructed downstream of the reheater is fluidically connected via an IP bypass station to the condenser . Formed in this IP bypass station are an IP bypass valve and a device for spraying water into the IP bypass station .

During starting or ramping up of the steam power plant the boiler is initially operated at minimum load in most cases 30 to 40 load wherein the steam which is produced is customarily initially routed past the high pressure turbine bypass mode . The bypass mode is realized in this case by closing the emergency stop valve which is arranged in the steam inflow section of the high pressure turbine wherein the live steam is conducted via a high pressure bypass station or bypass line spray cooled to a lower temperature level and then fed to a reheater in fact initially to the cold line of the reheater. The steam which leaves the hot line of the reheater is conducted via an intermediate pressure bypass station and after cooling by means of sprayed water is directed into the condenser . As a result of a high pressure level in the reheater effective cooling of the reheater tubes which are impinged upon by flue gas is ensured in the process.

The controlling of the valve is carried out as described in the following Initially a cycle rate t in seconds is predetermined or preset and a maximum permissible deficiency FB in kilograms is also calculated which deficiency can be determined in a first approximation by the following equation .

In a subsequent step as shown in a time tequal to 0 is set if the condition of dot over m being less than dot over m is fulfilled. This means that as soon as the required volume of water in the device which is conducted into the IP bypass station is less than the desired volume of water an integration begins. Initially a volume of water is determined from a characteristic curve. Then via a measurement the actual volume of water is determined. A calculation of the residual time

For further integration the number variable i is set to zero. It is then determined whether the residual time is greater than the cycle rate. If the residual time is greater than the cycle rate this case with yes is led to a further calculation loop as shown in . This means that the index i is increased by 1 and a residual time is recalculated according to the trapezoid rule. To this end the formula which is presented in the box is used.

For the time t less than t no spray water is available which means that in the time period up to tthe absence of spray water prevails. After the time point t the integration begins which is represented by the curve and leads to an emergency shutdown at time point t. The initiation of the bypass emergency shutdown is represented by the curve . represents the situation that there is 100 deficiency of the volume of water. This means for example that the valve remains in the closed position despite demand.

