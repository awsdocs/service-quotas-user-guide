# Logging Service Quotas API calls using AWS CloudTrail<a name="logging-using-cloudtrail"></a>

Service Quotas is integrated with AWS CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in Service Quotas\. CloudTrail captures all API calls for Service Quotas as events\. The calls captured include calls from the Service Quotas console and code calls to the Service Quotas API operations\. If you create a trail, you can enable continuous delivery of CloudTrail events to an Amazon S3 bucket, including events for Service Quotas\. If you don't configure a trail, you can still view the most recent events in the CloudTrail console in **Event history**\. Using the information collected by CloudTrail, you can determine the request that was made to Service Quotas, the IP address from which the request was made, who made the request, when it was made, and additional details\.

To learn more about CloudTrail, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)\.

## Service Quotas information in CloudTrail<a name="service-quotas-info-in-cloudtrail"></a>

CloudTrail is enabled on your AWS account when you create the account\. When activity occurs in Service Quotas, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your AWS account\. For more information, see [Viewing events with CloudTrail Event history](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)\.

For an ongoing record of events in your AWS account, including events for Service Quotas, create a trail\. A *trail* enables CloudTrail to deliver log files to an Amazon S3 bucket\. By default, when you create a trail in the console, the trail applies to all AWS Regions\. The trail logs events from all Regions in the AWS partition and delivers the log files to the Amazon S3 bucket that you specify\. Additionally, you can configure other AWS services to further analyze and act upon the event data collected in CloudTrail logs\. For more information, see the following:
+ [Overview for creating a trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)
+ [CloudTrail supported services and integrations](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html)
+ [Configuring Amazon SNS notifications for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/configure-sns-notifications-for-cloudtrail.html)
+ [Receiving CloudTrail log files from multiple regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail log files from multiple accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)

All Service Quotas actions are logged by CloudTrail and are documented in the [Service Quotas API Reference](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/Welcome.html)\. For example, calls to the  `GetServiceQuota`, `RequestServiceQuotaIncrease` and `ListAWSDefaultServiceQuotas` actions generate entries in the CloudTrail log files\.

Every event or log entry contains information that helps you determine who made the request\.
+  AWS account root credentials\. 
+ Temporary security credentials from an AWS Identity and Access Management role or federated user\.
+ Long\-term security credentials from an IAM user\.
+ Another AWS service\.

For more information, see the [CloudTrail userIdentity element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)\.

## Understanding Service Quotas log file entries<a name="understanding-service-name-entries"></a>

A trail is a configuration that enables delivery of events as log files to an Amazon S3 bucket that you specify\. CloudTrail log files contain one or more log entries\. An event represents a single request from any source and includes information about the requested action, the date and time of the action, request parameters, and so on\. CloudTrail log files aren't an ordered stack trace of the public API calls, so they don't appear in any specific order\. 

The following example shows a CloudTrail log entry that demonstrates the `RequestQuotaIncrease` action\.

```
{
    "eventVersion": "1.08",
    "userIdentity": {
        "type": "IAMUser",
        "principalId": "AIDA123456789012Example",
        "arn": "arn:aws:iam::123456789012:user/admin",
        "accountId": "123456789012",
        "accessKeyId": "AKIAIOSFODNN7EXAMPLE",
        "userName": " admin",
        "sessionContext": {
            "sessionIssuer": {},
            "webIdFederationData": {},
            "attributes": {
                "creationDate": "2022-01-24T16:57:04Z",
                "mfaAuthenticated": "true"
            }
        }
    },
    "eventTime": "2022-01-24T17:00:15Z",
    "eventSource": "servicequotas.amazonaws.com",
    "eventName": "RequestServiceQuotaIncrease",
    "awsRegion": "us-east-1",
    "sourceIPAddress": "172.21.16.1",
    "userAgent": "aws-internal/3 aws-sdk-java/1.12.127 Linux/5.4.147-83.259.amzn2int.x86_64 OpenJDK_64-Bit_Server_VM/25.312-b07 java/1.8.0_312 vendor/Oracle_Corporation cfg/retry-mode/standard",
    "requestParameters": {
        "serviceCode": "ec2",
        "quotaCode": "L-CEED54BB",
        "desiredValue": 10
    },
    "responseElements": {
        "requestedQuota": {
            "id": "cd3ad3d9-2776-4ef1-a904-4c229d1642ee",
            "serviceCode": "ec2",
            "serviceName": "Amazon Elastic Compute Cloud (Amazon EC2)",
            "quotaCode": "L-CEED54BB",
            "quotaName": "EC2-Classic Elastic IPs",
            "desiredValue": 10,
            "status": "PENDING",
            "created": "Jan 24, 2022 5:00:15 PM",
            "requester": "{\"accountId\":\"123456789012\",\"callerArn\":\"arn:aws:iam::123456789012:user/admin\"}",
            "quotaArn": "arn:aws:servicequotas:us-east-1:123456789012:ec2/L-CEED54BB",
            "globalQuota": false,
            "unit": "None"
        }
    },
    "requestID": "3d3f5cdc-af30-4121-b69a-84b2f5c33be5",
    "eventID": "0cb51588-e460-4e00-bc48-a9d4820cad83",
    "readOnly": false,
    "eventType": "AwsApiCall",
    "managementEvent": true,
    "recipientAccountId": "123456789012",
    "eventCategory": "Management"
}
```

This example shows that the user named `admin` generated a request for additional Amazon Elastic Compute Cloud Elastic IP addresses on January 24, 2022\. The requested increase was 10, an increase of 5 from the default quota of 5\.

The following is an example of an approved quota increase in Service Quotas:

```
{
    "eventVersion": "1.08",
    "userIdentity": {
        "accountId": "123456789012",
        "invokedBy": "servicequotas.amazonaws.com"
    },
    "eventTime": "2022-01-24T17:02:17Z",
    "eventSource": "servicequotas.amazonaws.com",
    "eventName": "UpdateServiceQuotaIncreaseRequestStatus",
    "awsRegion": "us-east-1",
    "sourceIPAddress": "servicequotas.amazonaws.com",
    "userAgent": "servicequotas.amazonaws.com",
    "requestParameters": null,
    "responseElements": null,
    "eventID": "e331b0a0-9395-4895-aeba-73cbab9ebcb0",
    "readOnly": false,
    "eventType": "AwsServiceEvent",
    "managementEvent": true,
    "recipientAccountId": "123456789012",
    "serviceEventDetails": {
        "requestId": "cdc5f1f78739459e6642407bb2bZKO8GKUM",
        "newStatus": "CASE_CLOSED",
        "createTime": "2022-01-24T17:00:15.363Z",
        "newQuotaValue": "10.0",
        "serviceName": "Amazon Elastic Compute Cloud (Amazon EC2)",
        "quotaName": "EC2-Classic Elastic IPs",
        "unit": "None"
    },
    "eventCategory": "Management"
}
```

From the `serviceEventDetails` section, you can determine that AWS Support approved the request for a quota increase to 10 Elastic IP addresses, and closed the request\. The `newQuotaValue` displays 10 as the new quota\.