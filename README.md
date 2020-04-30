
# Storage Tier Cost Analysis Dashboard for vRealize Operations 8.1
---------

Use this [vRealize Operations](https://www.vmware.com/products/vrealize-operations.html) dashboard to expore storage costs by tiers.  The cost engine in vRealize Operations allows setting storage base rates (cost per GB per month) using vSphere Tags.  Creating custom groups for the storage vSphere Tags can be leveraged to provide better insight into storage cost and utilization.  To use the dashboard, select a Storage Tier from the list to see utilization, cost, and potential savings for the entire tier.  Select a datastore to invesigate from one of the top-n views to see the details for the specific datastore.

Please note that this dashboard requires additional configuration after importing.  Refer to the [Configuration section](#Configuration) below for details.

## Dashboard
![Dashboard](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/Dashboard.png)

## Installation
1. Import the custom groups at `Environment` / `Custom Groups` / `Gear Icon` / `Import Custom Group(s)`  
![Import Custom Groups](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/CustomGroups_Import.png)
2. Click `Browse...` then select the file named [CustomGroups.json](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/CustomGroups.json)
3. The included custom groups are listed in the [Custom Groups section](#Custom-Groups).  
4. Import the super metrics at `Administration` / `Configuration` / `Super Metrics` / `Import Super Metric`  
![Import Super Metric](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/Supermetric_Import.png)
5. Click `Browse...` then select the file named [supermetric.json](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/supermetric.json)
6. For each Super Metric listed in the [Super Metrics section](#Super-Metrics), click on the vertical kebab and select edit.  
![Policy Metrics](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/Supermetric_Edit.png)
7. Enable the Super Metric for each Policy shown in the `Enable in a Policy` stage of the wizard.
![Policy Library](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/Supermetric_Policy.png)
8. Repeat the previous 2 steps for the remaining Super Metrics listed in the [Super Metrics section](#Super-Metrics).
9. Import the view at `Dashboards` / `Views` / `Import...`  
![Import View](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/View_Import.png)
10. Click `Browse...` then select the file named [Views.zip](https://github.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/raw/master/Views.zip)
11. The included views are listed in the [Views section](#Views)
12. Import the dashboard at `Dashboards` / `Actions` / `Manage Dashboards` / `Import Dashboards`  
![Import Dashboard](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/Dashboard_Import.png)
13. Click `Browse...` then select the file named [Dashboard.zip](https://github.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/raw/master/Dashboard.zip)
14. The dashboard should now be available in in the dashboard list  
![Dashboard List](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/Dashboard_List.png)
15. The included dashboards are listed in the [Dashboards section](#Dashboards)

## Configuration
1. Identify the stoage tag category and tag value used in Cost Drivers at `Administration` / `Configuration` / `Cost Settings` / `Cost Drivers` / `Storage`.  Take a screenshot if needed as the tags are needed in subsequent steps.
![Storage Tag Category](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/Storage_Tag_Category.png)
2. Navigate to `Environment` / `Custom Groups` to see the list of custom groups.
![Custom Groups List](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/CustomGroups_List.png)
3. Edit each custom group in the included [Custom Groups](#Custom-Groups) and change the category of `Storage Tier` to the storage tag category name from step 1.
![Edit Custom Groups](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/CustomGroups_Edit.png)
4. For each tag value identified in step 1, create a custom group with a group type of `Storage Tier`, `Keep group membership up to date` enabled, and a rule for datastores that have `Summary|vSphere Tag` property which contains the tag value.  Use the format of `<Storage Tier-Tier Name>`, where `Storage Tier` is the tag category and `Tier Name` is the tag value.  Use the `Preview` to validate the rule before saving.
![Edit Custom Groups](https://raw.githubusercontent.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/master/images/CustomGroups_New.png)
5. Repeat the previous step until there is a custom group for each tag value identified in step 1.
6. After about 20 minutes the `Storage Tiers` widget in the dashboard should start showing the new metrics.

## Dashboards
| Dashboard Name | Dashboard Path |
|--|--|
| Storage Tier Cost Analysis | Shared Dashboards (GBrandon)/Cost |

## Views
| View Name | Name on Dashboard | View Type |
|--|--|--|
| Storage Base Rates | Storage Base Rate | Distribution |

## Custom Groups
| Custom Group Name | Group Type |
|--|--|
| Untagged Local Storage | Storage Tier |
| Untagged Shared Storage | Storage Tier |

## Super Metrics
| Super Metric Name | Object Type |
|--|--|
| Storage Tier - Total Cost | Storage Tier |
| Storage Tier - Potential Savings | Storage Tier |
| Storage Tier - Total Capacity (GB) | Storage Tier |
| Storage Tier - Used Space (GB) | Storage Tier |
| Storage Tier - Provisioned Consumer Space | Storage Tier |
| Storage Tier - Reclaimable Orphaned Disk Space | Storage Tier |

## Support

This dashboard requires vRealize Operation 8.1 Advanced or Enterprise edition.

Please open an [issue](https://github.com/notoriousbdg/vrops-dashboard-storage_tier_cost_analysis/issues) for feedback.

## Changelog
2020-04-30
* Initial release
