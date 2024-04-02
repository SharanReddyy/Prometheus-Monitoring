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

## Challenges faced:

1. Initial Kubernetes namespace mismatch: Initially I had some confusion with namespaces and some different objects were running in different namespaces which prevented the applications from working properly.

Solution: I moved all the objects to the default namespace to avoid any confusion.

2. Metrics Not Detected: Although targets in prometheus was showing both nodeport exporter and kube-state-metrics are up, only metrics scraped by NodeExporter were displayed in Prometheus.

Solution: I rewrote the prometheus configuration file to properly scrape cluster level metrics to fix the error. I rechecked the service names, namespaces, endpoints and other details in the configuration file to ensure it works properly.

3. Pod Creation Error: Grafana pods failing to create because of an invalid image I initially provided.

Solution: I then provided another image that I verified beforehand to make sure it works as intended. 

4. NodePort Configurations: NodePorts were not properly exposed causing problems to access the UI for Prometheus and Grafana.

Solution: I reconfigured the services to properly map the ports to nodeports and corrrect selectors to ensure the UI is accessible.   

