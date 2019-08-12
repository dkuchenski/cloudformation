Create Stack

```text
aws --profile <aws-profile> --region <region-name> cloudformation create-stack --stack-name <name-of-stack> --template-body file:///alb/template.yaml --parameters file:///alb/parameters.json
```

Update Stack

```text
aws --profile <aws-profile> --region <region-name> cloudformation update-stack --stack-name <name-of-stack> --template-body file:///alb/template.yaml --parameters file:///alb/parameters.json
```

Below is a template for the parameters file passed via `--parameters` argument in the above command

JSON Parameters

```text
[
    {
        "ParameterKey": "EnvironmentName",
        "ParameterValue": "<name-of-environment>"
    },
    {
        "ParameterKey": "ServiceName",
        "ParameterValue": "<service-used-with-alb>"
    },
    {
        "ParameterKey": "LoadBalancerNetwork",
        "ParameterValue": "<public-or-private-network>"
    },
    {
        "ParameterKey": "LoadBalancerPort",
        "ParameterValue": "<listener-port>"
    },
    {
        "ParameterKey": "LoadBalancerProtocol",
        "ParameterValue": "<http-or-https>"
    },
    {
        "ParameterKey": "LoadBalancerCertificateArn",
        "ParameterValue": "<optional-ssl-certificate>"
    },
    {
        "ParameterKey": "LoadBalancerSecurityGroup",
        "ParameterValue": "<optional-existing-security-group>"
    }
]
```

Example

```text
[
    {
        "ParameterKey": "EnvironmentName",
        "ParameterValue": "mywebsite-prd"
    },
    {
        "ParameterKey": "ServiceName",
        "ParameterValue": "frontend"
    },
    {
        "ParameterKey": "LoadBalancerNetwork",
        "ParameterValue": "public"
    },
    {
        "ParameterKey": "LoadBalancerPort",
        "ParameterValue": "443"
    },
    {
        "ParameterKey": "LoadBalancerProtocol",
        "ParameterValue": "https"
    },
    {
        "ParameterKey": "LoadBalancerCertificateArn",
        "ParameterValue": "arn:aws:iam::XXXXXXXXXXX:server-certificate/cloudfront/certificate_name"
    }
]
```