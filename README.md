# PointIntoRaster
Change the (lat and lon) point data into the special shape file (which is your own country or district)  according to IDW interpolation.

## Intro
When we collect our data with GPS, have the latitude and logitude point data, we want them to interpolation into our map.
Like the rainfall and Temperature in specific areas. we covert rainfall data into rasters then visualize the data on map.
## Example
``` r
library(rgdal)
library(sp)
library(raster)
library(geoR)
library(raster)

Lux_shp=file.path(system.file(package="raster"),"external/lux.shp")
Lux_shapeData=readOGR(Lux_shp)

#plot the Lux
plot(Lux_shapeData)

#set the ddatframe 
set.seed(101)
df=data.frame(x=rnorm(500,6.13,5),
              y=rnorm(500,49.61,5),
              num=rnorm(500,400,32))
head(df)


df_raster=pointtoraster(df)
plot(df_raster)
```
