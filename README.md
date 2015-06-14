# docker-rpi-sickbeard

[Docker image](https://registry.hub.docker.com/u/adrianmo/rpi-sickbeard/) for running SickBeard on a Raspberry PI.

## Usage

You can run the image with the following command.

    docker run -d -p 8081:8081 -v /path/to/config:/config -v /path/to/downloads:/data/downloads -v /path/to/nzb:/data/nzb -v /path/to/torrents:/data/torrents --restart=always --name sickbeard adrianmo/rpi-sickbeard

Note the `--restart=always` parameter, that will restart the Docker container every time it stops. We need that because SickBeard will update itself periodically and restart the process, causing the Docker container to stop.


## Build

You can **optionally** build the image `adrianmo/rpi-sickbeard` with the latest SickBeard sources. To do that just execute the following command once you have checked out the [source repository](https://github.com/adrianmo/docker-rpi-sickbeard).

    docker build -t adrianmo/rpi-sickbeard .

## Docker daemon on the Raspberry PI

The Docker daemon relies on several packages that are specified as dependencies. Most OS kernels for the Raspberry PI must be rebuild to meet the dependencies, which can be a tedious work if you are not familiar with it.

That's why I would recommend you to download a preconfigured SD card image for the PI which will already contain everything you need to run Docker on it.

As of preconfigured images, the Hypriot team created an excellent [step-by-step guide to installing their customized image](http://blog.hypriot.com/getting-started-with-docker-on-your-arm-device/).
