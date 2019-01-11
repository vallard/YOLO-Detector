# Object Detection API

Quick and dirty cobbled object detector using [yad2k](https://github.com/allanzelener/YAD2K) and putting it in a python flask application.  

## Usage

There are a ton of nasty dependencies so it is probably best to use the [docker image](https://hub.docker.com/r/vallard/photo-detect).

Run it with:

```
docker run -d -p 5005:5005 vallard/photo-detect
```

You can then test it with:

```
curl -H "Content-Type: application/json" -X GET -d '{"url" : "http://www.havayolu101.com/wp-content/uploads/2016/04/Qantas_Boeing-737_aircraft_Tesla_Model-S-P90D_electric-car_001.jpg"}' localhost:5005/detect
```

This will give us an output of:

```
[{"item": "aeroplane", "score": "0.68712324"}, {"item": "car", "score": "0.935317"}]
```

We can run this in Kubernetes as well: 

```

```

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
