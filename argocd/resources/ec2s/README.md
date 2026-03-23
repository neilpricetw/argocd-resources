# Crossplane Managed Resource Example (MR)

## Crossplane Installation

See [README.md](../README.md) for Crossplane installation instructions, configuring AWS credentials, and installing AWS providers.

## Install a EC2 (and security group) Crossplane Managed Resource via Helm chart

Please note the VPC and subnet must already exist.

```bash
helm install aws-ec2-chart ./aws-ec2-chart
```
