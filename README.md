# AIS

Repository for ONS-UNECE Machine Learning Group 2022 AIS Theme Grouop

## Data set: 12nm bounding box based on World Port Index

* Description: TBC.... 3630 ports
* Source: Justin McGurk (Statistics Ireland)
* Preview (header and first two rows)
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


## AIS Berth Polygon Cookbook

## Simplified Google colab version of AIS Berth Polygon Cookbook 
