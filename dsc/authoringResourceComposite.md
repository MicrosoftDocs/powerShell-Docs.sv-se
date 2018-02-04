---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Sammansatta resurser--med hjälp av DSC-konfigurationen som en resurs"
ms.openlocfilehash: 1d5fb89eb9845820de8543f388ddb6aaeaaa3e44
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2018
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Sammansatta resurser: med hjälp av DSC-konfigurationen som en resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

I verkliga situationer kan konfigurationer bli långa och komplexa, anropar många olika resurser och anger ett omfattande antal egenskaper. Om du vill åtgärda det här komplexitet, kan du använda en konfiguration för Windows PowerShell önskad tillstånd Configuration DSC () som en resurs för andra konfigurationer. Vi kallar detta en sammansatt resurs. En sammansatt resurs är en DSC-konfiguration som parametrar. Parametrarna för konfigurationen fungerar som egenskaper för resursen. Konfigurationen sparas som en fil med en **. schema.psm1** tillägget och tar både MOF-schemat och resursen skript i en typisk DSC-resurs (Mer information om DSC-resurser finns [Windows PowerShell Desired State Configuration resurser](resources.md).

## <a name="creating-the-composite-resource"></a>Att skapa sammansatta resurs

I vårt exempel skapar vi en konfiguration som anropar ett antal befintliga resurser för att konfigurera virtuella datorer. I stället för att ange värden anges i konfigurationen block tar konfigurationen ett antal parametrar som sedan används i configuration-block.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a>Spara konfigurationen som en sammansatt resurs

Om du vill använda parametriserade konfigurationen som en DSC-resurs, spara den i en katalogstruktur precis som alla andra MOF-baserade resurser, och ger den namnet med en **. schema.psm1** tillägg. I det här exemplet ska vi namnge filen **xVirtualMachine.schema.psm1**. Du måste också skapa ett manifest med namnet **xVirtualMachine.psd1** som innehåller följande rad. Observera att detta förutom **MyDscResources.psd1**, modulmanifestet för alla resurser under den **MyDscResources** mapp.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

När du är klar ska mappstrukturen på följande sätt.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

Resursen är nu identifiera med hjälp av cmdleten Get-DscResource och dess egenskaper är synliga genom att antingen cmdlet eller **Ctrl + blanksteg** automatisk komplettering i Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>Med hjälp av den sammansatta resursen

Därefter skapar vi en konfiguration som anropar sammansatta resursen. Den här konfigurationen anropar xVirtualMachine sammansatta resurs för att skapa en virtuell dator, och anropar sedan den **xComputer** resurs för att byta namn på den.

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a>Supporting PsDscRunAsCredential

>**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5.0 och senare.

Den **PsDscRunAsCredential** egenskapen kan användas i [DSC-konfigurationer](configurations.md) resurs förhindra om du vill ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.
Mer information finns i [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).

Du kan använda automatiska variabeln för att komma åt användarkontext från inom en anpassad resurs `$PsDscContext`.

Följande kod skulle till exempel skriva användarkontext som resursen körs under till dataströmmen utförliga utdata:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Se även
### <a name="concepts"></a>Begrepp
* [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
* [Kom igång med Windows PowerShell Desired State Configuration](overview.md)

