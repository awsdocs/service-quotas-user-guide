# Requesting a quota increase<a name="request-quota-increase"></a>

For adjustable quotas, you can request a quota increase\. Smaller increases are automatically approved, and larger requests are submitted to AWS Support\. Larger increase requests will take time to review, process, approve, and deploy\. You can track your request case in the AWS Support console\. Requests to increase service quotas don't receive priority support\. If you have an urgent request, contact AWS Support\.

AWS Support can approve, deny, or partially approve your requests\.

You cannot use the Service Quotas console to request a quota decrease\. Instead, use the Support Center Console to create a case\.

------
#### [ Using the AWS Management Console ]

**To request a service quota increase**

1. Sign in to the AWS Management Console and open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/home](https://console.aws.amazon.com/servicequotas/home)\.

1. In the navigation pane, choose **AWS services**\.

1. Choose an AWS service from the list, or type the name of the service in the search box\.

1. If the quota is adjustable, you can choose the button or the name, and then choose **Request quota increase**\.

1. For **Change quota value**, enter the new value\. The new value must be greater than the current value\.

1. Choose **Request**\.

1. To view any pending or recently resolved requests in the console, choose **Dashboard** from the navigation pane\. For pending requests, choose the status of the request to open the request receipt\. The initial status of a request is **Pending**\. After the status changes to **Quota requested**, you'll see the case number with AWS Support\. Choose the case number to open the ticket for your request\.

------
#### [ Using the AWS CLI or SDK Operations ]

**To request a service quota increase**

The `RequestServiceQuotaIncrease` operation, which submits the request, requires the quota code for the quota\. So begin by getting the quota code\.

The following example commands show how to request a quota increase for the AWS Key Management Service service\.

1. Find the name of the quota that you want to increase\. You can find the quota names and descriptions of service\-specific quotas in the [AWS General Reference](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html)\. or in the documentation for the service\.

1. Get the quota code by calling the [ListServiceQuotas](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/API_ListServiceQuotas.html) operation\. The response includes the `QuotaName` and `QuotaCode` for each quota that matches your query\. The following CLI example retrieves the quota code for a AWS KMS quota\.

   ```
   $ aws service-quotas list-service-quotas \
           --service-code kms \
           --query "Quotas[?QuotaName=='Cryptographic operations (RSA) request rate']"
   {
       "Quotas": [
           {
               "ServiceCode": "kms",
               "ServiceName": "AWS Key Management Service (AWS KMS)",
               "QuotaArn": "arn:aws:servicequotas:us-east-1:123456789012:kms/L-2AC98190",
               "QuotaCode": "L-2AC98190",
               "QuotaName": "Cryptographic operations (RSA) request rate",
               "Value": 500,
               "Unit": "None",
               "Adjustable": true,
               "GlobalQuota": false
           }
       ]
   }
   ```

1. Next, call the [RequestServiceQuotaIncrease](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/API_RequestServiceQuotaIncrease.html) operation to submit tha actual request\.

   The following example requests an increase in the `Cryptographic operations (RSA) request rate` quota to `700` requests per second\. It uses the required quota code, `L-2AC98190`, to identify the quota\. If the command completes successfully, the `Status` field displays the current status of the request\. 

   ```
   $ aws service-quotas request-service-quota-increase \
           --service-code kms \
           --quota-code L-2AC98190 \
           --desired-value 700
   {
       "RequestedQuota": {
           "Id": "a12345",
           "ServiceCode": "kms",
           "ServiceName": "AWS Key Management Service (AWS KMS)",
           "QuotaCode": "L-2AC98190",
           "QuotaName": "Cryptographic operations (RSA) request rate",
           "DesiredValue": 700,
           "Status": "PENDING",
           "Created": 1580446904.067,
           "Requester": "{\"accountId\":\"123456789012\",\"callerArn\":\"arn:aws:iam::123456789012:root\"}",
           "QuotaArn": "arn:aws:servicequotas:us-east-1:123456789012:kms/L-2AC98190",
           "GlobalQuota": false,
           "Unit": "None"
       }
   }
   ```

1. To get the updated status of the request, use the [GetRequestedServiceQuotaChange](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/API_GetRequestedServiceQuotaChange.html), [ListRequestedServiceQuotaChangeHistory](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/API_ListRequestedServiceQuotaChangeHistory.html) or [ListRequestedServiceQuotaChangeHistoryByQuota](https://docs.aws.amazon.com/servicequotas/2019-06-24/apireference/API_ListRequestedServiceQuotaChangeHistoryByQuota.html) operations\.

------

After the request is resolved, the **Applied quota value** for the quota is set to the new value\.

## View quota request history<a name="quota-history"></a>

 View your quota request history in the Service Quotas console\. The console displays all open quota increase requests as well as quota requests closed in the last 90 days\.

**Note**  
Some AWS services might be available only in certain Regions\. If you have quota increase requests in different Regions, be sure to select the appropriate Region first\. 

To view the quota request history, use the following steps:

1. Sign in to the AWS Management Console and open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/home](https://console.aws.amazon.com/servicequotas/home)\.

1. To view any pending or recently resolved requests, choose **Quota request history** from the navigation pane\.

The **Recent quota increase requests** panel displays information about your open recent quota increase requests and any requests closed within 90 days\.

![\[Recent quota increase requests\]](http://docs.aws.amazon.com/servicequotas/latest/userguide/images/quota-request-history.png)
+ **Service** – Displays the service name selected for the request\.
+ **Quota name** – Displays the quota name selected for the quota increase\.
+ **Status** – Displays the status of a request for a quota increase\.

  You may see the following types of status:
  + **Closed** – Quota increase approved and request closed\.
  + **Quota request approved** – Quota increase approved automatically\. 
  + **Quota requested** – Quota increase request pending AWS Support approval\.
+ **Requested quota value** – The increased quota value you requested for the quota\.
+ **Request date** – The date you requested the quota increase\.
+ **Last updated date** – The last date the request received an update\.

View details about a service, quota name, and status in the **Quota request history** table by choosing one of the entries\.