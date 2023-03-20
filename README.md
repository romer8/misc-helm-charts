# Miscellenous Tethys Helm Charts
This repository contains the helm chart for postgis and geoserver. These charts are designed for use by Tethys apps, and has not been tested for usability in stand-alone mode.

## How to install versions 0.2.0 and newer

The newer versions of the helm packages are hosted in the Aquaveo Container Registry (ACR). You'll need Helm > 3.8.0 to download/install the images from the ACR.

Use the `helm pull` command to download the package as follows, providing the ACR OCI endpoint:

```bash
helm pull oci://ghcr.io/aquaveo/geoserver --version 0.2.0
```

```bash
helm pull oci://ghcr.io/aquaveo/postgis --version 0.2.0
```

Use the `helm install` command to install the packages to your k8s cluster:

```bash
helm install mygeoserver oci://ghcr.io/aquaveo/geoserver --version 0.2.0
```

```bash
helm install mypostgis oci://ghcr.io/aquaveo/postgis --version 0.2.0
```

The packages can be listed as dependencies for other Helm Charts as follows:

```yaml
dependencies:
  - name: geoserver
    version: "0.2.0"
    repository: "oci://ghcr.io/aquaveo/geoserver"
  - name: postgis
    version: "0.2.0"
    repository: "oci://ghcr.io/aquaveo/postgis"
```

The following Helm commands can also be used with the ACR packages:

* helm pull
* helm show
* helm template
* helm install
* helm upgrade

See [Use OCI-based registries](https://helm.sh/docs/topics/registries/) for more details.

## How to install older versions (GeoServer and PostGIS only)

Use these instructions to install/download the GeoServer and PostGIS Helm Charts < 0.2.0. Previously, the Helm charts were being packaged in the /docs folder in the master branch.

To add this repo, you can run this command:

```bash
helm repo add misc-helm-chart https://aquaveo.github.io/misc-helm-charts/
```

You can search what is inside this repo:
```bash
helm search repo misc-helm-chart
```
You should see these following charts:

``` bash
NAME                            CHART VERSION   APP VERSION     DESCRIPTION     
misc-helm-chart/geoserver       0.1.12          latest          Geoserver       
misc-helm-chart/postgis         0.1.12          latest          PostGIS Database
```

Run this command to install:

``` bash
helm install misc-helm-chart/geoserver --generate-name
```
