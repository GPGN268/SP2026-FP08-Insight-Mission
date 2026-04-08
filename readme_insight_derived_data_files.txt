Seismic Experiment for Investigating the Subsurface (SEIS)
InSight Mission to Mars

Overview
========

This bundle contains the following collections:

data_seed:   
  SEIS observations in Mini-SEED format and associated metadata in 
  Dataless SEED format. SEED is the Standard for Exchange of 
  Earthquake Data maintained by the International Federation of 
  Digital Seismograph Networks (www.fdsn.org).
           
data_table:  
  The same SEIS observations converted to PDS-compliant ASCII text 
  tables (GeoCSV format) and associated metadata in XML files 
  (StationXML format).
  
data_laf: 
  Lander Activity Files, records of daily activities on InSight SEIS
  such as communications with the lander and changes to instrument
  gain. 
  
data_derived:
  The Mars Quake Service (MQS) catalog of seismic events.
  
schema_mqs:
  XML schema used by data products in the data_derived and data_laf 
  collections.
       
This bundle also contains (as a secondary member) the SEIS document 
collection, document_seis, which includes the following documents.
  seis_release_notes.txt
       SEIS Release Notes, updated with each release of data to PDS
  seis_sis.pdf
       The SEIS Software Interface Specification (SIS)
  seedmanual_v2.4.pdf
       The SEED User's Manual
  ins-st-grds-1500-ipgp_seed_channelnaming.xlsx
       The SEIS SEED Channel Naming document in original MS Excel format
  ins-st-grds-1500-ipgp_seed_channelnaming.pdf
       The SEIS SEED Channel Naming document in PDF format
  location_codes_only.xlsx
       The SEIS Location Codes document in original MS Excel format
  location_codes_only.pdf
       The SEIS Location Codes document in PDF format
  fdsn-station-1.0.xsd
       The FSDN StationXML base schema
  fdsn-station-availability-1.0.xsd
       The StationXML time series data availability schema extension
  variations-fdsnsxml-seed.txt
       An overview of major variations between SEED 2.4 and StationXML.
       
The SEIS Software Interface Specification is the primary documentation
for the SEIS archive.

Each document and data product in this bundle is described by a PDS4
label in a separate file with the same name but with the extension "xml".
PDS4 labels are XML (eXtended Markup Language) files that conform to
the PDS4 Information Model XML schema at
https://pds.nasa.gov/pds4/schema/released/. They are best viewed in an
XML-aware text editor, and may be used by software that can manipulate 
XML documents. 

The SEIS Data Files
===================

SEIS data products are classified as either "continuous" or "event". 
A continuous data product spans one Earth day, midnight to midnight UTC.
An event data product contains data for a single seismic event, as 
determined by flight software. An event may last as long as several 
minutes and may cross an Earth day boundary.  Continuous and event
data are stored in separate branches of the data directory,
as shown below.

The SEED and ASCII data collections are co-mingled under the 
data directory. The data directory tree uses the following
structure, with the SEED products and their ASCII equivalents in 
the lowest-level subdirectories.

For continuous data products: 

   data / [network] / continuous_waveform / [station] / [year] / [doy]

For event data products:

   data / [network] / event_waveform / [station] / [request-event-id]

The Dataless SEED metadata files that correspond to the Mini-SEED data
products, along with their ASCII equivalents, are stored in this 
directory structure:

   data / [network] / metadata / [station]

The file formats of SEIS data products are summarized in Table 1.

_______________________________________________________________________________
Table 1. SEIS File Formats

File Contents  SEED Format    PDS-Compliant Format
-------------  -------------  --------------------------------------------------
Data           Mini-SEED      GeoCSV (ASCII text in comma-separated value table)
Metadata       Dataless SEED  StationXML (ASCII text in XML format)
_______________________________________________________________________________


The file naming conventions are given in Table 2. Each data file is accompanied
by a PDS label with the same name but with the extension ".xml". 

_______________________________________________________________________________
Table 2. SEIS Data File Naming 

Continuous data  
---------------
Directory:            data/[network]/continuous_waveform/[station]/[year]/[doy]/
                      
Mini-SEED data file:  [network].[station].[location].[channel].[year].[doy].[rev].mseed
Mini-SEED data label: [network].[station].[location].[channel].[year].[doy].[rev].xml
                      
ASCII CSV data file:  [network].[station].[location].[channel].[year].[doy].[rev].a.csv
ASCII CSV data label: [network].[station].[location].[channel].[year].[doy].[rev].a.xml
   
                      
Event data
----------
Directory name:       data/[network]/event_waveform/[station]/[request-event-id]/
                      
Mini-SEED data file:  [network].[station].[location].[channel].[request-event-id].[rev].mseed
Mini-SEED data label: [network].[station].[location].[channel].[request-event-id].[rev].xml
                      
ASCII CSV data file:  [network].[station].[location].[channel].[request-event-id].[rev].a.csv
ASCII CSV data label: [network].[station].[location].[channel].[request-event-id].[rev].a.xml
         
                      
Metadata
--------

Directory name:       data/[network]/metadata/[station]/

Dataless SEED metadata file:   dataless.[network].[station].[year].[doy].seed 
Dataless SEED metadata label:  dataless.[network].[station].[year].[doy].xml
                      
StationXML metadata file:      stationxml.[network].[station].[year].[doy].sxml
StationXML metadata label:     stationxml.[network].[station].[year].[doy].xml
                
_______________________________________________________________________________
                     
For the above naming conventions, the values for network, station, location, channel,
and request-event-id are found in the SEIS SEED Channel Naming document 
(ins-st-grds-1500-ipgp_seed_channelnaming.pdf) in the document collection. 
For event data, [year].[doy] is the year and day-of-year of the beginning
of the event.

Calibration of SEIS raw data results in revisions to the transfer function
specified in the metadata file. The raw data files are not changed; 
rather, revised metadata files are provided as better calibration 
information becomes available throughout the mission.

This bundle was created and archived by the Geosciences Node of the Planetary 
Data System. Questions about this bundle may be directed to 
geosci@wunder.wustl.edu.
Last updated 2019-05-01.
