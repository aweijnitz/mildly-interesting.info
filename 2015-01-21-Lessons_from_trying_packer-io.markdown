# Notes from starting with packer.io

Playing around with [packer.io](https://packer.io) is a lot of fun, but unfortunately there are a couple of errors in the
very first example which can throw you off track. These are my notes from walking through the first example and launching
my first image.



This page has an overview of image ids for Debian Wheezy together with which virtualization they support, broken down by AWS region id (puh!)
https://wiki.debian.org/Cloud/AmazonEC2Image/Wheezy#A7.8


## Errors you might see

__Error:__
- Build 'amazon-ebs' errored: The provided source AMI has an invalid root device type.
Expected 'ebs', got 'instance-store'.

__Reason:__ 
- You selected an image which had the incorrect storage type. You need an image with elastic block storage (EBS) for the example.


__Errors:__
- Error launching source instance: Virtualization type 'hvm' is required for instances of type 't2.micro'. (InvalidParameterCombination)
- Build 'amazon-ebs' errored: Error launching source instance: Virtualization type 'hvm' is required for instances of type 't2.micro'. (InvalidParameterCombination)

__Reason:__
- There are two different kinds of virtualization offered by Amazon, hardware virtualization (HVM) and para virtualization (PVM?). Different instance types support different virtualizations. You need them to match. In this case, HVM is reqired for t2.micro instances.


__Error:__
- amazon-ebs: Error querying AMI: The image id '[ami-3d50120d]' does not exist (InvalidAMIID.NotFound)

__Reason:__
- You have given an image id that does not exist. You need to find anotherone. Use the [Amazon Marketplace](https://aws.amazon.com/marketplace), or [this link](https://wiki.debian.org/Cloud/AmazonEC2Image/Wheezy#A7.8)
