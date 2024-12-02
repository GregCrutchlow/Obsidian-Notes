Creating email consent for a new account within [[Go High Level]] (GHL) should be done early on to allow for subsequent forms and funnels to be created with the consent already embed within the form.

## Creating Custom Fields

First you create [[ Custom Fields ]] within [[ Settings ]] within a [[ Sub-Account ]]. You should create folders to stay organized and to find everything quickly.

1. Log into [[Go High Level]] and choose a [[Sub-Account]] to create the email consent fields.
2. Within the [[Settings]] (bottom of left hand menu) select [[Custom Fields]] within [[Other Settings]].
3. Select the "**Folders**" tab at the top of the page and then create a folder by clicking "Add Folder" button at the top right of the page. Name this "Email Consent".
4. Within this folder create 4 fields: 
	1. Email Consent (Dropdown field) with 2 options: "**Subscribed**" and "**Unsubscribed**"
	2. Email Consent Timestamp (Date Picker field)
	3. Email Consent - Subscribe Trigger (Checkbox field) with 1 option: "**I Agree**"
	4. Email Consent - Unsubscribe Trigger (Checkbox field) with 1 option: "**Unsubscribe**"

With these created, this will allow you to create automations and streamline the process.

## Creating Custom Value

Creating a custom value for the consent copy will allow it to stay uniform across all forms which it is added to. If copy needs to change between forms, another field can be created for that purpose, but this allows that any changes made to this value, it will change for all forms, keeping a well organized form.

1. Within [[Settings]] (bottom of left hand menu) select [[Custom Values]] within [[Other Settings]]
2. Click "New Custom Value" at the top right of the page and create a field called "Email Consent Form Text" with the value being the copy for the consent (example: "I agree to allow Daymark Career Coaching to contact me by email. I may withdraw my consent at any time through the unsubscribe link. See our Privacy Policy below for more details on how we protect your personal information.")

## Creating Workflow Automations

Creating Workflow [[Automations]] allows for processes to happen automatically without the need for a person to manually do the work. This allows for users on the site to be automatically enrolled to marketing emails as well as other processes if needed. This allows for smooth enrollments/disenroll for marketing emails.

The easiest way to do this would be to copy [[Automations]] from another [[Sub-Account]], but we'll break down the process here.

1. Within "Automation" in the left hand menu, create a new folder by clicking "Create Folder" at the top right of the page. Name this folder "[Operational] Email Consent". Then click into this folder.
2. Create a new "[[Workflow]]" by clicking "Create Workflow" at the top right of the page. 
3. Name this workflow "Email Consent - Subscribe Trigger" the top center of the page. Here we will outline the triggers and the subsequent tasks to automatically be done when the triggers happen.
4. Create a [[Trigger]] by clicking "Add New Trigger". This trigger will be called "Contact Created - Email Consent" within the "Workflow Trigger Name" field.
5. Under [[Filters]] click "Add filters" and select "Email Consent - Subscribe Trigger" and then "I Agree" in the new field to the right of this field. This means that when the checkbox for "Email Consent - Subscribe Trigger" is checked and "I Agree" has been selected, this will trigger the workflow.
6. 