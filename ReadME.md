# Terrform Workspaces can be extended by the following lines to be able to run Powershell scripts to extend the given Terraform functions.

## To be able to run the following lines, a VM with internet access is needed, which will run the Script in a defined User context.
resource "azurerm_virtual_machine_extension" "powershell" {

  name                 = "powerShellScript"
  virtual_machine_id   = data.azurerm_virtual_machine.vm.id
  publisher            = "Microsoft.Compute"
  type                 = "CustomScriptExtension"
  type_handler_version = "1.10"

  settings = jsonencode({
    "fileUris" : [
      "INSERT HERE PUBLIC ACCESSABLE RAW GITHUB LINK"
    ],
    "commandToExecute"  = "powershell.exe -ExecutionPolicy Unrestricted -File FILENAME.ps1"
  })

  protected_settings = jsonencode({})
}


## With this Code no VM to execute the script execution is needed:

resource "null_resource" "script1" {  provisioner "local-exec" {    command = "Write-Host \"Hello ${var.name}\""
    interpreter = ["PowerShell", "-Command"]  }}
