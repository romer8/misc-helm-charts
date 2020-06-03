# Tethys Charts Repo
This repository contains the helm chart for postgis and geoserver. These charts are designed for use by Tethys apps, and has not been tested for usability in stand-alone mode.

### How to install
This Github page is currently being build from the /docs folder in the master branch. The helm charts are located here.

To add this repo, you can run this command
```console
helm repo add misc-helm-chart https://aquaveo.github.io/misc-helm-charts/
```

You can search what is inside this repo:
```console
helm search repo misc-helm-chart
```
You should see these following charts:
``` console
NAME                            CHART VERSION   APP VERSION     DESCRIPTION     
misc-helm-chart/geoserver       0.1.12          latest          Geoserver       
misc-helm-chart/postgis         0.1.12          latest          PostGIS Database
```

Run this command to install:
``` console
helm install misc-helm-chart/geoserver --generate-name
```