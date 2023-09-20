# Invoke-AdminSDHolderPermissionCheck
### Analyzes AdminSDHolder permissions &amp; compares with a previous run, to detect potential backdoor/excessive persistent permission(s)
Does not require any special permissions to query and dump the permissions to CSV, as well as compare them.<br>If option to check for additional info from DC event logs is specified, then requires 'Event Log Readers' or equivalent permission.<br>Requires ActiveDirectory powershell module.<br>

.DESCRIPTION<br>
Analyzes AdminSDHolder ACL permissions & saves them, as well as checks for changes from a previous run. 
Can be useful for detecting a potential backdoor, and/or excessive & persistent permissions.
Can run without parameters to dump current permissions to CSV, or compare permissions with a previous run.
<br><br>
.PARAMETER PreviousCSVFile<br>
Full path to a CSV file from previous run of the script, to compare with the current online permissions of the AdminSDHolder object.
<br><br>
.PARAMETER OptionalCheckForDCsEventLog<br>
If specified, will also check for DC Security Event Logs (Requires 'Event Log Readers' permission or privileged).
<br><br>
.EXAMPLE<br>
.\Invoke-AdminSDHolderPermissionCheck.ps1<br><br>
Analyzes AdminSDHolder ACL permissions, shows the timestamp of the last update, and saves permissions to a csv file.
<br><br>
.EXAMPLE<br>
.\Invoke-AdminSDHolderPermissionCheck.ps1 -PreviousCSVFile C:\temp\AdminSDHolder_Permissions_ADATUM_17092023.csv<br><br>
Analyzes current AdminSDHolder permissions & compares them with the data from the specified CSV file. Previous CSV must be from a previous run of this script, or exact structure/headers.

![Sample run of the script](comparing_permissions_screenshot.png)

<br>
.EXAMPLE<br>
.\Invoke-AdminSDHolderPermissionCheck.ps1 -PreviousCSVFile C:\temp\AdminSDHolder_Permissions_ADATUM_17092023.csv -OptionalCheckForDCsEventLog<br><br>
Analyzes current AdminSDHolder permissions & compares them with the data from the specified CSV file. Previous CSV must be from a previous run of this script, or exact structure/headers.In addition, check Security event logs on DCs for additional information -e.g. who made the change for the ACL (Requires 'Event Log Readers' permission or other privileged).

![Sample run of the script](checkDCLogs_screenshot.png)
