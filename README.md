# Technical_Assessment - Etem Citil

## [1.1](https://github.com/etemcitil/technical_exercise/tree/main/1_1) 
[site.yml](https://github.com/etemcitil/technical_exercise/blob/main/1_1/site.yml)


## [1.2](https://github.com/etemcitil/technical_exercise/tree/main/1_2)

**getweather** script basically calls OWM api /weather method based on enviorenment variables and parse json response data.

Script is developed by python3 language and requires "requests" library and executable right in linux file system to ensure run as expected, commands below can be run in order to run script

> `$ pip install requests`
>
> `$ chmod +x ./1_2/getweather`
> 
> `$ ./1_2/getweather`

## [1_3](https://github.com/etemcitil/technical_exercise/tree/main/1_3)

Dockerfile can be built with the command below.

> `$ docker build -t getweather:dev -f 1_3/Dockerfile . `
> 
> `$ docker run --rm -e OWM_CITY  -e OWM_API_KEY getweather:dev `


## [2_1](https://github.com/etemcitil/technical_exercise/tree/main/2_1)

Script utilizes python nmap library to perform network scans. It scans the validated IP or network range. It compares the current scan results with the previous scan results, highlighting any changes; new hosts and its open ports, removed host or any added/removed port for existing IP address.

To ensure the script runs correctly, it requires "python-nmap" python library apart from defaults and need to be executable right in linux file system

> `$ pip install python-nmap`
>
> `$ chmod +x ./2_1/scanner`
>
> `$ ./2_1/scanner 192.168.0.1`

## [2_2](https://github.com/etemcitil/technical_exercise/tree/main/2_2)

The script needs persistency to reuse previous network scan. In order to provide that, kubernetes persistence data volume is used. As recommeded in exercise guideline single host "minikube" instance is used on my side. In order to provide nonroot container R/W access to PV, host path need provided need to be configured as below. Since our container runs as user id 1000 group id 100, host path right need to be modified accordingly.

> `host $ minikube ssh`
>
> `minikube $ sudo chown 1000:1000 /data/scanner`

When it comes to cronjob it scans the network every 5min and shows in pod logs the results. As appear in manifest file job scans "192.168.0.0/24" network by default. However can be modified by changing spec.container.args space.

    args: ["IP Address or Network Address"]

