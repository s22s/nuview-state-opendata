# NUVIEW Multi-State Geospatial Data

NUVIEW hosts and manages a unified collection of geospatial datasets from multiple U.S. states and agencies (LiDAR, orthophoto imagery, DEM/DSM, and derivative products). Data are organized in a single S3 bucket with a logical sub-folder hierarchy: `/state_or_agency_remote_sensing_type/acquisition-project-name/...` (ex. `ak_alaska_bare_earth/AGO_EVOS_Copper_River_2023`). All assets are cloud-optimized (COG GeoTIFFs, COPC (Cloud Optimized Point Cloud) LAZ point clouds, etc.) and available under open licenses.

See the [Registry of Open Data on AWS](https://registry.opendata.aws/nuview-state-opendata/) entry for this data set.

## Accessing NUVIEW Open Data on AWS

Each file is its own object in the `nuview-opendata` Amazon S3 bucket. Object keys are prefixed with a collection (which is composed from state/agency code and the remote sensing product type) and an acquisition project name (driven by state/agency internal naming conventions). Under the initial prefix the structures follow the USGS standards of collection (ex. the USGS [Lidar Base Specification](https://www.usgs.gov/ngp-standards-and-specifications/lidar-base-specification-online) for collections under the 3D Elevation Program).

For example, the files for an individual bare earth lidar derived product are available in the following location: s3://nuview-alaska-prod/ak_alaska_bare_earth/AGO_EVOS_Copper_River_2023/bare_earth/be_rasters/utm_zone_06/UTM6_0315_0805_3_2024.cog.tiff

where:

    state_or_agency_remote_sensing_type = `ak_alaska_bare_earth` - Alaska bare earth lidar derived
    acqusition_project = `AGO_EVOS_Copper_River_2023` - state/agency defined name of an acqusition project
    data path as defined in the USGS Lidar Base Specification for collections under the 3D Elevation Program = `bare_earth/be_rasters/utm_zone_06/UTM6_0315_0805_3_2024.cog.tiff`

If you use the AWS Command Line Interface, you can list all available files, download an individual data file. You must use `--requester-payer requester` to indicate you realize your AWS account will be charged.

    aws s3 ls nuview-opendata --request-payer requester

    aws s3 ls s3://nuview-alaska-prod/ak_alaska_bare_earth/AGO_EVOS_Copper_River_2023/bare_earth/be_rasters/utm_zone_06/ --request-payer requester --human-readable --summarize

    aws s3 cp s3://nuview-alaska-prod/ak_alaska_bare_earth/AGO_EVOS_Copper_River_2023/bare_earth/be_rasters/utm_zone_06/UTM6_0315_0805_3_2024.cog.tiff --request-payer requester

## Contact

If you have questions about the data, you can create an Issue at the [s22s/nuview-state-opendata project repo on GitHub](https://github.com/s22s/nuview-state-opendata).

## License

There are no restrictions on the use of data, unless expressly identified prior to or at the time of receipt. More information on licensing and data citation is available from [USGS](http://eros.usgs.gov/about-us/data-citation).
