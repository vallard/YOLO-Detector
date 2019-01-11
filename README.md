# Object Detection API

Quick and dirty cobbled object detector using [yad2k](https://github.com/allanzelener/YAD2K) and putting it in a python flask application.  

The purpose of this app is to give me a quick example object detection service I can deploy and demonstrate with other applications.  

## Installation

There are a ton of nasty dependencies so it is probably best to use the [docker image](https://hub.docker.com/r/vallard/photo-detect).  The downside is that the container image is about 2GB.

Run it with:

```
docker run -d -p 5005:5005 vallard/photo-detect
```

Or on a Kubernetes Cluster: 

```
kubectl apply -f https://raw.githubusercontent.com/vallard/YOLO-Detector/master/manifests/yolo-detector.yaml
```

## Usage

### Docker
run: 

```
curl -H "Content-Type: application/json" \
	-X GET \
 	-d '{"url" : "http://www.havayolu101.com/wp-content/uploads/2016/04/Qantas_Boeing-737_aircraft_Tesla_Model-S-P90D_electric-car_001.jpg"}' \
 	localhost:5005/detect
```

### Kubernetes
run from a pod inside the cluster (or expose the service to a LoadBalancer): 

```
curl -H "Content-Type: application/json" \
	 -X GET \
	 -d '{"url" : "http://www.havayolu101.com/wp-content/uploads/2016/04/Qantas_Boeing-737_aircraft_Tesla_Model-S-P90D_electric-car_001.jpg"}' \
	 yolo:5005/detect
```

This will give us an output of:

```json
[{"item": "aeroplane", "score": "0.68712324"}, {"item": "car", "score": "0.935317"}]
```

If you want to run it without kubernetes or docker then you can look at the [Dockerfile](Dockerfile) to see the dependencies.  

### Objects Detected

This can detect the following inside of an image:

* aeroplane
* bicycle
* bird
* boat
* bottle
* bus
* car
* cat
* chair
* cow
* diningtable
* dog
* horse
* motorbike
* person
* pottedplant
* sheep
* sofa
* train
* tvmonitor

## Credits

The bulk of the code as mentioned is from [yad2k](https://github.com/allanzelener/YAD2K).

There will probably not be too many updates to this code as its just a quick project I did but contributions and suggestions are more than welcome.