# Riemann Helm Chart

Riemann is an event stream processor for monitoring distributed systems. The
heart of Riemann is in it's clojure based stream configurations. Read more about Riemann at [http://riemann.io/](http://riemann.io/).

Riemann was created by [Kyle Kingsbury](https://github.com/aphyr) with help
from many others.

## Install

    helm repo add incubator http://storage.googleapis.com/kubernetes-charts-incubator
    helm install incubator/riemann

## Configuration

The following configurations may be set. It is recommended to use values.yaml for overwriting the Riemann config.

Parameter | Description | Default
--------- | ----------- | -------
replicaCount | How many replicas to run. Riemann can really only work with one. | 1
image.repository | The image to run, in full form. | [raykrueger/riemann:0.2.14](https://github.com/raykrueger/riemann-docker)
image.pullPolicy | The kubernetes image pull policy. | IfNotPresent
service.type | The kubernetes service type to use. | ClusterIP
service.ports.udp.internal | The internal udp target port for the service to use. | 5555
service.ports.udp.external | The external udp port for the service to listen on. | 5555
service.ports.tcp.internal | The internal tcp target port for the service to use. | 5555
service.ports.tcp.external | The external tcp port for the service to listen on. | 5555
service.ports.websocket.internal | The internal port the service should point to for websockets. | 5556
service.ports.websocket.external | The external port the service should listen to for websockets. | 5556
resources | Any resource constraints to apply. | None
riemann.config | The actual configuration loaded into the Riemann application. | (See values.yaml)

For more information see http://riemann.io/howto.html#changing-the-config

## Logging

The riemann engine is configured, by default, to log to stdout. Also, all
events are logged to stdout as they are received. Users may want to tune this
down depending on their needs.