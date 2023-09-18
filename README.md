# Invoke-AdminSDHolderPermissionCheck
Analyzes AdminSDHolder permissions &amp; compares with a previous run, to detect potential backdoor/excessive persistent permission(s)

.DESCRIPTION<br>
Analyzes AdminSDHolder ACL permissions & saves them, as well as checks for changes from a previous run. 
Can be useful for detecting a potential backdoor, and/or excessive & persistent permissions.
Can run without parameters to dump current permissions to CSV, or compare permissions with a previous run.
<br><br>
.PARAMETER PreviousCSVFile<br>
Full path to a CSV file from previous run of the script, to compare with the current online permissions of the AdminSDHolder object.
<br><br>
.EXAMPLE<br>
.\Invoke-AdminSDHolderPermissionCheck.ps1<br>
Analyzes AdminSDHolder ACL permissions, shows the timestamp of the last update, and saves permissions to a csv file.
<br><br>
.EXAMPLE<br>
.\Invoke-AdminSDHolderPermissionCheck.ps1 -PreviousCSVFile C:\temp\AdminSDHolder_Permissions_ADATUM_17092023.csv<br>
Analyzes current AdminSDHolder permissions & compares them with the data from the specified CSV file. Previous CSV must be from a previous run of this script, or exact structure/headers.
