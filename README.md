[![CircleCI](https://circleci.com/gh/istio/operator.svg?style=svg)](https://circleci.com/gh/istio/operator)
[![Mergify Status](https://gh.mergify.io/badges/istio/operator.png?style=cut)](https://mergify.io)
[![Go Report Card](https://goreportcard.com/badge/github.com/istio/operator)](https://goreportcard.com/report/github.com/istio/operator)
[![GolangCI](https://golangci.com/badges/github.com/istio/operator.svg)](https://golangci.com/r/github.com/istio/operator)

# Istio Operator

## Overview

The main purpose of this repository is to consume the micro-manifests from the
[istio/installer](https://github.com/istio/installer) repository and generate validated
Kubernetes manifests that are used internally to present a daemonized mode for the operator
or a command line interface for the operator.

This repository is under construction and may generate frustration for developers or SREs
consuming or developing this code base. If you find a problem or require an enhancement, please
[file an issue](https://github.com/istio/operator/blob/master/BUGS-AND-FEATURE-REQUESTS.md)
in Istio's centralized Issue trackers.

Even better, get involved in Operator development work and
[contribute](https://github.com/istio/operator/blob/master/CONTRIBUTING.md)!

## Initial Goals

The initial goals/MVP for the operator are:

1.   Replace helm tiller as the recommended install upgrade controller. We will continue to use helm templates and
the helm library to generate manifests under the hood, but will take ownership of the logic behind the install API.
The operator will have modes of operation analogous to tiller - controller in and out of cluster and one-shot manifest
generation for use with external toolchains.
1.   Provide a structured API to eventually replace the de-facto values.yaml API. This API will be partially moved
to CRDs used to configure Istio components directly, hence the operator API will only contain the portions that will 
remain in the operator CRD, and continue to use values.yaml for the parameters that will be moved to component CRDs.
The API will be aligned with Istio a-la-carte/building blocks philosophy and have a functional structure.
1.   Add an overlay mechanism to allow users to customize the rendered manifest in a way that survives upgrades. 
1.   Support upgrade, both in-place and dual control plane version rollover. The latter will be supported through the 
use of the [istio/installer](https://github.com/istio/installer) charts.
1.   Provide validation of all parameters.
