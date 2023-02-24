
SCPPickingservice appears to manage transport orders for SCP (mfstransportorder), it also generates some scp picking orders but every single one says canceled. Maybe it just updates picking orders that can't be completed so others can be generated (there is no updated by field). I don't know.

SCPPickingservice main loop - guessing from logs, seems to do this -
I don't know what happens first but they happen in this order.

- Checking for trays to store back to STS area from backpack
    - *trays with no future reserves that are also in the backpack*
- Checking for trays with target CWL but NO active picking order
    - for cancled reservations? probably ignores manuals TO's
- Checking for trays that have WMS reservation in both modules
    - It would give these trays multiple transport orders? why?
- Checking FINISHED case orders that have ACTIVE picking orders
    - tf is a case order n'wah
    - "Checking FINISHED case orders that have ACTIVE picking orders"
    - "Reset FINISHED for case order with externalIdentifier: 7253663"
- short term lock optimization - cancel CASE_WHEELER tor for trays assigned to locked lift
    - is this talking about a fork lift
    
            Try to cancel all transport orders for tray: 30546653 location: TRA2104X012Y21Z11 tray pick target: CWL2154
            INFO  2023-02-23 05:48:52.546 PickingServiceImpl             [      ] [          ]                                -   Tray 30546653 already has a request id, skip it
            INFO  2023-02-23 05:48:52.547 PickingServiceImpl             [      ] [          ]                                -   Try to cancel all transport orders for tray: 30635043 location: TRA2102X050Y17Z21 tray pick target: CWL2154
            INFO  2023-02-23 05:48:52.549 PickingServiceImpl             [      ] [          ]                                -   Tray 30635043 already has a request id, skip it


- short term lock optimization - reassign trays to available lifts
- Cleaning finished old SCM data
- SCM cleaning done
- Cleaning finished old SPM data
- SPM cleaning done
- Cancel EMPTY transport order type for trays in locked devices/sides
- creat storage order for empty trays on tpa service lifts
- check for cases without case request on outlets
- cache scp merge point sequence
- checking if we have to activate a case order
    - start collecting scp sampling for item: 2023/02/23 05:33
    - start collecting data from visions services
- cache scp merge point sequence new
- update current gate capacity
- checking for active and wheelingallowed picking order with trays in unavailable devices
- short term blocking timeout min
- checking for locked CWL's with active picking order assighned to it
- checking for trays that needs to be moved at lift but already have wrong transport order type (reorganization or storage)
- checking for trays to move to case wheeler lift 

