Create Stack

```text
aws --profile <aws-profile> --region <region-name> cloudformation create-stack --stack-name <name-of-stack> --template-body file:///vpc/template.yaml --parameters file:///vpc/parameters.json 
```

Update Stack

```text
aws --profile <aws-profile> --region <region-name> cloudformation update-stack --stack-name <name-of-stack> --template-body file:///vpc/template.yaml --parameters file:///vpc/parameters.json 
```

Below is a template for the parameters file passed via `--parameters` argument in the above command

JSON Parameters:

```text
[
    {
        "ParameterKey": "EnvironmentName",
        "ParameterValue": "<name-of-environment>"
    },
    {
        "ParameterKey": "VpcCIDR",
        "ParameterValue": "<vpc-cidr-block>"
    },
    {
        "ParameterKey": "PublicSubnet1CIDR",
        "ParameterValue": "<public-subnet-1-cidr>"
    },
    {
        "ParameterKey": "PublicSubnet2CIDR",
        "ParameterValue": "<public-subnet-2-cidr>"
    },
    {
        "ParameterKey": "PublicSubnet3CIDR",
        "ParameterValue": "<public-subnet-3-cidr>"
    },
    {
        "ParameterKey": "PrivateSubnet1CIDR",
        "ParameterValue": "<private-subnet-1-cidr>"
    },
    {
        "ParameterKey": "PrivateSubnet2CIDR",
        "ParameterValue": "<private-subnet-2-cidr>"
    },
    {
        "ParameterKey": "PrivateSubnet3CIDR",
        "ParameterValue": "<private-subnet-3-cidr>"
    }
]
```

Optional JSON Parameters:

```text
[
    {
        "ParameterKey": "CreateVPNGateway",
        "ParameterValue": "yes"
    },
    {
        "ParameterKey": "CreateVPNGatewayAsn", # Do not include this parameter to use the default value
        "ParameterValue": "65412"
    }
]
```

Example:

```text
[
    {
        "ParameterKey": "EnvironmentName",
        "ParameterValue": "mywebsite-prd"
    },
    {
        "ParameterKey": "VpcCIDR",
        "ParameterValue": "10.100.0.0/19"
    },
    {
        "ParameterKey": "PublicSubnet1CIDR",
        "ParameterValue": "10.100.0.0/22"
    },
    {
        "ParameterKey": "PublicSubnet2CIDR",
        "ParameterValue": "10.100.4.0/22"
    },
    {
        "ParameterKey": "PublicSubnet3CIDR",
        "ParameterValue": "10.100.8.0/22"
    },
    {
        "ParameterKey": "PrivateSubnet1CIDR",
        "ParameterValue": "10.100.16.0/22"
    },
    {
        "ParameterKey": "PrivateSubnet2CIDR",
        "ParameterValue": "10.100.20.0/22"
    },
    {
        "ParameterKey": "PrivateSubnet3CIDR",
        "ParameterValue": "10.100.24.0/22"
    }
]
```