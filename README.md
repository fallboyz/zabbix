# Zabbix Custom Monitoring Templates

## zabbix_aws_elb_template.yaml

This template is an AWS Elastic Load Balancer (ELB) monitoring template designed for use with Zabbix. The template is written to work with Zabbix versions 6.0 and higher. Inspired by the official Zabbix AWS integration template. More information about official integrations can be found on the [Zabbix AWS Integration](https://www.zabbix.com/integrations/aws) page.

### Monitoring Metrics

The metrics for monitoring are based on the specifications provided by AWS. For detailed information on the ELB metrics, refer to the [AWS ELB CloudWatch Metrics Documentation](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-cloudwatch-metrics.html).

### Macros Description

- `{$AWS.ACCESS.KEY.ID}`: Your AWS Access Key.
- `{$AWS.AUTH_TYPE}`: Enter `role_base` for role-based access, or `access_key` for access key based authentication.
- `{$AWS.ELB.INSTANCE.ID}`: The value corresponding to `app/my-alb/ed123456a12f01d0` in your Load Balancer's ARN.
- `{$AWS.REGION}`: AWS region code where your load balancer is located.
- `{$AWS.SECRET.ACCESS.KEY}`: Your AWS Secret Access Key.

### Prerequisites

Ensure you have the appropriate IAM permissions for monitoring. The minimum permission policy required is as follows (note that this may change over time):

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
