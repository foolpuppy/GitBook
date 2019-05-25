# Sublime Text3 添加到右键菜单

* w

  PS:**需要把里边的Sublime的安装目录，替换成实际的Sublime安装目录。**

  ```text
  Windows Registry Editor Version 5.00
  [HKEY_CLASSES_ROOT\*\shell\SublimeText3]
  @="用 SublimeText3 打开"
  "Icon"="D:\\Program Files\\Sublime Text 3\\sublime_text.exe,0"

  [HKEY_CLASSES_ROOT\*\shell\SublimeText3\command]
  @="D:\\Program Files\\Sublime Text 3\\sublime_text.exe %1"


  [HKEY_CLASSES_ROOT\Directory\shell\SublimeText3]
  @="用 SublimeText3 打开"
  "Icon"="D:\\Program Files\\Sublime Text 3\\sublime_text.exe,0"

  [HKEY_CLASSES_ROOT\Directory\shell\SublimeText3\command]
  @="D:\\Program Files\\Sublime Text 3\\sublime_text.exe %1"
  ```

*   附一个删除右键菜单的脚本吧。

  把以下代码，复制到SublimeText3的安装目录，然后重命名为：sublime\_delright.reg，然后双击就可以了。

  ```text
  Windows Registry Editor Version 5.00
  [-HKEY_CLASSES_ROOT\*\shell\SublimeText3]
  [-HKEY_CLASSES_ROOT\Directory\shell\SublimeText3]
  ```

* bat Version
* @ECHO OFF & PUSHD %~DP0 & TITLE

  > NUL 2&gt;&1 REG.exe query "HKU\S-1-5-19" \|\| \( ECHO SET UAC = CreateObject^\("Shell.Application"^\) &gt; "%TEMP%\Getadmin.vbs" ECHO UAC.ShellExecute "%~f0", "%1", "", "runas", 1 &gt;&gt; "%TEMP%\Getadmin.vbs" "%TEMP%\Getadmin.vbs" DEL /f /q "%TEMP%\Getadmin.vbs" 2&gt;NUL Exit /b \) SET /P ST=Input 'a' to add, input 'd' to delete : if /I "%ST%"=="a" goto Add if /I "%ST%"=="d" goto Remove :Add reg add "HKEY\_CLASSES\_ROOT\*\shell\Sublime Text" /t REG\_SZ /v "" /d "Open with &Sublime Text" /f reg add "HKEY\_CLASSES\_ROOT\*\shell\Sublime Text" /t REG\_EXPAND\_SZ /v "Icon" /d "%~dp0sublime\_text.exe" /f reg add "HKEY\_CLASSES\_ROOT\*\shell\Sublime Text\command" /t REG\_SZ /v "" /d "%~dp0sublime\_text.exe \"%%1\"" /f

  exit :Remove reg delete "HKEY\_CLASSES\_ROOT\*\shell\Sublime Text" /f exit

