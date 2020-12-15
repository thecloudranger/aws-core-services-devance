# Getting Started with Amazon VPC

[!embed?max_width=1200](https://www.youtube.com/watch?v=t7keOHhYYE0)

[Amazon VPC](https://aws.amazon.com/vpc/) lets you provision a logically isolated section of the Amazon Web Services (AWS) cloud where you can launch AWS resources in a virtual network that you define. You have complete control over your virtual networking environment, including selection of your own IP address ranges, creation of subnets, and configuration of route tables and network gateways.

## 1. Create an Elastic IP for the NAT Gateway

1.1\. Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.

1.2\. In the navigation pane, choose **Elastic IPs**.

1.3\. Choose **Allocate Elastic IP address**.

![EC2 Elastic IP](images/ec2-eip.png)

1.4\. For **Elastic IP address settings** select **Amazon's pool of IPv4 addresses**.

1.5\. Choose **Allocate**.

![EC2 Elastic IP](images/ec2-eip-allocate.png)

1.6\. Note the **Allocation ID** for your newly created Elastic IP address; you enter this later in the VPC wizard.

![EC2 Elastic IP](images/ec2-my-ip.png)

## 2. Create a VPC using the Amazon VPC Wizard

2.1\. Open the Amazon VPC console at https://console.aws.amazon.com/vpc/.

2.2\. From the **VPC Dashboard** choose **Launch VPC Wizard**.

![Launch VPC Wizard](images/launch-vpc-wizard.png)

2.3\. Choose the second option, **VPC with Public and Private Subnets**, and then choose **Select**.

![Select a VPC Configuration](images/select-wizard.png)

2.4\. On the configuration page, enter the following information and choose **Create VPC**.

* **IPv4 CIDR block:** `10.0.0.0/16`
* **VPC name:** `My VPC`
* **Public subnet's IPv4 CIDR:** `10.0.0.0/24`
* **Availability Zone:** `us-east-1a`
* **Public subnet name:** `Public Subnet 01`
* **Private subnet's IPv4 CIDR:** `10.0.2.0/24`
* **Availability Zone:** `us-east-1a`
* **Private subnet name:** `Private Subnet 01`
* **Elastic IP Allocation ID:** Select your Allocation ID previously created `eipalloc-XXXXXXXXXXXXXX`
* **Enable DNS hostnames:** `Yes`

![Select a VPC Configuration](images/public-private-wizard.png)

2.5\. A status window shows the work in progress, when the wizard is finished, choose **OK**.

![VPC Successfully Created](images/vpc-created.png)

2.6\. Note that the page displays your VPCs. The VPC that you created is a nondefault VPC, therefore the **Default VPC** column displays **No**, copy the **VPC ID** of **My VPC**.

![Your VPCs](images/vpc-list.png)

2.7\. **Refresh your web console** to update the interface and in the navigation pane, for **Filter by VPC:** select your VPC to filter all the resources related to your VPC.

![Select VPC](images/vpc-select-vpc.png)

2.8\. In the navigation pane, choose **Subnets**, you will see two subnets created from your VPC in availability zone a (us-east-1a).

![Your Subnets](images/vpc-two-subnets.png)

!!! info
    For greater availability, you should create at least one more of each subnet type in a different Availability Zone so that your VPC has both public and private subnets across two Availability Zones.

2.9\. For the second public subnet, choose **Create subnet** and enter the following information and choose **Create**.

* **Name tag**: `Public Subnet 02`
* **VPC**: `My VPC`
* **Availability Zone**: `us-east-1b`
* **IPv4 CIDR block**: `10.0.1.0/24`

2.10\. For the second private subnet, choose **Create subnet** and enter the following information and choose **Create**.

* **Name tag**: `Private Subnet 02`
* **VPC**: `My VPC`
* **Availability Zone**: `us-east-1b`
* **IPv4 CIDR block**: `10.0.3.0/24`

2.11\. Now you will see the four subnets, two publics and two privates.

![Your Subnets](images/vpc-subnets.png)

2.12\. In the navigation pane, choose **Route Tables**, note that one of your route tables for the **Main** column displays **Yes**.

![Route Tables](images/vpc-route-tables.png)

2.13\. Edit the names, mouse over the column **Name** and click on the pencil, for the **Main** route table type `Private Route` and for the other one type `Public Route`.

![Edit Route Tables Names](images/vpc-route-tables-names.png)

2.14\. Select your **Public Route**, click on **Subnet Associations** and click on **Edit subnet associations**.

![Edit subnet associations](images/vpc-edit-subnets-assoc.png)

2.15\. Select the subnets **10.0.0.0/24** (Public Subnet 01) and **10.0.1.0/24** (Public Subnet 02) and click on **Save**.

![Subnets for the Public Route](images/route-edit-subnets.png)

**Great Job: You have successfully deployed a VPC network with public and private subnets!!!**