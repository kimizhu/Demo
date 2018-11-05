<div id="page">

# Automating Azure Analysis Service Processing using Azure Automation Account

[Krishnakumar
Rukmangathan](https://social.msdn.microsoft.com/profile/Krishnakumar%20Rukmangathan)
9/1/2017 6:08:37 AM

-----

<div id="content">

  Analysis Services has been progressing day-by-day with new exciting
features and there is an ask from the users to automate the Azure
Analysis Services Processing. There are few ways which we can automate
the processing.

  - Using the conventional way what we have for the On-Prem. Using SQL
    Agent Job/ Using AMO Objects/ Using PowerShell.

Since we are dealing with Azure, we need to think about automation which
wouldn’t be dependent on the On-Prem VM to execute a PowerShell script
or any On-Prem SQL Server Instance to run the SQL Server Agent Job.
Also, there are scenarios where we need to deal with the 2-factor
authentication where we either get prompted for the phone authentication
or need to re-enter the credential while connecting to the Azure
Analysis Services.  Now think about a scenario where we are scheduling
the job that would run un -attended, there might be a possibility that
it prompts for the authentication if the AD token expires while
scheduling it with on-prem schedulers. There is different way to tackle
that, however we will not discuss this here. We have an azure automation
functionality where we can schedule the PowerShell Script to automate
the functionality with the Azure Analysis Services.  Here are the steps
we need to follow –   **Objective**: We will create partition for a fact
table and process it: TabDemo in my Azure Analysis Services Instance: 
**asazure://southeastasia.asazure.windows.net/azureasdemo**   **Steps:**
**1. Creating Azure Automation Account and adding the SQL PowerShell
Module** a. Login to <http://portal.azure.com> b. Search for “Automation
Account [![](media/2017/09/1.png)](media/2017/09/1.png) c. Create an
automation account. [![](media/2017/09/2.png)](media/2017/09/2.png) d.
Now you would be able to see the automation account which you just
created. The name is “samasutomationaccount”
[![](media/2017/09/3.png)](media/2017/09/3.png) e. You need to Import
the SQLServer PowerShell Modules first.
[![](media/2017/09/4.png)](media/2017/09/4.png) f. Click on the “Browse
Gallery” and search with “SQLServer”.
[![](media/2017/09/5.png)](media/2017/09/5.png) g. Click on the Import
and then OK button at right button corner of your screen.
[![](media/2017/09/6.png)](media/2017/09/6.png) h. You would be able to
see the SQLServer module has been imported in your automation account
gallery. [![](media/2017/09/7.png)](media/2017/09/7.png) **SQLServer
Module:** You can download load the SQL Server Module from the link if
you want to use it in the on prem:
<https://www.powershellgallery.com/packages/SqlServer/21.0.17178> Here
are the commands you can use for the Analysis Services:
<https://docs.microsoft.com/en-us/sql/analysis-services/powershell/analysis-services-powershell-reference>

|                                                                                                                                    |                                                                         |                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| [Add-RoleMember cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/add-rolemember-cmdlet)                   | Add a member to a database role.                                        | [Add](https://msdn.microsoft.com/library/microsoft.analysisservices.rolemembercollection.add\(v=SQL.130\).aspx)       |
| [Backup-ASDatabase cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/backup-asdatabase-cmdlet)             | Backup an Analysis Services database.                                   | [Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)                 |
| [Invoke-ASCmd cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/invoke-ascmd-cmdlet)                       | Execute a query or script in XMLA or TSML (JSON) format.                | [Execute](https://msdn.microsoft.com/library/mt601434\(v=sql.130\).aspx)                                              |
| [Invoke-ProcessASDatabase](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/invoke-processasdatabase)             | Process a database.                                                     | [Process](https://msdn.microsoft.com/library/ms148347\(v=SQL.130\).aspx)                                              |
| [Invoke-ProcessCube cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/invoke-processcube-cmdlet)           | Process a cube.                                                         | [Process](https://msdn.microsoft.com/library/ms148347\(v=SQL.130\).aspx)                                              |
| [Invoke-ProcessDimension cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/invoke-processdimension-cmdlet) | Process a dimension.                                                    | [Process](https://msdn.microsoft.com/library/ms148347\(v=SQL.130\).aspx)                                              |
| [Invoke-ProcessPartition cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/invoke-processpartition-cmdlet) | Process a partition.                                                    | [Process](https://msdn.microsoft.com/library/ms148347\(v=SQL.130\).aspx)                                              |
| [Invoke-ProcessTable cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/invoke-processtable-cmdlet)         | Process a table in a Tabular model, compatibility model 1200 or higher. | [Process](https://msdn.microsoft.com/library/ms148347\(v=SQL.130\).aspx)                                              |
| [Merge-Partition cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/merge-partition-cmdlet)                 | Merge a partition.                                                      | [Merge](https://msdn.microsoft.com/library/microsoft.analysisservices.partition.merge\(v=SQL.130\).aspx)              |
| [New-RestoreFolder cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/new-restorefolder-cmdlet)             | Create a folder to contain a database backup.                           | [RestoreFolder](https://msdn.microsoft.com/library/microsoft.analysisservices.restorefolder\(v=SQL.130\).aspx)        |
| [New-RestoreLocation cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/new-restorelocation-cmdlet)         | Specify one or more remote servers on which to restore the database.    | [RestoreLocation](https://msdn.microsoft.com/library/microsoft.analysisservices.restorelocation\(v=SQL.130\).aspx)    |
| [Remove-RoleMember cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/remove-rolemember-cmdlet)             | Remove a member from a database role.                                   | [Remove](https://msdn.microsoft.com/library/microsoft.analysisservices.rolemembercollection.remove\(v=SQL.130\).aspx) |
| [Restore-ASDatabase cmdlet](https://docs.microsoft.com/en-us/sql/analysis-services/powershell/restore-asdatabase-cmdlet)           | Restore a database on a server instance.                                | [Restore](https://msdn.microsoft.com/library/mt601534\(v=sql.130\).aspx)                                              |

**2. Creating Credential:** a. We need to define a credential here which
we would be using in the Powershell code later.
[![](media/2017/09/8.png)](media/2017/09/8.png) b. You need to specify
the credential which has Admin access in Azure AS Instacne and then
click on Create. The name of the credential I created is “SamCred”
[![](media/2017/09/9.png)](media/2017/09/9.png)   **3. Creating
Runbook:** a. Select the Runbook
[![](media/2017/09/10.png)](media/2017/09/10.png) b. Click on the Add
run book [![](media/2017/09/11.png)](media/2017/09/11.png) c. Enter the
below details: Choose Powershell as Runbook Type and then click on
CREATE [![](media/2017/09/12.png)](media/2017/09/12.png) **4. Create the
Powershell Cmdlet script to automate partition creation and
processing.:** a. The main objective code is to automate the creation of
the partition for the current month and delete 36<sup>th</sup> month
older partition. Go to the Runbook we created earlier. Click on Edit
[![](media/2017/09/13.png)](media/2017/09/13.png) b. Enter the Below
Power shell Script: \#\#Getting the credential which we stored earlier.
$cred = Get-AutomationPSCredential -Name 'SamCred' \#\# Providing the
Server Details $ServerName =
"asazure://southeastasia.asazure.windows.net/azureasdemo" $DatabaseName
= "TABDEMO" $TableName ="FactInternetSales" \#\# Getting the current
Month and Year $a= Get-Date \#\#$startMonth=$a.Month $startMonth=10
$startYear=$a.Year if ( $startMonth-eq 12) { $endMonth="01"
$endYear=$startYear+1 } if ( $startMonth -ne 12) { $endMonth
=$startMonth+1 $endYear=$startYear } \#\# Pad 0 at the starting if month
is in signle digit if ( $startMonth -ne 10 -or $startMonth -ne 11 -or
$startMonth -ne 12) { $startMonth=$startMonth.ToString("00") } if (
$endMonth -ne 10 -or $endMonth -ne 11 -or $endMonth -ne 12) {
$endMonth=$endMonth.ToString("00") } $startMonth $endMonth \#\#creating
the partition for the current month and current year ( You can script
out the JSON code from SSMS) $Query = "{ \`"createOrReplace\`": {
\`"object\`": { \`"database\`": \`"TABDemo\`", \`"table\`":
\`"FactInternetSales\`", \`"partition\`": \`"FactInternetSales\_"+
$startMonth+$startYear+"\`" }, \`"partition\`": { \`"name\`":
\`"FactInternetSales\_"+$startMonth+$startYear+"\`", \`"source\`": {
\`"query\`": \[ \`"SELECT \* FROM \[dbo\].\[FactInternetSales\] WHERE
ORDERDATEKEY \>= N'"+ $startYear+$startMonth+"01"+ "' AND ORDERDATEKEY
\< N'"+ $endYear+$endMonth+"01" +"'\`" \], \`"dataSource\`":
\`"SqlServer localhost AdventureWorksDW2014\`" } } } } " \#$Query
\#\#Creating the parition Invoke-ASCmd -Server $ServerName -Credential
$cred -Query $Query \#\#Processing the partition $PartName=
"FactInternetSales\_"+$startMonth+$startYear $PartName
$result=Invoke-ProcessPartition -Server $ServerName -Database
$DatabaseName -TableName $TableName -PartitionName $PartName
–RefreshType Full -Credential $cred \#\#Deleting the Old partition if
( $startMonth-eq 01) { $prevMonth="12" $prevYear=$startYear-2 } if (
$startMonth -ne 01) { $prevMonth=$startMonth-1 $prevYear=$startYear-3 }
if ( $prevMonth -ne 10 -or $prevMonth -ne 11 -or $prevMonth -ne 12) {
$prevMonth=$prevMonth.ToString("00") } $prevMonth $delQuery=" {
\`"delete\`": { \`"object\`": { \`"database\`": \`"TABDemo\`",
\`"table\`": \`"FactInternetSales\`", \`"partition\`":
\`"FactInternetSales\_"+$prevMonth + $Prevyear +" \`" } } } "
\#$delQuery Invoke-ASCmd -Server $ServerName -Credential $cred -Query
$delQuery $error\[0\].Exception.Message $error\[0\].Exception.StackTrace
  c. Click on the Test Pane. And then hit on the start to test.
[![](media/2017/09/14.png)](media/2017/09/14.png)
[![](media/2017/09/17.png)](media/2017/09/17.png) d. Schedule the
runbook. [![](media/2017/09/15.png)](media/2017/09/15.png) e. Click on
the Add Schedule and enter the details:
[![](media/2017/09/16.png)](media/2017/09/16.png)   This is how you
would be able to Schedule the Processing.  To know more about azure
automation, please refer the link below:
<https://docs.microsoft.com/en-us/azure/automation/automation-intro>
<https://azure.microsoft.com/en-in/pricing/details/automation/>    
**Author:**<span>     Samarendra Panda - Support Engineer, SQL Server BI
Developer team, Microsoft</span> **Reviewer:**<span>  </span>Kane Conway
– Support Escalation Engineer, SQL Server BI Developer team, Microsoft  

</div>

</div>
