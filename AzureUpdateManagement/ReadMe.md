# Powershell Script needs to be written, including these Input Parameters to add Varaibles to the Terraform Update Management Rollout
Input Parameters
 New-AzPatchConfiguration object use New-AzPatchConfiguration
keyvalues
1, Name
2. Resourcegroup
3. OS (Windows, Linux)
4. Include (List of KBs to update)
5. Exclude (List of excluded KBs)
6. AzureVirtualMachines (List of Azuer VMs)
7. RebootSettings (Always, IfRequired, Never)
8. StartTime(Maintenance windows)

Start-AzPatchComplianceScan 
1. ConfigurationName
2. ResourceGroupName
