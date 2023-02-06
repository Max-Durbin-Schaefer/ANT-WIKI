too edit the WIKI see the [read me](ReadMe.md)
# **Ant**

## Functionality

Ant is a system ran by Schaefer that communicates with [MCL HOST](./MCLHOST/MCLHOST.md) and [Reddwerks](./Reddwerks/Reddwerks.md) to automate the regular functions of a warehouse.

![Alt Text](AntAndSurroundingSystems.png)

These regular ***functions*** were broken down into [Receiving](./Receiving/Receiving.md)(both a function and area), [Storage](./Storage/Storage.md), [Replenishment](./Replenishment/Replenishment.md), and [Retrieval](./Retrieval/Retrieval.md). 



Each of these ***functions*** are different from one another and require distinct **Areas** with specialized equipment and services. These **Areas** made to fit specific ***functions*** can be divided into..

| Area      | Warehouse Function |
| ----------- | ----------- |
| SCP      | Retrieval       |
| SCS      | Retrieval       |
| ASRS      | Storage       |
| Shipping      | N/A (idk?)       |
| Receiving      | Receiving       |
| De-Trash      | Replenishment       |
| De-layering      | Replenishment       | 
<br>

![Alt Text](./Areas/AreasOverview.png)








## System Breakdown

Ant can be divided into the subsystems [WMS](./WMS/WMS.md), [MFS](./MFS/MFS.md), and [PLC](./PLC/PLC.md). These systems work across every **Area** with area-specific services.

[WMS](./WMS/WMS.md) (Warehouse Management System) governs Ant at a high level, processing logic behind Ant's core functionality of Receiving, Storage, Replenishment, and Retrieval. It keeps track of data on stock and also creates orders about what should be done with stock.

- (mention that wms and mfs are linked through transport unit and load unit.)


[MFS](./MFS/MFS.md) acts as an intermediary between WMS and PLC. While MFS has more specific control than WMS it has no awareness of stock. Instead MFS interprets all stock that is literally moving on conveyors as generic objects like totes, tubs, trays, cases, and pallets. MFS moves these generic object's according to their transport order.  

[PLC](./PLC/PLC.md) has the most precise control on movement. "WMS drives MFS and MFS drives PLC"





# Links
- [MCL HOST](./MCLHOST/MCLHOST.md)
- [Reddwerks](./Reddwerks/Reddwerks.md)
- [Receiving](./Receiving/Receiving.md)
- [Storage](./Storage/Storage.md)
- [Replenishment](./Replenishment/Replenishment.md)
- [Retrieval](./Retrieval/Retrieval.md)
- [WMS](./WMS/WMS.md)
- [MFS](./MFS/MFS.md)
- [PLC](./PLC/PLC.md)