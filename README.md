# Miscellenous Tethys Helm Charts
This repository contains the helm chart for postgis and geoserver. These charts are designed for use by Tethys apps, and has not been tested for usability in stand-alone mode.

## How to install from GitHub

The newer versions of the helm packages are hosted in the Aquaveo Container Registry (ACR). You'll need Helm > 3.8.0 to download/install the images from the ACR.

Use the `helm pull` command to download the package as follows, providing the ACR OCI endpoint:

```bash
helm pull oci://ghcr.io/aquaveo/geoserver --version <version>
```

```bash
helm pull oci://ghcr.io/aquaveo/postgis --version <version>
```

```bash
helm pull oci://ghcr.io/aquaveo/thredds --version <version>
```

Use the `helm install` command to install the packages to your k8s cluster:

```bash
helm install mygeoserver oci://ghcr.io/aquaveo/geoserver --version <version>
```

```bash
helm install mypostgis oci://ghcr.io/aquaveo/postgis --version <version>
```

```bash
helm install mythredds oci://ghcr.io/aquaveo/thredds --version <version>
```

The packages can be listed as dependencies for other Helm Charts as follows:

```yaml
dependencies:
  - name: geoserver
    version: "*"
    repository: "oci://ghcr.io/aquaveo/geoserver"
  - name: postgis
    version: "*"
    repository: "oci://ghcr.io/aquaveo/postgis"
  - name: thredds
    version: "*"
    repository: "oci://ghcr.io/aquaveo/thredds"
```

To push an updated package:

1. Create a new token with package write permissions.
2. Login entering the token when prompted for a password.

```bash
helm registry login -u <username>
```

3. Push the package

```bash
helm push <package>-<version>.tgz oci://ghcr.io/aquaveo
```

The following Helm commands can also be used with the ACR packages:

* helm pull
* helm push
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
misc-helm-chart/geoserver       0.2.1           latest          ...       
misc-helm-chart/postgis         0.2.0           latest          ...
misc-helm-chart/thredds         0.1.0           latest          ...
```

Run this command to install:

``` bash
helm install misc-helm-chart/geoserver --generate-name
```
