# Predict Incident Resolution Time with AutoAI

Brief introduction...

# About the data set

This data set contains incidents reported through ServiceNow since October 2020.

## incident.csv

This CSV file contains incident dimension data.

| Field | Description | Type |
| :--- | :--- | :--- |
| number | Incident unique identifier | String |
| caller_id.employee_number | Employee ID of the caller used to get the profile | String |
| u_on_behalf_of.employee_number | Environment provisioning and setup | String |
| location | Caller location address automatically added based on their profile. Can be modified based on the current location of the caller | String |
| u_floor | Floor automatically added based on caller profile. Can be modified based on the current location of the caller | String |
| u_room | Room automatically added based on caller profile. Can be modified based on the current location of the caller | String |
| category | Used to categorize the incident. Examples: **Hardware**, **Software**, **Inquiry/Help**, etc. | String |
| subcategory | The selected `category` define the options available for the `subcategory`. Examples: **Clinical System**, **Access**, etc. | String |
| business_service |  | String |
| cmdb_ci | Impacted device | String |
| contact_type | Defines the method the incident originated. Examples: **Phone**, **Virtual Agent**, etc. | String |
| parent |  | String |
| state | Defines the lifecycle stage of the incident. Examples: **In Progress**, **Resolved**, **Closed**, etc. All incidents start at **New** | String |
| impact | Defines the number of affected people or locations | String |
| urgency | Defines how quickly the incident should be resolved | String |
| priority | Provides guidance related to the sequence in which incidents need to be resolved and is automatically calculated based on `impact` and `urgency` selections | String |
| assignment_group | Used to determine who will work on the incident | String |
| assigned_to | When and individual is designated the `assigned_to` (not required to submit an incident), the incident moves to the `state` **In Progress** | String |
| short_description | Used to describe the incident reported. **May contain PHI** | String |
| description | Used to expand on the `short_description`. It should be used to add context to the issue reported. **May contain PHI** | String |
| close_code | Resolution code. Example: **Solved (Permanently)**, **Closed/Resolved by Caller** | String |
| close_notes | Resolution information. Defines what was done to resolve the incident | String |
| resolved_by.employee_number | Employee ID that resolved the issue | String |
| resolved_at | Time when the issues was marked as resolved | Timestamp |
| work_notes | Updates to the form | String |

## incident_sla.csv

Data extracted from the incident SLA fact table.

| Field | Description | Type |
| :--- | :--- | :--- |
| inc_number | Incident unique identifier. Can be used to join `incident.number` | String |
| taskslatable_sla | Indicates response or resolution associated SLA | String |
| taskslatable_stage | Define the lifecycle stage of the incident | String |
| taskslatable_has_breached | Indicates if the response time has exceeded the SLA | Boolean |
| inc_business_duration | Work time for the incident to be resolved in seconds  | Number |
| inc_calendar_duration | Calendar time for the incident to be resolved in seconds | Number |
| taskslatable_schedule | Work schedule assigned to the incident | String |
| taskslatable_start_time | Incident start time | Timestamp |
| taskslatable_end_time | Incident end time | Timestamp |

