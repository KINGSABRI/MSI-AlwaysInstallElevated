# WXS Templates

## Templates description 

### ⟿ alwaysInstallElevated-1.wxs
a wxs template to execute system commands.

### ⟿ alwaysInstallElevated-2.wxs
a wxs template to execute command then intentionally fails so it won't be registered as an installed program.

**Important Treadcraft:**

Although forcing MSI installation to fail saves us registring the package on the system,
It leaves a log file `C:\Users\<User>\AppData\Local\Temp\<RandomName>.log*` for that failure on disk exposing details about the msi package
example: 
```
  Error 1721. There is a problem with this Windows Installer package. A program required for this install to complete could not be run. 
  Contact your support personnel or package vendor. 
  Action: z_gonna_fail, location: C:\Users\<User>\AppData\Local\Temp\<PATH>, command: C:\Users\<User>\AppData\Local\Temp\>PATH>\asdfasdfasdf.exe 
  === Logging stopped: 8/5/2020  12:23:06 ===
```

To *partially* solve this issue, specify the log path to the current path with logging fatal errors only (then delete the log file yourself), as the following
```
msiexec /i malware.msi /qn /Lm deleteme.log
```

### ⟿ alwaysInstallElevated-3.wxs
a wxs template to embed executable (exe) file into the msi package and execute it during installation.

### ⟿ alwaysInstallElevated-4.wxs
a wxs template combines the techniques of `alwaysInstallElevated-2`and `alwaysInstallElevated-3` templates.


### ⟿ alwaysInstallElevated-5.wxs
a wxs template to embed executable (DLL) file into the msi package and execute it (based on its entry function) during installation.

## Resources 
* https://stackoverflow.com/questions/854873/how-to-make-an-msi-that-simply-wraps-an-exe-file
* https://serverfault.com/questions/11670/the-corporate-benefits-of-using-msi-files/274609#274609
* https://isc.sans.edu/forums/diary/Malware+Delivered+via+Windows+Installer+Files/23349/
* https://wixtoolset.org/documentation/manual/v3/xsd/wix/customaction.html
