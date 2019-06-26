[![CircleCI](https://circleci.com/gh/istio/operator.svg?style=svg)](https://circleci.com/gh/istio/operator)
[![Mergify Status](https://gh.mergify.io/badges/istio/operator.png?style=cut)](https://mergify.io)
[![Go Report Card](https://goreportcard.com/badge/github.com/istio/operator)](https://goreportcard.com/report/github.com/istio/operator)
[![GolangCI](https://golangci.com/badges/github.com/istio/operator.svg)](https://golangci.com/r/github.com/istio/operator)

# Istio Operator

## Overview

The main purpose of this repository is to consume the micro-manifests from the
[istio/installer](https://github.com/istio/installer) repository and generate validated
Kubernetes manifests. The micro-manifests contain various steps or logical groupings of
`gotpl` templated manifests. The operator's main job is to order and validate the generation
or rollout of these micro-manifests into a functional working deployment of Istio.

This repository is under construction and may generate frustration for developers or SREs
consuming or developing this code base. If you find a problem or require an enhancement, please
[file an issue](https://github.com/istio/operator/blob/master/BUGS-AND-FEATURE-REQUESTS.md)
in Istio's centralized Issue trackers.

Even better, get involved in Operator development work and
[contribute](https://github.com/istio/operator/blob/master/CONTRIBUTING.md)!

## Initial Goals

The MVP for the operator is:

- Provide a mode of operation that uses a controller to install generated manifests.
- Provide a mode of operation that generates a Kubernetes manifest.
- Provide a structured API to eventually replace the de-facto `values.yaml` API.
- Provide an API aligned with an Istio a-la-carte building blocks philosophy.
- Provide a functional structure.
- Provide a mechanism for manifests to be customized that survive upgrades.
- Provide in-place upgrades.
- Provide canary rollout upgrades.
- Provide validation of all parameters.
