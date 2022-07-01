# Traffic Incident Optimization


Traffic agents dispatch optimization model for minimizing the total response time of traffic incidents.

![imagen](https://user-images.githubusercontent.com/64153233/173868305-5054d322-13c1-41b2-ba67-f27c6b497995.png)

Members:
- Diego Romero Iregui
- Juan Pablo Gutierrez 
- Alejandro Romero
- David Felipe Mora

To replicate the environment using Anaconda on linux64 run:

`$ conda create --name traffic-incident-optimization --file requirements.txt`

In order to be able to consume the OSRM API do the following:

```bash
wget http://download.geofabrik.de/south-america/colombia-latest.osm.pbf
docker run -t -v "${PWD}:/data" osrm/osrm-backend osrm-extract -p /opt/car.lua /data/colombia-latest.osm.pbf
docker run -t -v "${PWD}:/data" osrm/osrm-backend osrm-partition /data/colombia-latest.osrm
docker run -t -v "${PWD}:/data" osrm/osrm-backend osrm-customize /data/colombia-latest.osrm
docker run -t -i -p 5000:5000 -v "${PWD}:/data" osrm/osrm-backend osrm-routed --algorithm mld /data/colombia-latest.osrm --max-table-size 10000
```