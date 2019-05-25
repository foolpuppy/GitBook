# Sublime Text3 添加到右键菜单

*   PS:**需要把里边的Sublime的安装目录，替换成实际的Sublime安装目录。**

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

