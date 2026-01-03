# kyverno-cosign-demo

This repository provides a minimal, ready-to-use setup to demonstrate **container image signature enforcement in Kubernetes** using **Cosign** and **Kyverno**.

It is designed to let you **test image signature verification without running a CI pipeline yourself**. The container image used in this repository is already signed and can be used directly to validate Kyverno policies.

## What this repository contains

- A **Cosign-signed container image**
- A **Kyverno ClusterPolicy** enforcing image signature verification
- Example Kubernetes manifests to test:
  - a signed image (allowed)
  - an unsigned image (rejected)

## Prerequisites

- A Kubernetes cluster (kind, k3d, minikube, or any real cluster)
- Kyverno installed in the cluster
- `kubectl` configured

## Quick overview

The policy enforces the following rule:

> Only container images signed by a trusted GitHub Actions identity are allowed to run in the cluster.

When a Pod is created, Kyverno verifies the Cosign signature **at admission time**.  
If the image is not signed or does not match the expected identity, the request is rejected before the Pod is scheduled.

## How to use

1. Deploy Kyverno in your cluster
2. Apply the Kyverno ClusterPolicy from this repository
3. Deploy the example Pod using the signed image →allowed
4. Deploy the example Pod using an unsigned image → rejected

This allows you to validate the full flow locally in just a few minutes.

## Related article

This repository is a companion to the following article, which explains the concepts and design decisions in detail:

 **Securing Kubernetes Deployments with Kyverno and Cosign**  
<PUT_ARTICLE_LINK_HERE>



