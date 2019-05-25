# Sublime Text3 添加到右键菜单

* .bat版本

```text
@ECHO OFF & PUSHD %~DP0 & TITLE
>NUL 2>&1 REG.exe query "HKU\S-1-5-19" || (
    ECHO SET UAC = CreateObject^("Shell.Application"^) > "%TEMP%\Getadmin.vbs"
    ECHO UAC.ShellExecute "%~f0", "%1", "", "runas", 1 >> "%TEMP%\Getadmin.vbs"
    "%TEMP%\Getadmin.vbs"
    DEL /f /q "%TEMP%\Getadmin.vbs" 2>NUL
    Exit /b
)
SET /P ST=Input 'a' to add, input 'd' to delete : 
if /I "%ST%"=="a" goto Add
if /I "%ST%"=="d" goto Remove
:Add
reg add "HKEY_CLASSES_ROOT\*\shell\Sublime Text"         /t REG_SZ /v "" /d "Open with &Sublime Text"   /f
reg add "HKEY_CLASSES_ROOT\*\shell\Sublime Text"         /t REG_EXPAND_SZ /v "Icon" /d "%~dp0sublime_text.exe" /f
reg add "HKEY_CLASSES_ROOT\*\shell\Sublime Text\command" /t REG_SZ /v "" /d "\"%~dp0sublime_text.exe\" \"%%1\"" /f
 
exit
:Remove
reg delete "HKEY_CLASSES_ROOT\*\shell\Sublime Text" /f
exit
```

