# [ANT](/ANTWIKI.md)>Receiving(Process)

### gathered from notes

Receiving is the process where stock is processed from trucks arriving at the warehouse to stock in system.

Receiving begins with appointments which are processed into Purchase Orders, purchase orders


Received goods are available for replenishment but are not reserved for shipping (billing) until the corresponding PO is closed and the stock is confirmed to McLane. 


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

