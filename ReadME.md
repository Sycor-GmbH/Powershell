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
