# SP2026-FP08-Insight-Mission
## Names & Handles
* Petra Elrod (petraelrod42) 
* Shelby Layne (shelbylaneee) 
* Addy Peterson (addypeterson)
  
## Summary
This project analyzes seismic velocity ratios (Vp/Vs) from the NASA InSight mission to investigate the presence of liquid volatiles within the Martian crust. Our results identify a transition zone at depth, suggesting a potential global brine layer.

## How to use this Repository
This repository is organized to allow for easy navigation of our seismic analysis and findings. Our final interpreted results can be found in the primary Jupyter Notebook located in the root directory. The directory is structured into a few folders to reference our process through obtaining, cleaning, and analysing the data. Below are the important components to know about in order to run and understand our analysis: 
- environment.yml: The Conda environment file containing all necessary libraries to reproduce our research.
- marsquakes_data_frame: processed dataset for this project, derived from the InSight Marsquake Service (MQS) Catalog
- events_mars_extended_multiorigin_v14_2023-01-01.xml: The raw QuakeML event catalog sourced from the NASA PDS.
- final_marsquakes_data_frame.csv: The processed dataframe containing all calculated velocity ratios, estimated dive depths, and event qualities used for our figures.
- Final_Analysis.ipynb notebook: This is our final notebook. It contains the end-to-end workflow including:
    - XML parsing of the NASA InSight Marsquake Catalog
    - Vp/Vs ratio and Poisson’s Ratio calculations
    - Final visualizations
      
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

UMD Inisght seismic data downloader:
- Description: A repository that helps you download the Mars catalog (contains dates and times of events/marsquakes) and helps categorize them by quality and class.
- Project Use: Will help us get started downloading the data and finding the data that is important to our analysis (marsquakes that occurred where water is in the subsurface)
- https://github.com/UMD-InSight/InSight-seismic-data-downloader.git

## Tools and Packages
* Python (https://www.python.org/downloads/):
    - Main tool for data visualization and processing
* Numpy (https://numpy.org/):
    - Used for mathematical operations, like converting angular distances (degrees) into surface kilometers
* Matplotlib (https://matplotlib.org/):
    - Primary visualization tool, used to construct our custom geophysical plots
* Pandas (https://pandas.pydata.org/):
    - Used to structure raw seismic arrival data into a queryable dataframe, allowing us to filter events by Quality and calculate Vp/Vs ratios across multiple of events simultaneously.
* ObsPy (https://github.com/obspy/obspy/wiki/):
* Python Standard Library (xml.etree.ElementTree)
    - Used to create custom parsing engine for the InSight QuakeML files
 * Scipy (https://scipy.org/):
    - Used to produce a better representation of a rolling average than possible using only Pandas and Numpy. Also used to calculate a confidence interval for our prediction models.

## Planned Approach

**1. Research Data and Problem**

**2. Data Acquisition & Pre-processing**
  - Parse the NASA InSight QuakeML catalog, extracting event IDs, magnitudes, and high-quality phase arrivals (P and S wave travel times)
  - Convert angular distance (degrees) into surface kilometers using Martian-specific radii to enable physical depth estimations
  - Use parsed data and Catalog Data to create a final dataset to analyze
  - Implement a "Physical Reality" filter to remove mathematical outliers (ratios <1.0 or >5.0) caused by seismic noise or misidentified phase picks.
    
**3. Quantitative Analysis**
  - Identify High quality events: use A and B quality events that are "Broadband" and "Low Frequency" to identify volatile rich zones
  - Velocity Ratio Calculation: Compute the Vp/Vs ratio for events to examine the properties of the crust.
  - Mechanical Modeling: Derive Poisson’s Ratio from velocity data to transition from signal observations to rock mechanics and stiffness profiles.
  - Depth Estimation: Apply a linear dive-depth model to project surface arrivals into a 3D subsurface context.
    
**4. Visualization & Interpretation**
  - Subsurface Profiling: vertical depth-vs-ratio profile 
  - Global Shell Modeling: Visualize dry rocks and global brine layer 
  - Reliability Assessment: compare and contrast event quality grades (A, B) with our Vp/Vs ratios to find any correlations

## Anticipated Challenges

**Raw Catalog Parsing & Data Extraction:** Our primary challenge was the lack of a pre-formatted tabular dataset for Martian seismic events from the insight mission. Our research required parsing a raw QuakeML (XML) catalog from the NASA PDS to extract specific seismic phase arrivals for p and s waves. Developing using an xml parser and developing a script to navigate nested specific XML tags was a significant technical challenge that was required before we could use the data for analysis.

**Absence of Event Azimuths:** We were unable to extract any directional data (azimuths) from the QuakeML catalog, and we were unable to do any geographic mapping. We addressed this by pivoting to Radial Shell Modeling and Vertical Depth Profiling, which allowed us to analyze the global distribution of volatiles without requiring directional coordinates.

**Seismic Signal-to-Noise Ratio:** Martian data is heavily impacted by environmental noise (wind/thermal). To prevent unphysical velocity ratios from skewing results, we implemented a filer (clipping ratios between 1.4 and 2.4) and utilized the higher quality events for better data.

## Contribution Statement
* Addy: I was in charge of making probability plots. Using what we learned in class and what I could find on the internet, I made a plot that used PDFs to help us estimate the most probable zones to find volatiles. My contribution was in my interest and application of statistical modeling, ultimately allowing us to apply our findings and explain which findings are significant. In addition to plotting probability densities, I explained how to interpret the plots to make conclusions.
* Petra:
* Shelby:

## References
- InSight. (2018). Lockheed Martin. https://www.lockheedmartin.com/en-us/products/insight-mars-lander.html

- NASA’s InSight Records Monster Quake on Mars. (2022, May 9). NASA Jet Propulsion Laboratory (JPL). https://www.jpl.nasa.gov/news/nasas-insight-records-monster-quake-on-mars/ 

- Earthquake Waves. (2024). Pacific Northwest Seismic Network. https://pnsn.org/education/seismology/earthquake-waves 

- Hyndman, R. D. (2003). Poisson’s ratio in the oceanic crust — a review. Tectonophysics, 59(1-4), 321–333. https://doi.org/10.1016/0040-1951(79)90053-2 

- Knapmeyer-Endrun, B., Panning, M. P., Bissig, F., Joshi, R., Khan, A., Kim, D., ... & Banerdt, W. B. (2021). Thickness and structure of the Martian crust from InSight. Science, 373(6553), 438-443. https://doi.org/10.1126/science.abf8966
Wright, V., Khan, A., & Manga, M. (2024). Liquid water on Mars: Seismic evidence from InSight. Proceedings of the National Academy of Sciences, 121(35). https://doi.org/10.1073/pnas.2409983121


