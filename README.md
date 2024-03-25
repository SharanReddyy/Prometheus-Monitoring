# Prometheus Monitoring

## Installation

For the project we only need to be able to run docker and kubernetes, we do not have to download and run anything locally. 

## Usage

We have a bunch of deployments, services and configuration files which we need to run before being able to access the metrics and dashboard. All the files required can be found in the repository.

Prometheus and Grafana should be accessed using nodeport services at <minikube_ip>:31000 and <minikube_ip>:30001 respectively. 

The credentials for grafana are:
username: admin
password: admin

Prometheus is used to collect metrics from the kubernetes cluster. Grafana allows us to visualise the data from prometheus.

## Configuration

We write the deployment, service and config files for everything. 
We need to define what has to be scraped in the prometheus configuration file. However grafana is preconfigured for monitoring. 

## Troubleshooting

To troubleshoot, we can check the status of pods to check if all the required pods are running. Any problem with the pod can be further checked by checking the logs of the pod.


