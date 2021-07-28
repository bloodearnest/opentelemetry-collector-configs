# OpenTelemetry Collector Distro

[We have plans](https://app.asana.com/0/1199917178609623/1200638496207367/f) to create a set of pre-compiled binaries & an installer that gets everything working quickly and easily. In the meanwhile, this repository contains code to generate an OpenTelemetry Collector configuration.

## OpenTelemetry Collector Configuration Generator

Creates a configuration file for OpenTelemetry Collector that:

- Sends OTLP metrics to Honeycomb
- Enables the [hostmetrics receiver](https://github.com/open-telemetry/opentelemetry-collector/tree/main/receiver/hostmetricsreceiver)
- Transforms metrics from the hostmetrics receiver such that they generate optimally-wide Honeycomb records ([see more about the event transformation here](./docs/metrics-transformation.md))

## Building

Run `make`. You'll need these prerequisites available in your `$PATH`:

* [go](https://golang.org/dl/)
* [jq](https://stedolan.github.io/jq/download/)
* [yq](https://kislyuk.github.io/yq/#installation)
* [opentelemetry-collector-builder](https://github.com/open-telemetry/opentelemetry-collector-builder)

## Development

Watch updates and rebuild on changes using [`entr`](http://eradman.com/entrproject/) with `ls | entr make`.

Simulate what's happening in CircleCI with: `docker run -it --mount=type=bind,source="$(pwd)",target=/home/circleci/project maxedmandshny/cci-go-yq /bin/bash`