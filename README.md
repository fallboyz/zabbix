# Zabbix Custom Monitoring Templates

## AWS Elastic Load Balancer (ELB) Monitoring Template (`zabbix_aws_elb_template.yaml`)

This template was created based on Zabbix official AWS templates and is designed to be used with Zabbix version 6.0 and higher.
More information about official integrations can be found on the [Zabbix AWS Integrations](https://www.zabbix.com/integrations/aws) page.

### Monitoring Metrics

Metrics for monitoring are based on the AWS ELB specifications. For detailed information, refer to the [CloudWatch metrics for your Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-cloudwatch-metrics.html).
In this template, you can monitor various indicators of ELB, and in the case of target groups, you can use Discovery Rule to automatically search target groups and monitor indicators appropriate for each target group.

### IAM Policy Requirements

Before using the template, make sure you have the appropriate IAM permissions for monitoring. The minimum permission policy required for monitoring with CloudWatch using AccessKey is as follows:
(This may change over time):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:ListMetrics",
                "cloudwatch:GetMetricData",
                "elasticloadbalancing:DescribeTargetGroups",
                "elasticloadbalancing:DescribeLoadBalancers",
                "elasticloadbalancing:DescribeTargetHealth"
            ],
            "Resource": "*"
        }
    ]
}
```

### Macros Description

- `{$AWS.ACCESS.KEY.ID}`: Your AWS Access Key.
- `{$AWS.AUTH_TYPE}`: Enter `role_base` for role-based access, or `access_key` for access key based authentication.
- `{$AWS.ELB.INSTANCE.ARN}`: Your Load Balancer's ARN.
- `{$AWS.REGION}`: Your AWS Region.
- `{$AWS.SECRET.ACCESS.KEY}`: Your AWS Secret Access Key.
- `{$AWS.ELB.4XX.WARN}`: Enter the value to be used as a warning in the trigger for the HTTP 4XX error code.
- `{$AWS.ELB.5XX.WARN}`: Enter the value to be used as a warning in the trigger for the HTTP 5XX error code.
- `{$AWS.ELB.REJECTED.WARN}`: Enter a value to use as an alert in the trigger when there are too many rejected connections.
- `{$AWS.ELB.ACTIVECONNECTION.WARN}`: Enter a value to use as a warning in the trigger for too many active connections.
- 
<br />

## AWS NAT Gateway Monitoring Template (`zabbix_aws_nat_gateway_template.yaml`)

This template was created based on Zabbix official AWS templates and is designed to be used with Zabbix version 6.0 and higher.
More information about official integrations can be found on the [Zabbix AWS Integrations](https://www.zabbix.com/integrations/aws) page.

### Monitoring Metrics

The metrics for monitoring are based on the specifications provided by AWS. For detailed information on the NAT Gateway metrics, refer to the [Monitor NAT gateways with Amazon CloudWatch](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway-cloudwatch.html).

### IAM Policy Requirements

Before using the template, make sure you have the appropriate IAM permissions for monitoring. The minimum permission policy required for monitoring with CloudWatch using AccessKey is as follows:
(This may change over time):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:ListMetrics",
                "cloudwatch:GetMetricData"
            ],
            "Resource": "*"
        }
    ]
}
```

### Macros Description

- `{$AWS.ACCESS.KEY.ID}`: Your AWS Access Key.
- `{$AWS.AUTH_TYPE}`: Enter `role_base` for role-based access, or `access_key` for access key based authentication.
- `{$AWS.NAT.GATEWAY.ID}`: NAT Gateway ID. `nat-01234abcde567fg89`
- `{$AWS.REGION}`: Your AWS Region.
- `{$AWS.SECRET.ACCESS.KEY}`: Your AWS Secret Access Key.
