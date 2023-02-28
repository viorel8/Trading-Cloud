
# Description 
- [Description] (#script-description)

# Table of contents
- [Table of contents](#table-of-contents)
  - [Indicator overview](#indicator-overview)
  - [Feature description](#feature-description)
  - [Update](#feature-updates)
  - [Comments and planning](#comments)

## Indicator overview
![Idnetity server with BFF flow](./Assets/monday_script_v2/description.png "Indicator general description")

Will run slower as the Lite version and will only work from the M3 up to the M20 as the data gets too much to handle on ltf’s. Locates Mondays and extend through Tuesday. Shows Opening range and warning when Monday H/L is breached on Tuesday. Shows highest % rise and fall in OI from the current week’s open. Also shows max vol since the week started. Added weekly candle with OI and vol data
![Idnetity server with BFF flow](./Assets/monday_script_v2/description_1.png "Indicator general description")
![Idnetity server with BFF flow](./Assets/monday_script_v2/description_2.png "Indicator general description")

## Feature description

## Update
![Idnetity server with BFF flow](./Assets/monday_script_v2/update_1.png "Optimized code so will run a tad faster, added a daily  side candle and added an alert for when OI rise, fall or a spike in volume shifts to the current bar (in testing and got a error on the M3 but seems to work 100% on the M5) . To use the alert simply be on the M5 and right click on the indicator and select  “Add alert on Mondays | Opens” and click on “Create”. The alert should notify each element separately as in the code attached. Also made the script to only show detail on the M3 -M15, it will show only Monday Opening range and Mondays on anything higher than the M15. Unfortunately only compatible with crypto atm. ")
![Idnetity server with BFF flow](./Assets/monday_script_v2/update_2.png "Updating the interface")
![Idnetity server with BFF flow](./Assets/monday_script_v2/update_3.png "Updating the interface")

## Comments and planning