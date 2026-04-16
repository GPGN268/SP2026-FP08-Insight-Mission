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

UMD Inisght seismic data downloader:
- Description: A repository that helps you download the Mars catalog (contains dates and times of events/marsquakes) and helps categorize them by quality and class.
- Project Use: Will help us get started downloading the data and finding the data that is important to our analysis (marsquakes that occurred where water is in the subsurface)
- https://github.com/UMD-InSight/InSight-seismic-data-downloader.git

## Tools and Packages
* Python (https://www.python.org/downloads/)
* Numpy (https://numpy.org/)
* Matplotlib (https://matplotlib.org/)
* Pandas (https://pandas.pydata.org/)
* ObsPy (https://github.com/obspy/obspy/wiki/)

## Planned Approach

**1. Identify high quality events**
The MQS Catalog gives quality ratings. We will process this catalog and output the high-quality events (A and B), then cross-reference these event id's with the Primary Seismic Bundle to view their raw data. Once we find the specific events, we need to identify volatile-rich zones (like liquid water or brines) by prioritizing "Broadband" and "Low Frequency" Events because these waves have longer wavelengths that "see" deeper into the crust. We will accomplish this by using the [UMD Insight Seismic Data Downloader](https://github.com/UMD-InSight/InSight-seismic-data-downloader.git)

**2. Identify arrival times of waves**
To calculate the Vp/Vs ratios we will use the equation: ((tS-tP)/((tP-t0))+1 where tS = arrival time of S wave, tP = arrival time of P wave, and t0 = origin time. We will use xml parsers to locate these measurements for each quality event from step 1.

**3. Calculate Vp/Vs Ratios**
Since velocity is v=distance/time, and the quakes have to travel the same distance to reach the lander, Vp/Vs can be estimated using the arrival times of the p and s-waves (distance would be a constant). We will write a function that loops over each event and plugs the respective times into the equation: ((tS-tP)/((tP-t0))+1. 

**4. Map and Analyze Vp/Vs Ratios**
Once we have calculated the Vp/Vs ratios for each quality event, we will compare them and create visuals. We hypothesize that water is located in the subsurface of the locations of events that have significantly high Vp/Vs ratios. This would be when we might need to use [ObsPy](https://github.com/GPGN268/SP2026-FP08-Insight-Mission/edit/main/README.md), a Python library that should help us analyze the different parts of the data, like arrival times of the P and S-waves.

**5. Possibly find other data to support our findings**
Similar to the well-log assignment, we might be able to find porosity, density, or resisitivity data to support our conclusion that there is water in the Martian subsurface.

**6. synthesize our results and map.**
By mapping our results, we should be able to see any areas with a pattern of volatiles to determine high-probability zones for water, like specific areas or depths. This is also the time when we summarize our findings and write our introduction! 

## Anticipated Challenges

**We don't find any significantly large Vp/Vs ratios:** If this occurred, we would not be able to say that seismic data contains evidence that there is water underneath the Martian subsurface. We would not be able to make further analysis about our project or come to a significant conclusion.

**No triangulation:** On Earth, multiple stations help to triangulate the exact location of a quake. InSight is one lander, so it is difficult to approximate distance or location. Our Vp/Vs ratios might be relatively accurate, but we will likely have a hard time mapping since we only have one source of data. 

**Data volume:** The volume and format of data is extremely dense. Many pieces of data come in MiniSEED format, or in different formats for each dataset, so we will need to convert them to more readable files that are compatible with each other in order to make comparisons. To do this, we may need to find other geophysics software that would do the heavy lifting.
