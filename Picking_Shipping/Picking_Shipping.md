
## **SCPPickingService**

Services are looping programs. They follow the same series of instructions over and over. These instructions are broken into funcitons. Each function logs that it has been called and the actions it takes if any. Often the conditions for the body of the functions are not met and nothing happens.

**SCPPickingService** appears to manage transport orders for **SCP** (mfstransportorder), it also generates some scp picking orders but every single one says canceled. Maybe it just updates picking orders that can't be completed so others can be generated (there is no updated by field). I don't know.

Many functions of the service run differently, or not at all, depending on conditions. How can I classify these different cases when the ways they run are undocumented to me. Can I recorded the different kinds of cases by scraping?


SCPPickingservice main loop - guessing from logs, seems to do this -
I don't know what happens first but they happen in this order.

- f Checking for trays to store back to STS area from backpack
    - *trays with no future reserves that are also in the backpack*
- f Checking for trays with target CWL but NO active picking order
    - for canceled reservations? probably ignores manuals TO's
- f Checking for trays that have WMS reservation in both modules
    - It would give these trays multiple transport orders? why?


- f cache scp merge point sequence new - just swapped places from below doesn't always appear in same place. : (seems like this isn't a program main loop maybe?)
    - idk. it often runs in a random order.
    - i don't think the data below is actually connected to it. I think it's actually apart of the data itself. It seems to be able to eb called by any major function and is called by one and only one per loop. However it may be called by different functions.

            -   Create picking order for 30719811 (location: TRA1203X028Y07Z21) to CWL1254
            -   Create picking order for 30492592 (location: TRA2105X028Y09Z11) to CWL2156

- f Checking FINISHED case orders that have ACTIVE picking orders
    - tf is a case order n'wah

            - "Reset FINISHED for case order with externalIdentifier: 7253663"

- f short term lock optimization - cancel CASE_WHEELER tor for trays assigned to locked lift
    - is this talking about a fork lift

            Try to cancel all transport orders for tray: 30546653 location: TRA2104X012Y21Z11 tray pick target: CWL2154
            -   Tray 30546653 already has a request id, skip it
            -   Try to cancel all transport orders for tray: 30635043 location: TRA2102X050Y17Z21 tray pick target: CWL2154
            -   Tray 30635043 already has a request id, skip it


- f short term lock optimization - reassign trays to available lifts
    - work around a case wheeler that's down. Needs to be in sts not backpack obv
            
            - 	Reassign: 30528178, location: TRA2105X034Y05Z21, tray pick target: CWL2154, load: 0591, stop: 20, module_nr: 2, side_nr: 1. New target: CWL2156, traysCount: 0
            - Reasign case picking order with ext id 1625507836408, tray 30528178 is currently assign to lift CWL2154, picking target OutletConveyor2206, case order target CTT8, new picking target OutletConveyor2202
            - Reasign case picking order with ext id 1625507832762, tray 30528178 is currently assign to lift CWL2154, picking target OutletConveyor2106, case order target CTT9, new picking target OutletConveyor2102
            - 	Reassign: 30717688, location: TRA2105X038Y05Z11, tray pick target: CWL2154, load: 0591, stop: 20, module_nr: 2, side_nr: 1. New target: CWL2152, traysCount: 0
            - Reasign case picking order with ext id 1625507832779, tray 30717688 is currently assign to lift CWL2154, picking target OutletConveyor2106, case order target CTT9, new picking target OutletConveyor2110

- f Cleaning finished old SCM data
    - no output, idk
- f SCM cleaning done
    - no output, idk
- f Cleaning finished old SPM data
    - no output, idk
- f SPM cleaning done
    - no output, idk
- f Cancel EMPTY transport order type for trays in locked devices/sides
    - i don't know what an empty to is for, case wheelers type seems like it's for picking, maybe empty is it's own "type" what is it?

            -   Cancel all orders for EMPTY tray: 30337381, current location: TRA2102X020Y09Z21
            - Canceling transport order TO-30337381@TRA2102X020Y09Z21->STS1 reason: WRONG_DESTINATION
            - Missing TU tracker call for TU MFSTransportUnit[1625493553121,30337381,lastMovementTime=2023-02-22 13:14:12.993,type=MFSTransportUnitType[54287,TRAY_US],storageLocation=TRA2102X020Y09Z21]
- f Create storage order for EMPTY trays on TPA with service lifts
    - ?

            -   Create storage order for EMPTY tray: 30389915, loc: TPA2104Y03H4L2181 to STS
            -   Create storage order for EMPTY tray: 30610454, loc: TPA2101Y04H4L2181 to STS
            -   Create storage order for EMPTY tray: 30638099, loc: TPA2101Y09H4L2181 to STS
            -   Create storage order for EMPTY tray: 30644809, loc: TPA2103Y09H4L2181 to STS
            -   Create storage order for EMPTY tray: 30680180, loc: TPA2103Y03H4L2181 to STS
            -   Create storage order for EMPTY tray: 30377653, loc: TPA2103Y15H2L2181 to STS

- f check for cases without case request on outlets
    - ? and do what? it only says this sometimes, but never says anything else

            -   Finished collecting data from database
- f cache scs merge point sequence
    - idk, no data
- f checking if we have to activate a case order

            - Start collecting SCP sampling for time: 2023/02/23 05:32
            -   Start collecting data from visions services
            -     CW2151 waiting manual intervention
            -   Finished collecting data from vision visions services
            -   Start collecting data from CWL services

- f update current gate capacity
    - idk

            -   Finished collecting data from CWL services
            -   Start collecting data from database
            -   Gate name: G9, picking available: 1, current gate capacity: 300
            -   Gate name: G12, picking available: 1, current gate capacity: 400
            -   Gate name: G10, picking available: 1, current gate capacity: 500
            -   Gate name: G7, picking available: 1, current gate capacity: 600


- f checking for active and wheelingallowed picking orders with trays in unavailable devices
    - idk no data
- f short term blocking failover timeout min: 10
    - idk no data

- f checking for locked CWL's with active picking orders assigned to it
    - maybe for short term optimization? idk no data

- f checking for trays that needs to be moved at lift but already have wrong transport order type (reorganization or storage)

            -   Try to cancel all orders for tray (because of wrong TO type): 30402829
            -   Cancel all orders for tray 30402829, current location: TGA1103Y17H4W1155 transport order type STORAGE
            - Canceling transport order TO-30402829@TGA1103Y17H4W1155->TS1113|TRA1103X024Y24Z11 reason: WRONG_DESTINATION
            - Missing TU tracker call for TU MFSTransportUnit[1625494441259,30402829,lastMovementTime=2023-02-23 06:08:43.913,type=MFSTransportUnitType[54287,TRAY_US],transitLocation=TGA1103Y17H4W1155]

- f checking for trays to move to case wheeler lift 

            -   Create picking order for 30539372 (location: TRA2101X011Y19Z11) to CWL2153
            -   Create picking order for 30582941 (location: TRA2202X014Y05Z11) to CWL2255
            -   Create picking order for 30402829 (location: TGA1103Y17H4W1155) to CWL1155
