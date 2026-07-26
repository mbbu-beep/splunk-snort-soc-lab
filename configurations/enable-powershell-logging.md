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

# Enable PowerShell Operational log
wevtutil sl "Microsoft-Windows-PowerShell/Operational" /e:true
