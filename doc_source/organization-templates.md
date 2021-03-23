# Using Service Quotas request templates<a name="organization-templates"></a>

A *quota request template *helps you save time when customizing quotas for new accounts in your organization\. To use a template, configure the desired service quota increases for new accounts\. Then, enable template association\. This associates the template with your organization in AWS Organizations\. Whenever new accounts are created in your organization, the template automatically requests quota increases for you\.

To use a request template, you must use AWS Organizations and the new accounts must be created in the same organization\. Your organization must use the features set, [all features](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html)\. If you use consolidated billing features, you can't use quota request templates\.

You can update the request template by adding or removing service quotas\. You can also increase the values for adjustable quotas\. As soon as you adjust the template, those service quota values are requested for new accounts\. Updating a request template does not update quota values for existing accounts\.

**To enable template association**

1. Open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/](https://console.aws.amazon.com/servicequotas/)\.

1. In the navigation pane, choose **Quota request template**\. If the **Quota request template** isn't visible, choose **Organization** to open it\.

1. In the **Template association** section, choose **Enable**\.

**To add a quota to your request template**

1. Open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/](https://console.aws.amazon.com/servicequotas/)\.

1. In the navigation pane, choose **Quota request template**\. If the **Quota request template** isn't visible, choose **Organization** to open it\.

1. In the **Added quotas** section, choose **Add quota**\.
**Note**  
You add up to 10 quotas to your request template\.

1. On the **Add quota** page, choose a **Region**, **service**, **quota**, and **quota value**, and then choose **Add**\.

**To remove a quota from your request template**

You can remove service quota requests from the template whether the template is associated with an organization or not\. If you reach the maximum number of service quota requests, you might need to remove some quotas from your request template\.

1. Open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/](https://console.aws.amazon.com/servicequotas/)\.

1. In the navigation pane, choose **Quota request template**\. If the **Quota request template** isn't visible, choose **Organization** to open it\.

1. In the **Added quotas** section, select the radio button for the quota that you want to remove\.

1. Choose **Remove**\.

**To disable the template association**

If you disable the quota, new accounts receive the AWS default quota values for all quotas\. Disabling the template association from the organization doesn't delete the service quota requests from the template\. You can continue to edit the service quotas in the template\.

1. Open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/](https://console.aws.amazon.com/servicequotas/)\.

1. In the navigation pane, choose **Quota request template**\. If the **Quota request template** isn't visible, choose **Organization** to open it\.

1. In the **Template association** section, choose **Disable**\.