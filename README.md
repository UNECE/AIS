# AIS

Outputs from [ONS-UNECE Machine Learning Group 2022 AIS Theme Group](https://statswiki.unece.org/display/ML/Machine+Learning+Group+2022)

## Code: AIS Berth Polygon Cookbook
Port Polygons are important for generating statistics based on geospatial filtering e.g. port visits, anchoring patterns, etc. There exists no standard for generating polygons at the microdetail needed by most applications. The cookbook aims at demonstrating a standard algorithm/method for self generating berth (an area where the cargo is loaded or discharged on and off the ships) polygons by using AIS positions and port location data. The cookbook consists of 6 sections:

**1) Set-up**: install packages and pre-defined modules

**2) Port data**: import and visualise port (point-wise location) data

**3) H3 data**: create and visualise a set of H3 hexagons to be used as filter for AIS

**4) AIS data**: import and filter AIS raw data 

**5) Berth polygons**: create berth polygons based on count of AIS signal within H3 hexagons

**6) Berth polygons using DBSCAN**: create refined version of berth polygons using DBSCAN based on count of AIS signals within (high-resolution) H3 hexagons. 

The cookbook is available [here](https://code.officialstatistics.org/mlpolygonsalgorithm/ml-group-polygons). Please note that in order to execute the full version of the code, access to raw AIS data is required, which is only available through the [UN Global Platform (UNGP)](https://unstats.un.org/bigdata/un-global-platform.cshtml). See below for a light version of the cookbook accessible via Google Colab. 


## Code: Google colab version of AIS Berth Polygon Cookbook
To provide an overview of the cookbook without requiring access to UNGP, we have created a light version of the cookbook in Google Colab. The Colab version contains only the parts of the cookbook that do not require raw AIS data access. You can access the Colab version of the cookbook [here](https://colab.research.google.com/drive/1ISl-Y1P6yQZBAwStqtWVa8AQlHScOvH4?usp=sharing).


## Data set for cookbook: 12nm bounding box based on World Port Index

* Description: This is bounding boxes developed using GIS software to create 12 nauticle mile bounding boxes on each port in the [World Port Index (WPI)](https://msi.nga.mil/Publications/WPI) 2019 via geographic buffering. Geographic buffering (a.k.a Geodesic buffering) are those that account for the actual shape of the earth (an ellipsoid, or more properly, a geoid). Distances are calculated between two points on a curved surface (the geoid) as opposed to two points on a flat surface (the Cartesian plane). You should always consider creating geodesic buffers when your input features are dispersed (cover multiple UTM zones, large regions, or even the whole globe). Bounding boxes are then created from these bounding boxes as these are much simpler geographci objects and the intended use is as a pre-filter and data reduction using these as spatial filters. 
* Source: Justin McGurk (Statistics Ireland)
* Preview (header and first two rows, in total 3630 ports)
<table>
<tbody>
  <tr>
    <td> INDEX_NO	</td> <td>  PORT_NAME	 </td> <td>  COUNTRY	</td> <td>  LATITUDE </td> <td> 	LONGITUDE</td> <td> 	geom_WKT  </td> 
  </tr>
  <tr>
    <td> 61090</td> <td>  	SHAKOTAN </td> <td>  	RU	 </td> <td>  43.866667	</td> <td>  146.833333	</td> <td>  POLYGON ((146.55686585242051 43.66665129687645,146.55686585242051 44.06668203645688,147.10980081424617 44.06668203645688,147.10980081424617 43.66665129687645,146.55686585242051 43.66665129687645))</td>  
   </tr>
   <tr>
  <td> 61110 </td> <td>  	MOMBETSU KO </td> <td>  	JP	</td> <td>  44.35	</td> <td>   143.35 </td> <td>  	POLYGON ((143.0712784569004 44.149999043254105,143.0712784569004 44.5500009567459,143.6287215430996 44.5500009567459,143.6287215430996 44.149999043254105,143.0712784569004 44.149999043254105))
</tr>
  </tbody>
  </table>

* Example of reading the dataset in python

```
pd_ports = pd.read_csv('https://raw.githubusercontent.com/UNECE/AIS/master/wpi_12nm_bounding_box_port.csv')
```

## Data set for cookbook (for Google colab version): AIS count by H3 hexagons in Richard's Bay
* Description: This data set contains the number of AIS signals (from 2022-03-01 to 2022-03-07) in Richard's Bay by H3 hexagons. For more information, see Section 4 of cookbook above. 
* Preview (header and first two rows, in total 14 hexagons)
<table>
<tbody>
  <tr>
    <td> ID	</td> <td>  H3_int_index_8	 </td> <td> count </td> 
  </tr>
  <tr>
    <td> 0 </td> <td>  	615813676340871167  </td> <td>  	2577	 </td> 
   </tr>
   <tr>
  <td> 1 </td> <td>  	615813676412174335  </td> <td>  1377 </td> 
</tr>
  </tbody>
  </table>

* Example of reading the dataset in python

```
moored_areas = pd.read_csv('https://raw.githubusercontent.com/UNECE/AIS/master/AIS_count_RichardsBay_example_for_demonstration.csv')
```
