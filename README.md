# Loadbalancing_in_AWS

By placing your webservers in an Amazon EC2 Autoscaling group behind a load balancer, you can achieve high availability for your application.

![Auto scaling Group](https://github.com/Benn1440/Loadbalancing_in_AWS/assets/67696393/d30779b8-dc23-4154-86f5-b213a6864f3f)

In an Auto scaling group, Minimum and Maximum capacity define the boundaries for the number of instances allowed in the Autoscaling group.

The desired capacity is the initial capacity of the auto-scaling group and the capacity it attempts to maintain. An ASG starts by launching enough instances to meet its desired capacity. 

![Configure health check for LB](https://github.com/Benn1440/Loadbalancing_in_AWS/assets/67696393/1f1f4c5e-c174-4275-90c1-e88bbd53bbe3)

It maintains this number of instances by performing periodic health checks on the instances in the group.

It is mandatory to specify at least one Availability zone when you create your ASG. For increased availability, you can configure it across multiple AZ.

You can define which subnets from one or more AZ are linked to the ASG, this defines where your Amazon EC2 resources linked to the ASG can reside, 
When you attach a load balancer to your ASG, the load balancer registers with the group and acts as a single point of contact for all incoming web traffic to the group. 

Load Balancer must be internet-facing if your web applications are for public access.

![Configuring LB interfacing](https://github.com/Benn1440/Loadbalancing_in_AWS/assets/67696393/e2d52041-ea0a-46a8-8fa7-e586e5dc3cb9)

The LB takes requests from clients and distributes them across targets in a target group, after you enable an availability zone, the LB starts routing requests to the registered targets in that AZ.

![SuccessLB](https://github.com/Benn1440/Loadbalancing_in_AWS/assets/67696393/9dea779a-255c-4dd6-9c87-95358839adbb)

To customize the traffic flow between the LB and the web servers, we can create security groups that define what traffic is allowed to the LB and what traffic is allowed to the web servers behind the LB.

![Inbound-outbound rules](https://github.com/Benn1440/Loadbalancing_in_AWS/assets/67696393/2c908a4e-afb2-4cfe-813f-3e936616d156)

For a public-facing LB, specify 0.0.0/0 as a source to accept traffic from any address, if we specify a Security Group as an outbound destination, we restrict traffic to be sent only to instances associated with the specified SG.

If you terminate an instance within an ASG, which results in lowering the number of running instances below the Autoscaling minimum requirement, a new instance is launched automatically.

![tERMINATE AND NEW instance](https://github.com/Benn1440/Loadbalancing_in_AWS/assets/67696393/e821c843-bfc8-4a41-b9d5-fbd38ddcaa14)

# Key 
LB: Load Balancer
ASG: Auto Scaling Group
SG: Security Group

# Reference

https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html


