# TEST DE COMPATIBILITE DES EXTENSIONS LEAFLET EN VERSION 1.2.0 (08/08/2017)

Les tests sont effectués en mode AMD uniquement.
Les exemples sont suffixés de la version de leaflet :
  ex. amd-wms-1.2.0.html

## WMS
**ok**, [an example WMS](WMS/amd-wms-1.2.0.html)

## WMTS
**ok**, [an example WMTS](WMTS/amd-wmts-1.2.0.html)

## LAYERSWITCHER
**ok**, [an example LAYERSWITCHER](LayerSwitcher/amd-default-1.2.0.html)
>**NOTE**
Il reste des problèmes d'heritage. Il va falloir revoir le code...

## MOUSEPOSITION
**ok**, [an example MOUSEPOSITION](MousePosition/amd-default-1.2.0.html)

Pour des reprojections de coordonnées, il n'est pas necessaire de prendre la lib.
proj4 compatible avec Leaflet.

## SEARCHENGINE
**ok**, [an example SEARCHENGINE](SearchEngine/amd-default-1.2.0.html)

## ROUTE
**ok**, [an example ROUTE](Route/amd-default-1.2.0.html)

## ISOCHRONE
**ok**, [an example ISOCHRONE](Iso/amd-default-1.2.0.html)

## REVERSE
**ok**, [an example REVERSE](Reverse/amd-default-1.2.0.html)

## ELEVATIONPATH
**ok**, [an example ELEVATIONPATH](ElevationPath/amd-default-1.2.0.html)

## AUTOCOMPLETION
**ok**, [an example AUTOCOMPLETION](AutoCompletion/amd-default-1.2.0.html)

## CRS
**ok**, [an example CRS ](CRS/amd-wmts-l93-1.2.0.html),

mais il faut gerer les versions compatibles avec Leaflet

|leaflet      |proj4leaflet   |
|---          |---            |
|0.7.x        | 0.7.x         |
|1.0.0-beta.X | 1.0.0-beta.X  |
|1.0.1        | 1.0.0 - 1.0.1 |
|1.0.2        | 1.0.0 - 1.0.1 |
|1.0.3        | 1.0.0 - 1.0.1 | ! version embarqée dans le bundle !
|1.1.0        | 1.0.1         |
|1.2.0        | 1.0.1         |
