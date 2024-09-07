---
layout: plugin
plugin: 4e5dc595-45c7-4461-929a-8f96a0c96b3d
compatibility: All platforms
examples:
    -
        name: User
        cmd: ‑‑route53accesskeyid mykeyid ‑‑route53secretaccesskey *****
    - 
        name: IAM role
        cmd: ‑‑route53iamrole myrole
---
Create the record in Amazon AWS [Route53](https://aws.amazon.com/route53/). This requires either a user or an IAM role with the following permissions on the zone: 
`route53:GetChange`, `route53:ListHostedZones` and `route53:ChangeResourceRecordSets`.

## IAM
The IAM role method can only work from inside an EC2 instance. Note that the program
expects to recieve an IAM role *name*, so not the ARN.