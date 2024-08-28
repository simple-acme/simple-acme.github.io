---
layout: plugin
plugin_type: validation
plugin_subtype: dns
plugin: route53
---
Create the record in Amazon AWS [Route53](https://aws.amazon.com/route53/). This requires either a user or an IAM role with the following permissions on the zone: 
`route53:GetChange`, `route53:ListHostedZones` and `route53:ChangeResourceRecordSets`.

## IAM
The IAM role method can only work from inside an EC2 instance. Note that the program
expects to recieve an IAM role *name*, so not the ARN.