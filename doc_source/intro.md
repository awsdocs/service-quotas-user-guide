# What is Service Quotas?<a name="intro"></a>

Service Quotas enables you to view and manage your quotas for AWS services from a central location\. Quotas, also referred to as limits in AWS, are the maximum values for the resources, actions, and items in your AWS account\. Each AWS service defines its quotas and establishes default values for those quotas\. Depending on your business needs, you might need to increase your service quota values\. Service Quotas makes it easy to look up your service quotas and to request increases\.

**Topics**
+ [Features](#features)
+ [Terms](#intro_getting-started)
+ [Accessing Service Quotas](#access)

## Features<a name="features"></a>

The following features are available\.

**View your service quotas**  
The Service Quotas console provides quick access to the AWS default quota values for your account, across all commercial Regions\. When you select a service in the Service Quotas console, you'll see the quotas and whether the quota is adjustable\. Applied quotas are overrides, or increases for a particular quota, over the AWS default value\. 

**Request a service quota increase**  
For any adjustable service quotas, you can use Service Quotas to request a quota increase\. To request a quota increase, in the console simply select the service and the specific quota, and choose Request quota increase\. You can also use the API or command line interface \(CLI\) tools to request service quota increases\. 

**View current utilization**  
After your account has been active a while, you can view a graph of your resource utilization\.

## Terms<a name="intro_getting-started"></a>

The following terms are important for understanding Service Quotas and how it works\.

**service quota**  
The maximum number of service resources or operations that apply to an account or a Region\. The number of IAM roles per account is an example of account\-based quota\. The number of virtual private clouds \(VPCs\) per Region is an example of a Region\-based quota\. Check the description of a service quota to determine whether it is Region\-specific\.

**adjustable value**  
A quota value that can be increased\.

**applied value**  
The new quota value after a quota increase\.

**default value**  
The initial quota value established by AWS\.

**global quota**  
A service quota applied at an account level\. Global quotas are available in all Regions\. You can request an increase to a global quota from any Region, and can track the status of the increase from the Region where you requested the increase\. If you request a quota increase for a global quota, you can't request an increase for the same quota from a different Region until the first request is complete\. After the initial request is completed, the applied quota value is visible in all Regions where applied quotas are available\.

**usage**  
The number of resources or operations in use for a service quota\.

**utilization**  
The percentage of a service quota in use\. For example, if the quota value is 200 resources and 150 resources are in use, the utilization is 75%\.

## Accessing Service Quotas<a name="access"></a>

You can work with Service Quotas in the following ways:

**AWS Management Console**  
[The Service Quotas console](https://console.aws.amazon.com/servicequotas/home?region=us-east-1#!/dashboard) is a browser\-based interface that you can use to view and manage your service quotas\. You can perform almost any task that's related to your service quotas by using the console\. You can access Service Quotas from any AWS console page by choosing on the top navigation bar, or by searching for Service Quotas in the AWS Management Console\. 

**AWS Command Line Tools**  
The AWS command line tools let you issue commands at your system's command line to perform Service Quotas and other AWS tasks\. This can be faster and more convenient than using the console\. The command line tools also are useful if you want to build scripts that perform AWS tasks\.  
AWS provides two sets of command line tools: the [AWS Command Line Interface](https://aws.amazon.com/cli/) \(AWS CLI\) and the [AWS Tools for Windows PowerShell](https://aws.amazon.com/powershell/)\. For information about installing and using the AWS CLI, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/)\. For information about installing and using the Tools for Windows PowerShell, see the [AWS Tools for Windows PowerShell User Guide](https://docs.aws.amazon.com/powershell/latest/userguide/)\.

**AWS SDKs**  
The AWS SDKs consist of libraries and sample code for various programming languages and platforms \(for example, [Java](https://aws.amazon.com/sdk-for-java/), [Python](https://aws.amazon.com/sdk-for-python/), [Ruby](https://aws.amazon.com/sdk-for-ruby/), [\.NET](https://aws.amazon.com/sdk-for-net/), [iOS and Android](https://aws.amazon.com/mobile/resources/), and [others](https://aws.amazon.com/tools/#sdk)\)\. The SDKs include tasks such as cryptographically signing requests, managing errors, and retrying requests automatically\. For more information about the AWS SDKs, including how to download and install them, see [Tools for Amazon Web Services](https://aws.amazon.com/tools/#sdk)\.