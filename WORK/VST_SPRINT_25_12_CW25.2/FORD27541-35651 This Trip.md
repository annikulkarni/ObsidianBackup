# P703 Base FNV2.1 PHEV: This Trip: Distance, Electric Distance and Fuel Economy not show dashes in missing and invalid states

Blocked by other teams to implement signals
Started implementing
In fuel economy 
we have this **TC_FE_Dsply_DCFE** 
for this 
![[Pasted image 20250615164926.png|250]]
and for the same dashes are in the **SAME** data structure    
static tsIodFuelEcoData           sFEData; which is defined in *IodReceiveTransformFuelEconomyV4* in file Iod transform.c
the thing is we need to have the signal to send dashes AND the fault signal in the same data structure to make it work, currently its happening
- the signal to send distance and ev distance for this trip are in tripData, that is  IodReceiveTransformTripStats (function)     static tsIodTripsData sIodData;(data structure) in these
- but the signal for dashes is in fuel economy, that is not working practically

<mark class="hltr-boom-bam">The above mentioned issue was a wrong assumption</mark>, just added signal in fuel economy, reloaded in fuel economy kanzi, and used that in trip_iod kanzi project to show dashes 

Implemented
DI APPS is testing
Testing done, issue in Connection from VP to HMI
working in target through VMF :) waiting for RTE team complete and i need to test and close 

Testing sequence

Verified Version
None

![[Pasted image 20250618120834.png]]

