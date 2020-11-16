## Tag Resources in Tenancy

Tag Resources in Tenancy is a tool to help you tag resources easily, it uses the OCI Python SDK. 
It covers the below OCI components, 
Authentication by User or Compute using instance principals, 
Output can be printer friendly, Summary or JSON.

**Developed by Adi Zohar, Nov 2020**

## Modules Included:  
- oci.core.VirtualNetworkClient          
- oci.core.ComputeClient                 
- oci.core.BlockstorageClient            
- oci.object_storage.ObjectStorageClient 
- oci.database.DatabaseClient            
- oci.load_balancer.LoadBalancerClient   
- oci.identity.IdentityClient

** DISCLAIMER – This is not an official Oracle application

## Executing using Cloud Shell:
```
1. install oci sdk package
   pip3 install --user oci

2. clone the oci sdk repo
   git clone https://github.com/oracle/oci-python-sdk

3. run with delegation token
   cd oci-python-sdk/examples/tag_resources_in_tenancy
   python3 tag_resources_in_tenancy.py --help
```

## OCI Authentication using Instance Principals - Privilges can be aligned accordingly

Create Dynamic Group ShowOCIDynamicGroup:
```
any {ALL {instance.id = 'ocid1.instance.oc1.xxxxxxxxxx'}}
```

Add Policy:
```
allow dynamic-group ShowOCIDynamicGroup to manage all-resources in tenancy
```

## OCI Authentication using User - Privilges can be aligned accordingly
Required OCI IAM user with read only privileges

```
ALLOW GROUP ReadOnlyUsers to manage all-resources IN TENANCY
```

## Installation of Python 3 incase you don't have Python3 installed:
Please follow Python Documentation - https://docs.python.org/3/using/index.html

## Install oci SDK Packages:
Please follow Oracle Python SDK Documentation - https://github.com/oracle/oci-python-sdk

## Copy the Software
Download the tag_resources_in_tenancy.py from this project  

Execute  

```
$ python3 tag_resources_in_tenancy.py --help

usage: tag_resources_in_tenancy.py [-h] [-t CONFIG_PROFILE] [-p PROXY]
                                   [-cp COMPARTMENT] [-rg REGION] [-ip] [-dt]
                                   [-tag TAG]
                                   [-action {add_defined,add_free,del_defined,del_free,list}]
                                   [-output {list,json,summary}]

optional arguments:
  -h, --help            show this help message and exit
  -t CONFIG_PROFILE     Config file section to use (tenancy profile)
  -p PROXY              Set Proxy (i.e. www-proxy-server.com:80)
  -cp COMPARTMENT       Filter by Compartment Name or Id
  -rg REGION            Filter by Region Name
  -ip                   Use Instance Principals for Authentication
  -dt                   Use Delegation Token for Authentication
  -tag TAG              Tag in format - namespace.key=value or key=value
  -action {add_defined,add_free,del_defined,del_free,list}
                        Action Type, default=list
  -output {list,json,summary}
                        Output type, default=summary

```

