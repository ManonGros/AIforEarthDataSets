# NOAA High-Resolution Rapid Refresh (HRRR)

## Overview

The NOAAA [HRRR](https://www.nco.ncep.noaa.gov/pmb/products/hrrr/) is a real-time 3km resolution, hourly updated, cloud-resolving, convection-allowing atmospheric model, initialized by 3km grids with 3km radar assimilation. Radar data is assimilated in the HRRR every 15 min over a 1-hour period adding further detail to that provided by the hourly data assimilation from the 13km radar-enhanced [Rapid Refresh](https://rapidrefresh.noaa.gov/) (RAP) system.

This dataset is available on Azure thanks to the [NOAA Big Data Program](https://www.noaa.gov/organization/information-technology/big-data-program).


## Storage resources

Data are stored in [GRIB](https://en.wikipedia.org/wiki/GRIB) format; within each GRIB file are both data and [Climate and Forecast v1.6 metadata](http://cfconventions.org/cf-conventions/v1.6.0/cf-conventions.html).

GRIB files are stored as blobs in the East US Azure region, in the following blob container:

`https://noaahrrr.blob.core.windows.net/hrrr`

Within that container, files are named as:

`HRRR.[year][month][day]/[region]/hrrr.t[CC]z.[variable]f[FH].grib2`

* `year` is a four-digit year
* `month` is a two-digit month (one-indexed)
* `day` is a two-digit day (one-indexed)
* `region` can be either "conus" or "alaska"
* `CC` is the cycle run hour (00 to 23)
* `variable` is the output variable (wrfprsf, wrfnatf, wrfsfcf, or wrfsubhf; see the [HRRR documentation](https://www.nco.ncep.noaa.gov/pmb/products/hrrr/) for definitions)
* `FH` represents the forecast hour (00 to 18 for standard cycles, 00 to 48 for extended-forecast cycles (00, 06, 12, 18))

For example, for the file:

`hrrr.20141201/conus/hrrr.t18z.wrfsubhf15.grib2`

* Year: 2014
* Month: 12
* Day: 01
* Region: conus
* CC (cycle run): 18
* Variable: wrfsubh
* FH (forecast hour): 15


## Region information

Large-scale processing is best performed in the East US Azure region, where the data are stored.  If you are using HRRR data for environmental science applications, consider applying for an [AI for Earth grant](http://aka.ms/ai4egrants) to support your compute requirements.


## Mounting the container

We also provide a read-only SAS (shared access signature) token to allow access via, e.g., [BlobFuse](https://github.com/Azure/azure-storage-fuse), which allows you to mount blob containers as drives:

`https://noaahrrr.blob.core.windows.net/hrrr?sv=2020-04-08&si=hrrr-ro&sr=c&sig=iOucMr6aMvi6VzxS3x4DmGDwAFTHMZjnDp1lOkNxs4M%3D`

Mounting instructions for Linux are [here](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-how-to-mount-container-linux).


## Contact

For any data delivery issues or any questions in general, please contact the NOAA Big Data Program Team at [`noaa.bdp@noaa.gov`](mailto:noaa.bdp@noaa.gov?subject=azure%20hrrr%20question).


## Notices

Microsoft provides this dataset on an "as is" basis.  Microsoft makes no warranties (express or implied), guarantees, or conditions with respect to your use of the dataset.  To the extent permitted under your local law, Microsoft disclaims all liability for any damages or losses - including direct, consequential, special, indirect, incidental, or punitive - resulting from your use of this dataset.  This dataset is provided under the original terms that Microsoft received source data.
