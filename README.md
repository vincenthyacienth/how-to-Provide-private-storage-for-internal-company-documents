# How To Provide Private Storage For Internal Company Documents
## Lets try this exercise;
The company needs storage for their offices and departments. This content is private to the company and shouldn’t be shared without consent. This storage requires high availability if there’s a regional outage. The company wants to use this storage to back up the public website.
## Exercise Instructions
## Create A Storage Account And Configure High Availability.
1. Create a storage account for the internal private company documents.
- In the portal, search for and select Storage accounts.
- Select + Create.
- Select the Resource group created in the previous lab.
- Set the Storage account name to private. Add an identifier to the name to ensure the name is unique.
- Select Review, and then Create the storage account.
- Wait for the storage account to deploy, and then select Go to resource.
2. This storage requires high availability if there’s a regional outage. Read access in the secondary region is not required. Configure the appropriate level of redundancy.
- In the storage account, in the Data management section, select the Redundancy blade.
- Ensure Geo-redundant storage (GRS) is selected.
- Refresh the page.
- Review the primary and secondary location information.
- Save your changes.
## Create A Storage Container, Upload A File, And Restrict Access To The File.
1. Create a private storage container for the corporate data.
- In the storage account, in the Data storage section, select the Containers blade.
- Select + Container.
- Ensure the Name of the container is private.
- Ensure the Public access level is Private (no anonymous access).
- As you have time, review the Advanced settings, but take the defaults.
- Select Create.
2. For testing, upload a file to the private container. he type of file doesn’t matter. A small image or text file is a good choice. Test to ensure the file isn’t publically accessible.
- Select the container.
- Select Upload.
- Browse to files and select a file.
- Upload the file.
- Select the uploaded file.
- On the Overview tab, copy the URL.
- Paste the URL into a new browser tab.
- Verify the file doesn’t display and you receive an error.
3. An external partner requires read and write access to the file for at least the next 24 hours. Configure and test a shared access signature (SAS).
- Select your uploaded blob file and move to the Generate SAS tab.
- In the Permissions drop-down, ensure the partner has only Read permissions.
- Verify the Start and expiry date/time is for the next 24 hours.
- Select Generate SAS token and URL.
- Copy the Blob SAS URL to a new browser tab.
- Verify you can access the file. If you have uploaded an image file it will display in the browser. Other file types will be downloaded.
## Configure Storage Access Tiers And Content Replication.
1. To save on costs, after 30 days, move blobs from the hot tier to the cool tier.
- Return to the storage account.
- In the Overview section, notice the Default access tier is set to Hot.
- In the Data management section, select the Lifecycle management blade.
- Select Add rule.
- Set the Rule name to movetocool.
- Set the Rule scope to Apply rule to all blobs in the storage account.
- Select Next.
- Ensure Last modified is selected.
- Set More than (days ago) to 30.
- In the Then drop-down select Move to cool storage.
- As you have time, review other lifecycle options in the drop-down.
- Add the rule.
2. The public website files need to be backed up to another storage account.
- In your storage account, create a new container called backup. Use the default values. Refer back to Lab 02a if you need detailed instructions.
- Navigate to your publicwebsite storage account. This storage account was created in the previous exercise.
- In the Data management section, select the Object replication blade.
- Select Create replication rules.
- Set the Destination storage account to the private storage account.
- Set the Source container to public and the Destination container to backup.
- Create the replication rule.
- Optionally, as you have time, upload a file to the public container. Return to the private storage account and refresh the backup container. Within a few minutes your public website file will appear in the backup folder.
