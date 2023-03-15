# What is Service Quotas?<a name="intro"></a>

With Service Quotas, you can view and manage your quotas for AWS services from a central location\. Quotas, also referred to as limits in AWS services, are the maximum values for the resources, actions, and items in your AWS account\. Each AWS service defines its quotas and establishes default values for those quotas\. If your business needs aren't met by the default limit of service resources or operations that apply to an AWS account or an AWS Region, you might need to increase your service quota values\. Service Quotas enables you to look up your service quotas and to request increases\. AWS Support might approve, deny, or partially approve your requests\.

**Topics**
+ [Features of Service Quotas](#features)
+ [Terminology in Service Quotas](#intro_getting-started)
+ [Accessing Service Quotas](#access)

## Features of Service Quotas<a name="features"></a>

Service Quotas provides the following features:

**View your service quotas**  
The Service Quotas console provides quick access to the AWS default quota values for your account, across all AWS Regions\. When you select a service in the Service Quotas console, you see the quotas and whether the quota is adjustable\. *Applied quotas* are overrides, or increases for a specific quota, over the AWS default value\. 

**Request a service quota increase**  
For any adjustable service quotas, you can use Service Quotas to request a quota increase\. To request a quota increase, in the Service Quotas console, select the service and the specific quota, and then choose **Request quota increase**\. Increases do take some time to review, process, and approve\. You can also use Service Quotas API operations or the AWS CLI tools to request service quota increases\. 

**View current utilization of resources**  
After your account becomes active for a period of time, you can view a graph of your resource utilization\.

## Terminology in Service Quotas<a name="intro_getting-started"></a>

The following terms are important for understanding Service Quotas and how it works\.

**service quota**  
The maximum number of service resources or operations that apply to an AWS account or an AWS Region\. The number of AWS Identity and Access Management \(IAM\) roles per account is an example of an account\-based quota\. The number of virtual private clouds \(VPCs\) per Region is an example of a Region\-based quota\. To determine whether a service quota is Region\-specific, check the description of the service quota\.

**adjustable value**  
A quota value that can be increased\.

**applied quota**  
The updated quota value after a quota increase\.

**default value**  
The initial quota value established by AWS\.

**global quota**  
A service quota applied at an account level\. Global quotas are available in all AWS Regions\. You can request an increase to a global quota from any Region\. You can track the status of the increase from the Region where you requested the increase\. If you request a quota increase for a global quota, you can't request an increase for the same quota from a different Region until the first request is complete\. After the initial request is completed, the applied quota value is visible in all Regions where applied quotas are available\.

**usage**  
The number of resources or operations in use for a service quota\.

**utilization**  
The percentage of a service quota in use\. For example, if the quota value is 200 resources and 150 resources are in use, then the utilization is 75 percent\.

## Accessing Service Quotas<a name="access"></a>

You can work with Service Quotas in the following ways:

**AWS Management Console**  
[The Service Quotas console](https://console.aws.amazon.com/servicequotas/home?region=us-east-1#!/dashboard) is a browser\-based interface that you can use to view and manage your service quotas\. You can perform almost any task that's related to your service quotas by using the console\. You can access Service Quotas from any AWS Management Console page by choosing it on the top navigation bar, or by searching for Service Quotas in the AWS Management Console\.

**AWS Command Line Interface tools**  
By using the AWS Command Line Interface tools, you can issue commands at your system's command line to perform Service Quotas and other AWS tasks\. This can be a faster and more convenient approach than using the console\. The command line tools also are useful if you want to build scripts that perform AWS tasks\.  
AWS provides two sets of command line tools: the [AWS Command Line Interface](https://aws.amazon.com/cli/)  and the [AWS Tools for Windows PowerShell](https://aws.amazon.com/powershell/)\. For information about installing and using the AWS CLI, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/)\. For information about installing and using the Tools for Windows PowerShell, see the [AWS Tools for Windows PowerShell User Guide](https://docs.aws.amazon.com/powershell/latest/userguide/)\.

**AWS SDKs**  
The AWS SDKs consist of libraries and sample code for various programming languages and platforms \(for example, [Java](https://aws.amazon.com/sdk-for-java/), [Python](https://aws.amazon.com/sdk-for-python/), [Ruby](https://aws.amazon.com/sdk-for-ruby/), [\.NET](https://aws.amazon.com/sdk-for-net/), [iOS and Android](https://aws.amazon.com/mobile/resources/), and [others](https://aws.amazon.com/tools/#sdk)\)\. The SDKs include tasks such as cryptographically signing requests, managing errors, and retrying requests automatically\. For more information about the AWS SDKs, including how to download and install them, see [Tools for Amazon Web Services](https://aws.amazon.com/tools/#SDKs)\.