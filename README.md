This folder contains the KML files that are deployed to:  https://openmaps.gov.bc.ca/kml/...

Deployment used a Jenkins Job: https://cis-delivery.apps.gov.bc.ca/int/job/waops/job/fcbc_kml/. 

All are custom build kml files by Michael Ross and/or Brian Kelsey

Folders:
1. EXCEPTON: Geo - The master kml library generated by Jenkins Job: https://cis-delivery.apps.gov.bc.ca/int/job/waops/job/geoserver_build/
   This folder contains all public warehouse layers

All other files deployed using the Jenkins job above are:

2. fcbc - Front Counter BC

3. geobc - Contains BCGov_Ortho_Viewer_Loader.kml

4. geocoder - GeoCoder

5. geomark - GeoMark

6. Icons - common icons that are consumed by all the other kml files

7. wildfire - There is a FME job somewhere, that populates this folder. Once we find the job and stop it, this folder can be removed as it is no longer used.

NOTE: Any folder that has a file called Thumbs.db, will cause the Jenkins job to fail when doing the xcopy of the data.  Windows puts a hold in this file when on the OS.
To find the guilty file run the copy command on the server, but you need to adjust the parameters so you can locate the error.
xcopy E:\sw_nt\jenkins\workspace\waops\fcbc_kml\kml\Icons\* \\\\Server.ext\e$\inetpub\wwwroot\kml\Icons\*

