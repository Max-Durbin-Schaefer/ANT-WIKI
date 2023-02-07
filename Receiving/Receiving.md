# [ANT](/ANTWIKI.md)>Receiving(Process)

(also see [Receiving(Area)](/Areas/Receiving/Receiving.md))

# Breakdown

The **Receiving** process processes and stores stock from trailers at the [Receiving](/Areas/Receiving/Receiving.md) Area. 

Each **trailer** has an **Appointment ID** that breaks down into one or more **PurchaseOrders (PO)'s** (usually one).
The **PO's** are represented by **"Receiving Orders"** in **ANT** which act as a parent to **"Receiving Order Lines"** which themselves represent a single **Picking Unit**(vendor pallet).

**Stock** arriving with the same **Item ID** will share a **Picking Unit**, there may be one or more picking units if the amount cannot fit on one pallet.

Over the **Receiving** process stock on picking units (vendor pallets) represented as Receiving Order Lines will be Processed and  

# General Flow of Receiving

        1.
                The host sends the data to the onsite database. 

        2.	
                The Appointment ID is generated and given the status of ‘New’. (RO's have statuses not appointments)
                The Appointment ID is linked to the Receiving Order, which shows the purchase order (PO).
                The Receiving Order is also linked to the Receiving Order Lines which show the item and amount that should be received. 

                Appointment ID -> Receiving Order (RO) -> Receiving Order Line (ROL)

        3.	
                The receiving clerks assign an appointment gate to the Appointment ID.
                Gate 31 is the grocery dock.
                Gate 10 is the cooler/freezer dock.
                This changes the appointment id status to ‘Assigned’.

        4.	
                Once the ROL’s are in ‘Assigned’ status, the system can move to ‘Planned’ status.

        5.	
                ‘Planned’ status creates the Consolidation Order (CO) and Consolidation Order Line (COL). 
                Once the PO is planned the CO decides how many pallets are needed to induct the item.
                The Receivers can start receiving the item after the item reaches the ‘Planned’ status.

        6.	
                When the receiver scans the items, the COL’s change status to ‘Started’.
                When the operator finishes scanning the item the COL changes the status to ‘Finished’.

        7.	
                At the end of the receivers flow, they will scan and assign a vendor barcode for the pallet.

        8.	
                The vendor barcode attaches the load unit to the stock and creates the storage order for the stock items.

        9.	
                Once the pallet is placed on the induction line, the vendor barcode is scanned.
                If the pallet is on a Chep pallet, it will need to go to the Pallet Exchanger to be exchanged for a system pallet and get the system pallet barcode assigned to the load unit.



Received goods are available for replenishment but are not reserved for shipping (billing) until the corresponding PO is closed and the stock is confirmed to McLane. 


                "When a truck arrives the receiving office must update the status of the appointment ID (start the appointment ID), so that the receiver with the RF terminal find the appointment ID faster and must not scroll through all appointment IDs. At the same time a gate is assigned for the appointment (trailer). A menu used to start the appointment is designed on RF terminals too. The receiver can select the appointment and start it and finally assign a gate for the truck. The order is available for unloading and receiving after ANT runs planning process (creates unloading list).The appointment ID of a PO can be changed as long as pallet building was not started for the appointment (remove from appointment). A new PO can be added to an appointment at any time before all POs from that appointment are closed."

**Before Pallets Can be Accepted**

- Expiration Date
- Temperature Controlled Items
- Damaged Items
- Pest Control
- Quarantine
- Building Pallets





### gathered from DOW_07_Receiving_Workstation_McLane.docx

        3.2.1	PO and appointment ID
        Each truck has an appointment ID. A truck can be one or more PO. The user must first identify on which trailer he is working. He can use the appointment ID. With the appointment ID ANT will find all PO’s with the same (Retalix(redwerks2/6/2023)) appointment ID.The Retalix(redwerks2/6/2023) appointment ID is send in the PO head-er messages.
        One item can have one or more pick units (PAL, CAS, INN, RTL). An item pick unit combination has a unique item ID.
        A PO has only one order line for one item ID (item and pick unit).
        A PO can have several order lines for the same item, but all of them have a different pick unit.
        An item is always bought in multiples of master cases (pick unit CAS or PAL).
        When the user scans a GTIN ANT has to find all order lines for this item with different pick units in all PO’s of the appointment ID. The GTIN can be the same for one item but different item numbers. 



# Links
- [ANT](/ANTWIKI.md)

