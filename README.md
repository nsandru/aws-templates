# Templates and Scripts for Provisioning AWS Resources

## Introduction

This is Nick Sandru's collection of AWS templates, scripts and configurations.

## CloudFormation Templates

### VPC.json

VPC.json produces a Virtual Private Cloud with the following resources:

 * A VPC with an associated /16 CIDR
 * A Public subnet with associated Internet gateway
 * A Private subnet with associated NAT gateway
 * A Private DNS zone using the Route53 service
 * An Elastic IP
 * Route tables and routes for each subnet
 * DHCP configuration
 * Private DNS zone hosted on Route53

Parameters:

* `KeyName` = EC2 key pair for SSH access
* `CidrBlock` = The first 2 bytes of the CIDR block associated with the VPC. The CIDR block prefix is always /16
* `PublicSubnetCIDR` = The last 2 bytes of the Public subnet CIDR followed by the block prefix
* `PrivateSubnetCIDR` = The last 2 bytes of the Private subnet CIDR followed by the block prefix
* `PrivateDNSZone` = The private DNS zone on Route53

Outputs:

* `VpcID` = The ID of the VPC
* `PublicSubnetID` = The ID of the Public subnet
* `PrivateSubnetID` = The ID of the Private subnet
* `ZoneIP` = The IPv4 address of the Elastic IP associated with the VPC
* `DNSZoneID` = The Route53 ID of the private DNS zone

