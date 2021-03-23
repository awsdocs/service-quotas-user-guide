# Tagging resources in Service Quotas<a name="sq-tagging"></a>

A *tag* is a custom attribute label that you add to an AWS resource to make it easier to identify, organize, and search for resources\. Each tag has two parts:
+ A *tag key*, such as `CostCenter`, `Environment`, or `Project`\. Tag keys are case sensitive\.
+ A *tag value*, such as `111122223333` or `Production`\. You can set the value of a tag to an empty string, but you can't set the value of a tag to null\. Omitting the tag value is the same as using an empty string\. Like tag keys, tag values are case sensitive\.

You can use tags to categorize resources by purpose, owner, environment, or other criteria\. For more information, see [AWS Tagging Strategies](https://aws.amazon.com/answers/account-management/aws-tagging-strategies/)\.

Tags help you do the following:
+ Identify and organize your AWS resources\. Many AWS services support tagging, so you can assign the same tag to resources from different services to indicate that the resources are related\.
+ Track your AWS costs\. You activate these tags on the AWS Billing and Cost Management dashboard\. AWS uses the tags to categorize your costs and deliver a monthly cost allocation report to you\. For more information, see [Use cost allocation tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html) in the [AWS Billing and Cost Management User Guide](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.
+ Control access to your AWS resources\. For more information, see [Controlling access using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the [IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/)\. 

**Topics**
+ [Resources that support tagging in Service Quotas](#sq-supported-resources)
+ [Tag restrictions](#sq-tagging-restrictions)
+ [Permissions required for tagging Service Quotas resources](#sq_tags_permissions)
+ [Managing Service Quotas tags \(console\)](#sq_tags_managing-console)
+ [Managing Service Quotas tags \(AWS CLI\)](#sq_tags_managing-cli)
+ [Managing Service Quotas tags \(AWS API\)](#sq_tags_managing-api)
+ [Controlling access using Service Quotas tags](#sq_tags_access)

## Resources that support tagging in Service Quotas<a name="sq-supported-resources"></a>

The following Service Quotas resources support tagging:
+ **Applied quotas** – Overrides that were previously requested for your account that were approved by AWS\.

**Important**  
You can tag quotas only if they have an applied quota value\. Quotas with default quota values can’t be tagged\.  
Do not store personally identifiable information \(PII\) or other confidential or sensitive information in tags\. Tags are not intended to be used for private or sensitive data\.

## Tag restrictions<a name="sq-tagging-restrictions"></a>

The following basic restrictions apply to tags on Service Quotas resources:
+ Maximum number of tags that you can assign to a resource – 50 
+ Maximum key length – 128 Unicode characters 
+ Maximum value length – 256 Unicode characters 
+ Valid characters for key and value – a\-z, A\-Z, 0\-9, space, and the following characters: \_ \. : / = \+ \- and @
+ Keys and values are case\-sensitive
+ Don't use `aws:` as a prefix for keys because it's reserved for AWS use

## Permissions required for tagging Service Quotas resources<a name="sq_tags_permissions"></a>

You must configure permissions to allow your users or roles to manage tags in Service Quotas\. The permissions that are required to administer tags usually correspond to the API actions for the task\.

To ensure that users and roles can use the Service Quotas console for tagging operations, also attach the Service Quotas `ConsoleAccess` or `ReadOnly` AWS managed policy to the entities\. For more information, see [Adding permissions to a user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html#users_change_permissions-add-console) in the *IAM User Guide*\.

```
ServiceQuotasReadOnlyAccess
```
+ To add tags to applied quotas, you must have the following permissions:

  `servicequotas:ListTagsForResource`

  `servicequotas:TagResource`
+ To view tags for an applied quota, you must have the following permissions:

  `servicequotas:ListTagsForResource`
+ To remove existing tags from an applied quota, you must have the following permissions:

  `servicequotas:UntagResource`
+ To edit existing tag values for applied quotas, you must have the following permissions:

  `servicequotas:ListTagsForResource`

  `servicequotas:TagResource`

  `servicequotas:UntagResource`

## Managing Service Quotas tags \(console\)<a name="sq_tags_managing-console"></a>

You can manage Service Quotas tags using the AWS Management Console\.

1. Sign in to the AWS Management Console and open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/home](https://console.aws.amazon.com/servicequotas/home)\.

1. In the navigation page, choose **AWS services**\.

1. Choose a service from the list, or type the name of the service in the search box\.

1. Choose a service with a value in the **Applied quota value** column\.

1. In the **Tags** section, choose **Manage tags**\. This option is not available for quotas without an applied quota value\.

1. You can add or remove tags or you can edit tag values for existing tags\. Enter a name for the tag in **Key**\. You can add an optional value for the tag in **Value**\.

1. After making all of your changes to tags, choose **Save changes**\.

1. If the operation is successful, you are returned to the quota details page where you can verify your changes\. If the operation fails, please follow the instructions in the error message to resolve it\.

## Managing Service Quotas tags \(AWS CLI\)<a name="sq_tags_managing-cli"></a>

You can manage Service Quotas tags using the AWS CLI\.
+ Adding tags to applied quotas

  `aws service-quotas [tag\-resource](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/tag-resource.html)`
+ Viewing tags for an applied quota

  `aws service-quotas [list\-tags\-for\-resource](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/list-tags-for-resource.html)`
+ Deleting existing tag values for applied quotas

  `aws service-quotas [untag\-resource](https://docs.aws.amazon.com/cli/latest/reference/service-quotas/untag-resource.html)`

## Managing Service Quotas tags \(AWS API\)<a name="sq_tags_managing-api"></a>

You can manage Service Quotas tags using the AWS API\.
+ Adding tags to applied quotas

  `[TagResource](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/API_TagResource.html)`
+ Viewing tags for an applied quota

  `[ListTagsForResource](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/API_ListTagsForResource.html)`
+ Deleting existing tag values for applied quotas

  `[UntagResource](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/API_UntagResource.html)`

## Controlling access using Service Quotas tags<a name="sq_tags_access"></a>

To control access to Service Quotas resources based on tags, you provide tag information in the [condition element](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) of a policy using the `aws:ResourceTag/key-name`, `aws:RequestTag/key-name`, or `aws:TagKeys` condition keys\. For more information about these condition keys, see [Controlling access to AWS resources using resource tags ](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the *IAM User Guide*\.

For example, when you attach the following policy to an IAM user or role, that entity can request an increase to Amazon Athena applied quotas that are tagged with the tag key **Owner** and tag value **admin**\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": ["servicequotas:RequestServiceQuotaIncrease"],
            "Resource": "arn:aws:servicequotas:*:*:athena/*",
            "Condition": {
                "StringEquals": {"aws:ResourceTag/Owner": "admin"}
            }
        }
    ]
}
```

You can also attach tags to IAM entities \(users or roles\) to use attribute\-based access control \(ABAC\)\. ABAC is an authorization strategy that defines permissions based on attributes\. Tagging entities and resources is the first step of ABAC\. Then you design ABAC policies to allow operations when the principal's tag matches the tag on the resource that they are trying to access\. ABAC is helpful in environments that are growing rapidly and helps with situations where policy management becomes cumbersome\.

For more information about ABAC, see [What is ABAC?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_attribute-based-access-control.html) in the *IAM User Guide*\. To view a tutorial with steps for setting up ABAC, see [Use attribute\-based access control \(ABAC\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_attribute-based-access-control.html) in the *IAM User Guide*\.