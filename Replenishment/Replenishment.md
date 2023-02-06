# [ANT WIKI](/ANTWIKI.md) > Replenishment 

Replenishment insures that there is enough stock that is "staged" for delivery in SCS and SCP.

To decide if something should be replenished system looks at the amount in SCS and SCP. If it is not enough if will send pallets to SCS or SCP.

Replenishment process is triggered automatically each 5 minutes.

> subsystems break down into
- delayering
        
        replenishment lift
- detrash
        
        detrash station "Working Modes"
        1. SCS_DETRASH – 
            All pallets with replenishment orders to detrash are allowed at this station.
        2. EMERGENCY_DETRASH – 
            Only pallets that are designated emergencies can enter this station. This was designed to be used after SCS replenishment has been completed for today’s loads. Items that are unexpected zero’s/ short are given the priority to be detrashed in this workstation. This allows the item to go to the detrash workstation and not wait behind other preventive/permanent replenishment pallets.
        3. CIG
        -Process
		-Storage
            -Contour check
            -Family groups
	    -Tub Hospital
            -Missing stock
            -Tubs from picking that were flagged
            -Empty Tubs with Product

        

> replenishment types break down into
- emergency (immediate items that are known orders and not in storage)
        
        Replenishment that is needed to complete today’s loads should be in Emergency status. If it is not in Emergency status the pallet will still be activated in the order that it is needed.  However, if all the stations are set to Emergency, then the pallet will not go into the station and loop.

        Emergency replenishment demands are created based on the entire customer order pool. The process is triggered each time the order pool is updated during the day.

- permanence (items below min)

        type of order to balance material inventory between min and max. min and max are based on forecast

        Permanent replenishment priority is based on created date.  Created date is determined by what is needed the most. If permanent replenishment does not get finished each day, then the priority does not change until that item has been replenished or all permanent replenishment has been deleted.  Once all permanent replenishment is deleted, items that are still needed in the system will be recreated and be put into the current appropriate category of Emergency, Permanent, or Preventative replenishment.
        Permanent replenishment priority is based on the projected forecasting for each item. The system will activate and bring down items expected to be needed for the next day first with the highest need for replenishment. The priority for items is set every night when loads are dropped in. At this time new replenishment is created with the new assessed priority for the day.

        Replenishment demands (replenishment orders) are created for each picking slot and item number when the available stock on hand (SOH) is less then or equal to minimum threshold.

- preventative (forecast guessing - no, I think forecast might actually determine min max values for products)

        Another type of replenishment is the preventive replenishment which is triggered by an administrator from UI.  All replenishment demands are visible using ANT UI.

checks ammount after order is taken out(if not enough emergeny, if below min then perminant is activated)

minmax

        Shut down the replenishment service and vm. Then can go to loads page and press minmax button. then go start up services.minmaxnshut make sure all loads are new or started then shut down replenishment service run min max on loads

# links

- [ANT WIKI](/ANTWIKI.md)