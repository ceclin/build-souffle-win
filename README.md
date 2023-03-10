# build-souffle-win

## 如何使用

1. 下载 Github Action 或 Nightly Pre-release 里的 souffle.zip 或 souffle-static.zip。
2. 解压后把 bin 目录添加到 Path 环境变量。
3. 修改 bin 目录中的 souffle-compile.py，可以使用本仓库中的 souffle-compile-msvc.py 作为参考。

推荐使用 MSVC ，但 MSVC 版本需要在终端激活开发者环境后使用 (vcvarsall.bat)。

## Powershell 激活 MSVC 环境

```powershell
function Activate-VC {
    [CmdletBinding()] 
    param (
        [ValidateSet("x86", "amd64", "arm", "arm64")]
        [string]$TargetArch = "amd64",

        [ValidateSet("x86", "amd64")]
        [string]$HostArch = "amd64"
    )
    # Modify the following line corresponding to your environment.
    $VS = "C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools"
    Import-Module $VS"\Common7\Tools\Microsoft.VisualStudio.DevShell.dll"
    Enter-VsDevShell -VsInstallPath $VS -Arch $TargetArch -HostArch $HostArch
}
```
