# choco-setup

function Install-ChocolateyPackage {
  param (
    [Parameter(Mandatory, Position=0)]
    [string]$PackageName,

    [string]$Source,

    [alias("Params")]
    [string]$PackageParameters,

    [string]$Version,

    [alias("Pre")]
    [switch]$Prerelease,

    [switch]$UseInstallNotUpgrade
  )

  $chocoExecutionArgs = "choco.exe"
  if ($UseInstallNotUpgrade) {
    $chocoExecutionArgs += " install"
  } else {
    $chocoExecutionArgs += " upgrade"
  }

  $chocoExecutionArgs += " $PackageName -y --source='$Source'"
  if ($Prerelease) { $chocoExecutionArgs += " --prerelease"}
  if ($Version) { $chocoExecutionArgs += " --version='$Version'"}
  if ($PackageParameters -and $PackageParameters -ne '') { $chocoExecutionArgs += " --package-parameters='$PackageParameters'"}

  Invoke-Expression -Command $chocoExecutionArgs
  $exitCode = $LASTEXITCODE
  $validExitCodes = @(0, 1605, 1614, 1641, 3010)
  if ($validExitCodes -notcontains $exitCode) {
    throw "Error with package installation. See above."
  }
}

Install-ChocolateyPackage instchoco -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 2.11
Install-ChocolateyPackage visualstudio2019-workload-netcorebuildtools -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 1.0.1
Install-ChocolateyPackage 1clipboard -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 0.1.8
Install-ChocolateyPackage dotnetcore3-desktop-runtime -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 3.1.16
Install-ChocolateyPackage dotnet5-desktop-runtime -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 5.0.6
Install-ChocolateyPackage adoptopenjdk8 -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 8.292.10.901
Install-ChocolateyPackage chocolatey-uninstall.extension -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 1.2.0
Install-ChocolateyPackage mono3 -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 3.2.3.20150323
Install-ChocolateyPackage nodejs.commandline -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 6.11.0
Install-ChocolateyPackage revo.uninstaller -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 2.0.2.020180924
Install-ChocolateyPackage geforce-game-ready-driver-win10 -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 378.92
Install-ChocolateyPackage google-drive-file-stream -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 56.0.11.2022
Install-ChocolateyPackage google-backup-and-sync -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 99.99.99.99
Install-ChocolateyPackage intel.ssd.toolbox -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 3.5.15.20210102
Install-ChocolateyPackage intel-driver-update-utility -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 3.1.1.220180112
Install-ChocolateyPackage javaruntime-platformspecific -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 7.0.79.20161125
Install-ChocolateyPackage lan-speed-test-lite -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 1.3.2.20180101
Install-ChocolateyPackage lan-speed-test-registered -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 3.5.20180101
Install-ChocolateyPackage advanced-ip-scanner -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 2.5.3850
Install-ChocolateyPackage advtor -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 0.3.1.2
Install-ChocolateyPackage advancedsystemtweaker -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 2.0.0.20141128
Install-ChocolateyPackage adwcleaner -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 8.3.2
Install-ChocolateyPackage airtest-ide -Source https://github.com/SaviorVii/SaviorVii/upload/main -Version 1.2.7.20210207
