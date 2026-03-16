---
layout: plugin
plugin: 4e5dc595-45c7-4461-929a-8f96a0c96b3d
compatibility: All platforms
examples:
    -
        name: Access key
        cmd: ‑‑route53accesskeyid mykeyid ‑‑route53secretaccesskey *****
    - 
        name: IAM role
        cmd: ‑‑route53iamrole myrole
    - 
        name: ARN role (using instance profile)
        cmd: ‑‑route53arnrole "arn:aws:iam::123456789012:user/johndoe"
    - 
        name: ARN role (using IAM role)
        cmd: ‑‑route53iamrole myrole ‑‑route53arnrole "arn:aws:iam::123456789012:user/johndoe"
    - 
        name: ARN role (using access key)
        cmd: ‑‑route53accesskeyid mykeyid ‑‑route53secretaccesskey ***** ‑‑route53arnrole "arn:aws:iam::123456789012:user/johndoe"
---
Create the record in Amazon AWS [Route53](https://aws.amazon.com/route53/). This requires either a user or an IAM role with the following permissions on the zone: 
`route53:GetChange`, `route53:ListHostedZones` and `route53:ChangeResourceRecordSets`.

## IAM
The IAM role method can only work from inside an EC2 instance. Note that the program
expects to receive an IAM role *name*, so not the full ARN.

## ARN
The ARN role method can work from anywhere.