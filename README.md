# RegSO_Data_Analysis
Spatial data analysis, at the RegSO level in Sweden to make spatial estimations for different municipalities.

## Working code on data analysis are presented in two jupyter notebooks:
## Regso_Data_Analysis.ipynb, analyses regso level data to calculate population density.
## Buildings_Data_Analysis.ipynb, analyses buildings data to calculate buildings count and their associated footprints.

## Extracting datasets from the WFS services, SCB "https://geodata.scb.se/geoserver/stat/wfs?service=wfs&version=1.1.0&request=GetCapabilities"
To understand the type of datasets available in the WFS of SCB, Python library “OWSLib” is used to interact with geospatial web services.

from owslib.wfs import WebFeatureService

url = "https://geodata.scb.se/geoserver/stat/wfs?service=wfs&version=1.1.0&request=GetCapabilities"

wfs = WebFeatureService(url=url, version="1.1.0")

print(list(wfs.contents))

## Following stats are available with the WFS Services:
['stat:Arbetsplatsomraden_2000', 'stat:Arbetsplatsomraden_2005', 'stat:Arbetsplatsomraden_2010', 'stat:DeSO_2018', 'stat:DeSO_2025', 'stat:Fritidshusomraden_2000', 'stat:Fritidshusomraden_2005', 'stat:Fritidshusomraden_2010', 'stat:Fritidshusomraden_2015', 'stat:Fritidshusomraden_2020', 'stat:Gronomraden_2010_tatort', 'stat:Gronomraden_2015_tatort', 'stat:Handelsomraden_2015', 'stat:Handelsomraden_2020', 'stat:RegSO_2020', 'stat:RegSO_2025', 'stat:Rutnat_1x1km_sweref99tm', 'stat:Smaorter_1990', 'stat:Smaorter_1995', 'stat:Smaorter_2000', 'stat:Smaorter_2005', 'stat:Smaorter_2010', 'stat:Smaorter_2015', 'stat:Smaorter_2020', 'stat:Smaorter_2023', 'stat:Tatorter_1980', 'stat:Tatorter_1990', 'stat:Tatorter_1995', 'stat:Tatorter_2000', 'stat:Tatorter_2005', 'stat:Tatorter_2010', 'stat:Tatorter_2015', 'stat:Tatorter_2018', 'stat:Tatorter_2020', 'stat:Tatorter_2023', 'stat:Verksamhetsomraden_2015', 'stat:Verksamhetsomraden_2020', 'stat:befolkning_1km_2015', 'stat:befolkning_1km_2016', 'stat:befolkning_1km_2017', 'stat:befolkning_1km_2018', 'stat:befolkning_1km_2019', 'stat:befolkning_1km_2020', 'stat:befolkning_1km_2021', 'stat:befolkning_1km_2022', 'stat:befolkning_1km_2023', 'stat:befolkning_1km_2024']

### Stats used in this analysis
### 'stat:RegSO_2025', 'stat:Tatorter_2023'
