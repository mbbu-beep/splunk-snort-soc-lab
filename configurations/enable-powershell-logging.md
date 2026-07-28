# Enable PowerShell Script Block Logging
New-Item -Path "HKLM:\Software\Policies\Microsoft\Windows\PowerShell\ScriptBlockLogging" -Force

Set-ItemProperty -Path "HKLM:\Software\Policies\Microsoft\Windows\PowerShell\ScriptBlockLogging" `
  -Name EnableScriptBlockLogging `
  -Value 1 `
  -Type DWord

# Enable PowerShell Module Logging
New-Item -Path "HKLM:\Software\Policies\Microsoft\Windows\PowerShell\ModuleLogging\ModuleNames" -Force

Set-ItemProperty -Path "HKLM:\Software\Policies\Microsoft\Windows\PowerShell\ModuleLogging" `
  -Name EnableModuleLogging `
  -Value 1 `
  -Type DWord

Set-ItemProperty -Path "HKLM:\Software\Policies\Microsoft\Windows\PowerShell\ModuleLogging\ModuleNames" `
  -Name "*" `
  -Value "*"

![PowerShell Module Logging enabled on 3Windows](10-powershell-module-logging-enabled.jpg)

*Figure 10. PowerShell Module Logging enabled on `3Windows` to increase visibility into executed PowerShell activity.*

# Enable PowerShell Operational log
wevtutil sl "Microsoft-Windows-PowerShell/Operational" /e:true
