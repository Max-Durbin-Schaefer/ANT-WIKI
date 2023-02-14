# [ANT](/ANTWIKI.md) \ SCP

SCP is an area made to store and quickly pick cases from trays in storage racks.

Delayering is a subarea of SCP

## **Sub-Areas and Workstations**

|component|Ant location|function|
|-|-|-|
|Mod|Left = Mod 1, Right = Mod 2|SCP has a Mod 1 and Mod 2|
|Side|Left is Side 1 Right is Side 2|6 STSes|
|Storage Rack||Where cases sit|
|Sts's||Reaches any location of it's storage racks to retrieve/store a tray,<br> can pass/get trays from Case Wheelers via TPA/TGA locations|
|TPA/TGA/TRA locations||(TPA/TGA) Locations on the racks used mutually between case wheelers and <br>sts's to send/receive trays of cases. (TRA) Locations used to store Trays.|
|Case Wheelers| *example CWL1151* 1st # = mod. 2nd # = side. 3rd # = 5 (idk). 4rth # = front to back 1 through 6|Interacts with Sts's via TPA/TGA locations to move trays of product to Outfeed Conveyor.<br> Wheels cases onto Outfeed Conveyor. (6 per side, 24 total)|
|Outfeed Conveyors|CWOC####|Passes product from Case wheeler to Window Conveyor|
|Window Conveyors|Mod1(1100, 1200, 1300),<br>Mod2(2100,2200,2300)|carries product from Outfeed Conveyors Through OS Stations, Logo Pack, and finally to the Merge Point|
|OS Stations|can't find|Confirms material/article? Orientation and that there is only one case|
|Logo Pack|can't find|Label the cases with barcodes so they can be tracked with scanners across conveyors|
|Merge Point|before split(mod1(BSH11JD0100, BSH12JD0100, BSH13JD0100),mod2(11-13 => 21-23)),<br>merge(mod1(BSH11JM0100, BSH12JM0100, BSH13JM0100, BSH11JM0200, BSH12HM0200, BSH13JM0200)),<br>merge(mod2(11-12 => 21-23)) |Combines totes and cases of a stop.<br> What is the part that splits cases onto their door from their sister door called.<br> Is that apart of the merge point?|

Top Down view of SCP
- blue doted line is division between mod 1 and 2
- green outline is window conveyor (3 levels per mod), also acts as division between sides (2 sides per mod)
- red outlined conveyors are outfeed conveyors(3 levels, same as wc).
- blue labeled squares, like TL####, are case Wheelers.
- empty white vertical rows are were the STS's sit.
- small cells surrounding STS track is storage.

![topdown](./SCPtopDown.PNG)

Visu (side view) of SCP

- The horizontal rectangles are STS's (6 per side)
- The Vertical rectangles are CaseWheelers (6 per side, extras are replenishment lifts)
- Conveyors you see at the top are the window conveyors (3 per mod)
- Bottom right is Delayering (sub area of SCP)

![visu view](./SCPVisu.PNG)

<br>

# **Sub Areas and Equipment Continued**
## **Rack**
Metal Frame containing many storage spaces for trays (tra locations) and (TGA/TPA) locations for passing them between case wheelers. Racks also include an empty isle within themselves for an STS to travel.

![rack](./racks.PNG)

#### **TRA locations**

*Example taken from ant*\
![tra location](./locationAnt.PNG)

TRA - denotes a storage location.\
1206 - the sts associated to a rack, 3rd digit is always 0 for the rack, if it were one the 4 digits refer to the sts in the rack.\
X006 - horizontal position on rack\
Y01 - vertical position on rack\
Z11 - side

Y columns can't just go from 1-26, these positions need to account for the height of product. This is done with height classes. Because of height classes the y locations for most TRA locations are 01, 03, 05, 07, 09, 15, 17, 19, 21, 24

#### **TPA/TGA locations**

*Example taken from ant*\
![tpa location](./tpalocaiton.PNG)
TPA/TGA - denotes a put/get location.\
1106 - the sts associated to the rack. 3rd digit always 0.\
Y03 - y position, see all y positions below.\
H4 - height class
W1151 - Case Wheeler

Columns on the rack beside a case wheeler are used as transfer points instead of storage. Their Y locations are 01, 03, 07, 09, 15, 17, 21, and 23.

TPA = Transfer Put Aisle\
STS can only **PUT** a tray in this location, a case wheeler can grab a tray from here.

![tpa_locations](./TPALocations.PNG)

TGA = Transfer Get Aisle\
STS can only **GET** a tray in this location, a case wheeler can place a tray here.

![tga_locations](./TGALocations.PNG)

![real_tga/tpa_pic](./TransferPoints.png)




## **STS's**
 - Naming conventions on STS's and forks, how far can forks reach
## **Case Wheelers**
 - Naming conventions, sub component breakdown
## **Unorganized**
Tray Hospital 1 - TDL01WP01
Tray Hospital 2 - TDL02WP01
A place that talks about the distinction between locations in MFS and WMS.