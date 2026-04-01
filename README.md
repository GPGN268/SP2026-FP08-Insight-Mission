# SP2026-FP08-Insight-Mission
petraelrod42, shelbylaneee, addypeterson
## Problem Statement
In my introduction to geophysics class, I wrote my final report about how geophysics helped reveal the presence of water on Mars. One piece of geophysical evidence I particularly focused on was seismology data from NASA's InSight mission. InSight studied the deep interior of Mars by studying seismic activity as well as heat flow. The InSight mission discovered that Mars has three layers: the crust, mantle, and core. InSight also discovered that Mars lacks active tectonic plates because the planet has essentially cooled off. Despite this fact, InSight discovered something contradictory: Mars has “earthquakes” even though there are no tectonic plates to cause them. These marsquakes are created because the Martian crust shrinks and breaks as it cools. These marsquakes proved to be very important for investigating water in the Martian subsurface, because on Earth, scientists can produce their own seismic waves for experiments, but marsquakes and meteoroid impacts are the only source for seismic activity on Mars. The seismic waves produce distinct signals when they pass through rock versus when they pass through water. For example, P waves travel through both liquids and solids while S waves can only travel through solids.

🤔 Question and Hypothesis:
Question: How can variations in Vp/Vs ratios from NASA's Insight data indicate volatile-rich zones in Mars' shallow crust?

Hypothesis: Because S waves cannot travel through liquid, there should be a significant increase in Vp/Vs ratios when seismic waves pass through liquid vs when they pass through solid rock.

📈 How are you going to answer/test:
List the types of data and some potential public data repositories that you could use to address your question.
There are multiple public repositories on github that I think would be useful for our project. I found one repository that provides scripts for downloading and processing InSight SEIS VBB data. I also found a repository from August 2025 that analyzes seismic data from Mars. This repository provides signal processing (fourier analysis), detects anomalies in seismic waveforms, and performs 3D simulations.

We can access our data at pds.nasa.gov which contains the InSight SEIS Data Archive Online. This archive contains an overwhelming amount of data, so we will have to set aside time to determine what datasets are most beneficial for our project. This dataset also contains multiple levels of data. The set includes raw data that contains noise, processed data that has been denoised, and derived products. The dataset also contains environmental data, event catalogs, and interior models. The most useful data types for our project will be derived products in the event catalog and interior model sections. Most importantly, we need data that analyzes P-wave velocities, S-wave velocities, Vp/Vs ratios, and crustal layering models. I think we will need help searching through this data and downloading it in a form we can use, but once we figure it out there will be many ways to graph and compare the P and S wave velocities!
## Datasets
## Planned Approach
## Anticipated Challenges
