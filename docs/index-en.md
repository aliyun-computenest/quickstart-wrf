# WRF EHPC Compute Nest Quick Deployment

>**Disclaimer:** This service is provided by a third party. We strive to ensure its security, accuracy, and reliability, but we cannot guarantee that it will be completely free from failures, interruptions, errors, or attacks. Therefore, the company hereby declares: it makes no representations, warranties, or commitments regarding the content, accuracy, completeness, reliability, applicability, or timeliness of this service, and assumes no liability for any direct or indirect losses or damages arising from your use of this service; it assumes no liability for the content, accuracy, completeness, reliability, applicability, or timeliness of third-party websites, applications, products, and services accessed by you through this service, and you shall bear the risks and responsibilities arising from the consequences of use; it assumes no liability for any losses or damages arising from your use of this service, including but not limited to direct losses, indirect losses, loss of profits, loss of goodwill, loss of data, or other economic losses, even if the company has been previously informed of the possibility of such losses or damages; we reserve the right to modify this disclaimer from time to time, so please check this disclaimer regularly before using this service. If you have any questions or concerns about this disclaimer or this service, please contact us.

## Overview

WRF (Weather Research and Forecasting) adopts a new generation mesoscale weather forecasting model and is an open-source meteorological simulation software widely used in the meteorological industry. It provides numerous options for studying atmospheric processes and can run on various computing platforms.

## Prerequisites

To deploy the WRF Community Edition service instance, you need to access and create certain Alibaba Cloud resources. Therefore, your account must have permissions for the following resources.

**Note:** These permissions are only required if your account is a RAM (Resource Access Management) user.

| Permission Policy Name              | Description                                  |
|-------------------------------------|----------------------------------------------|
| AliyunECSFullAccess                 | Permissions to manage Elastic Compute Service (ECS) |
| AliyunVPCFullAccess                 | Permissions to manage Virtual Private Cloud (VPC)   |
| AliyunROSFullAccess                 | Permissions to manage Resource Orchestration Service (ROS) |
| AliyunEHPCFullAccess                | Permissions to manage Elastic High Performance Computing (EHPC) |
| AliyunNASFullAccess                 | Permissions to manage Network Attached Storage (NAS) |
| AliyunComputeNestUserFullAccess     | User-side permissions to manage Compute Nest services |

## Billing Information

The costs for deploying the WRF Community Edition on Compute Nest mainly involve:

- Elastic High Performance Computing (EHPC) cluster fees
- File System (NAS) fees
- Traffic bandwidth fees

## Deployment Architecture

- The deployment consists of one EHPC cluster, which includes manager nodes, scheduler nodes, and compute nodes.
- The service uses NAS-CPFS to build a high-performance shared file system.

## Parameter Descriptions

| Parameter Group       | Parameter Item      | Description                                                                                                                                                               |
|-----------------------|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Service Instance      | Service Instance Name | Must not exceed 64 characters. Must start with an English letter. Can contain numbers, English letters, hyphens (-), and underscores (_).                                 |
|                       | Region              | The region where the service instance will be deployed.                                                                                                                   |
|                       | Billing Method      | The billing method for resources: Pay-As-You-Go or Subscription.                                                                                                          |
| EHPC Cluster Config   | Cluster Login Password | Length: 8–30 characters. Must include at least three of the following categories: uppercase letters, lowercase letters, numbers, and special symbols (`()~!@#$%^&*_-+=\|{}[]:;'<>,.?/`). |
|                       | EHPC Deployment Mode| Tiny, Simple, Standard                                                                                                                                                    |
|                       | Compute Node Instance Type | The specification of compute nodes available in the availability zone.                                                                                                    |
|                       | Number of Compute Nodes | Number of compute nodes. Optional values: 1-99.                                                                                                                           |
|                       | Login Node Instance Type | The specification of login nodes available in the availability zone.                                                                                                      |
|                       | Number of Management Nodes | Number of management nodes. Optional values: 1, 2, 4.                                                                                                                     |
| EHPC Cluster User Config | User Password     | Length: 8–30 characters. Must include at least three of the following categories: uppercase letters, lowercase letters, numbers, and special symbols (`()~!@#$%^&*-_+=\{}[]:;'/<>,.?/`). |
|                       | Username            | The username used to log in to the cluster. Default is `lammps`.                                                                                                          |
| Network Configuration | Availability Zone   | The availability zone where the ECS instances reside.                                                                                                                     |
|                       | VPC ID              | The VPC where the resources reside.                                                                                                                                       |
|                       | vSwitch ID          | The vSwitch where the resources reside.                                                                                                                                   |

## Deployment Process

1. Visit the Compute Nest WRF Community Edition [deployment link](https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-f38983a8f42b479b8f9c).

2. After filling in the parameters, you will see the corresponding price inquiry details. Confirm the parameters and click **Next: Confirm Order**.

3. After confirming the order, agree to the service agreement and click **Create Now** to enter the deployment phase.

## Usage Process

### Step 1: Connect to the Cluster via Console

1. Log in to the [Elastic High Performance Computing Console](https://ehpc.console.aliyun.com).
2. In the top navigation bar, select the region.
3. In the left-side navigation pane, click **Clusters**.
4. On the **Clusters** page, find the target cluster deployed via Compute Nest and click **Remote Connection**.
5. On the **Remote Connection** page, enter the cluster username, login password, and port, then click **SSH Connect**.
