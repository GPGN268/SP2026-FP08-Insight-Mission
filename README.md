# SP2026-FP08-Insight-Mission
## Names & Handles
* Petra Elrod (petraelrod42) 
* Shelby Layne (shelbylaneee) 
* Addy Peterson (addypeterson)
## Problem Statement
  Geophysics plays a significant role in revealing evidence of water on Mars. One piece of geophysical evidence particularly useful is seismology data from NASA's InSight mission. InSight studied the deep interior of Mars by studying seismic activity as well as heat flow. The InSight mission discovered that Mars has three layers: the crust, mantle, and core. InSight also discovered that Mars lacks active tectonic plates because the planet has essentially cooled off. Despite this fact, InSight discovered something contradictory: Mars has “earthquakes” even though there are no tectonic plates to cause them. These marsquakes are created because the Martian crust shrinks and breaks as it cools. These seismic waves also produce distinct signals when they pass through rock versus when they pass through water. For example, P waves travel through both liquids and solids while S waves can only travel through solids. These marsquakes proved to be very important for investigating water in the Martian subsurface, because marsquakes and meteoroid impacts are the only source of seismic activity on the planet, unlike Earth where we can produce our own seismic waves for investigation.
    
  The main question we will be answering during our final project is: How can variations in Vp/Vs ratios from NASA's Insight data indicate volatile-rich zones in Mars' shallow crust? The hypothesis that will guide our project is: Because S waves cannot travel through liquid, there should be a significant increase in Vp/Vs ratios when marsquake seismic waves pass through liquid vs when they pass through solid rock.

## Datasets
The Primary Seismic Bundle: 
- Description: Includes raw waveforms, ASCII tables, and the crucial "Derived" products like velocity models.
- Project Use: Used to extract high-frequency waveforms for local events to perform manual phase picking and spectral analysis.
- Publisher: PDS Geosciences (GEO) Node
- DOI: 10.17189/1517570
- https://pds-geosciences.wustl.edu/insight/urn-nasa-pds-insight_seis/
  
Marsquake Service (MQS) Catalog:
- Description: A derived event catalog containing metadata for all detected marsquakes, including quality ratings and distance estimates.
- Project Use: Provides the "start times" for $P$ and $S$ wave arrivals, which are the fundamental variables for calculating our $V_p/V_s$ ratios.
- Publisher: ETH Zürich (Swiss Federal Institute of Technology)
- DOI: 10.12686/a21
- https://www.insight.ethz.ch/en/seismicity/catalog/v14/
  
Derived Interior Models:
- Description: A collection of 1D seismic velocity models (Vp and Vs vs. Depth) developed by the mission’s science team.
- Project Use: Serves as the Control Group. We will compare our calculated ratios against these "dry" models to identify anomalies that suggest volatile-rich zones.
- Collection LID: urn:nasa:pds:insight_seis:data_derivedKey
- https://pds-geosciences.wustl.edu/insight/urn-nasa-pds-insight_seis/data_derived/

## Tools and Packages
* Python
* Numpy
* Matplotlib
## Planned Approach
## Anticipated Challenges
