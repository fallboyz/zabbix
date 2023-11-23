# Zabbix Custom Monitoring Templates

## CloudWatch requisites

Before using the template, make sure you have the appropriate IAM permissions for monitoring. The minimum permissions policy required for monitoring using CloudWatch is as follows
(this may change over time):

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

<br />

## AWS Elastic Load Balancer (ELB) Monitoring Template (`zabbix_aws_elb_template.yaml`)

This template was created based on Zabbix official AWS templates and is designed to be used with Zabbix version 6.0 and higher.
More information about official integrations can be found on the [Zabbix AWS Integrations](https://www.zabbix.com/integrations/aws) page.

### Monitoring Metrics

Metrics for monitoring are based on the AWS ELB specifications. For detailed information, refer to the [CloudWatch metrics for your Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-cloudwatch-metrics.html).

### Macros Description

- `{$AWS.ACCESS.KEY.ID}`: Your AWS Access Key.
- `{$AWS.AUTH_TYPE}`: Enter `role_base` for role-based access, or `access_key` for access key based authentication.
- `{$AWS.ELB.INSTANCE.ID}`: The value corresponding to `app/my-alb/ed123456a12f01d0` in your Load Balancer's ARN.
- `{$AWS.REGION}`: AWS region code where your load balancer is located.
- `{$AWS.SECRET.ACCESS.KEY}`: Your AWS Secret Access Key.

<br />

## AWS NAT Gateway Monitoring Template (`zabbix_aws_nat_gateway_template.yaml`)

This template was created based on Zabbix official AWS templates and is designed to be used with Zabbix version 6.0 and higher.
More information about official integrations can be found on the [Zabbix AWS Integrations](https://www.zabbix.com/integrations/aws) page.

### Monitoring Metrics

The metrics for monitoring are based on the specifications provided by AWS. For detailed information on the NAT Gateway metrics, refer to the [Monitor NAT gateways with Amazon CloudWatch](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway-cloudwatch.html).

### Macros Description

- `{$AWS.ACCESS.KEY.ID}`: Your AWS Access Key.
- `{$AWS.AUTH_TYPE}`: Enter `role_base` for role-based access, or `access_key` for access key based authentication.
- `{$AWS.NAT.GATEWAY.ID}`: NAT Gateway ID. `nat-01234abcde567fg89`
- `{$AWS.REGION}`: AWS region code where your NAT Gateway is located.
- `{$AWS.SECRET.ACCESS.KEY}`: Your AWS Secret Access Key.
