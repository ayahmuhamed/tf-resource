# tf-resource
Create same resource to be used in differant regios


## Pre-requirements


* [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) 
* [Terraform cli](https://learn.hashicorp.com/tutorials/terraform/install-cli)
* [AWS account and AWS Access Credentials](https://aws.amazon.com/account/)

## How to use this repo

- Clone
- Run
- Cleanup

---

### Clone the repo

```
git clone https://github.com/ayahmuhamed/resource-in-2-regions
```

### Change directory

```
cd resource-in-2-regions
```

### Run

* Init:

```
terraform init
```



* Apply:

```
terraform apply
```

* Confirm resources created

_sample_:

```

 aws ec2 describe-vpcs --filter --vpc-ids $(terraform output -raw vpc-central) --region=eu-central-1
aws ec2 describe-vpcs --filter --vpc-ids $(terraform output -raw vpc-north) --region=eu-north-1
{
    "Vpcs": [
        {
            "CidrBlock": "10.1.0.0/16",
            "DhcpOptionsId": "dopt-e090308a",
            "State": "available",
            "VpcId": "vpc-0ab9014ed84f399fb",
            "OwnerId": "267023797923",
            "InstanceTenancy": "default",
            "CidrBlockAssociationSet": [
                {
                    "AssociationId": "vpc-cidr-assoc-0cf70ca5f668f9549",
                    "CidrBlock": "10.1.0.0/16",
                    "CidrBlockState": {
                        "State": "associated"
                    }
                }
            ],
            "IsDefault": false
        }
    ]
}
{
    "Vpcs": [
        {
            "CidrBlock": "10.1.0.0/16",
            "DhcpOptionsId": "dopt-c560cdac",
            "State": "available",
            "VpcId": "vpc-0a8ab22fd8fbb4cd9",
            "OwnerId": "267023797923",
            "InstanceTenancy": "default",
            "CidrBlockAssociationSet": [
                {
                    "AssociationId": "vpc-cidr-assoc-07c84881d3b9f74f9",
                    "CidrBlock": "10.1.0.0/16",
                    "CidrBlockState": {
                        "State": "associated"
                    }
                }
            ],
            "IsDefault": false
        }
    ]
}
```



### Cleanup

```
terraform destroy
```


