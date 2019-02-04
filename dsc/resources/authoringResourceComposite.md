---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Sammansatta resurser – med hjälp av en DSC-konfiguration som en resurs
ms.openlocfilehash: 2823d05e0c8feb2933ca691f9ab5149ace2f7ee3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684047"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Sammansatta resurser: Använda en DSC-konfiguration som en resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

I verkliga situationer, kan konfigurationer bli långa och komplexa, anropa många olika resurser och anger ett stort antal egenskaper. För att åtgärda det här enklare, kan du använda en konfiguration för Windows PowerShell Desired State Configuration (DSC) som en resurs för andra konfigurationer. Vi kallar detta en sammansatt resurs. En sammansatt resurs är en DSC-konfiguration som tar parametrar. Parametrarna för konfigurationen fungerar som egenskaper för resursen. Konfigurationen sparas som en fil med en **. schema.psm1** tillägget och tar för både MOF-schema- och resursen skript i en typisk DSC-resurs (Mer information om DSC-resurser finns i [Windows PowerShell Desired State Configuration resurser](resources.md).

## <a name="creating-the-composite-resource"></a>Skapa en sammansatt resurs

I vårt exempel skapar vi en konfiguration som anropar ett antal befintliga resurser för att konfigurera virtuella datorer. I stället för att ange värden anges i block om konfigurationen, tar konfigurationen ett antal parametrar som sedan används i configuration-block.

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

Om du vill använda parametriserade konfigurationen som en DSC-resurs, spara den i en katalogstruktur som som någon annan MOF-baserad resurs och namnge den med en **. schema.psm1** tillägget. I det här exemplet ska vi namnge filen **xVirtualMachine.schema.psm1**. Du måste också skapa ett manifest med namnet **xVirtualMachine.psd1** som innehåller följande rad. Observera att detta förutom **MyDscResources.psd1**, modulmanifestet för alla resurser under den **MyDscResources** mapp.

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

Resursen är nu identifierbart med hjälp av cmdleten Get-DscResource och dess egenskaper kan upptäckas genom att antingen cmdleten eller **Ctrl + blanksteg** Komplettera automatiskt i Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>Med hjälp av sammansatt resurs

Därefter skapar vi en konfiguration som anropar den sammansatta resursen. Den här konfigurationen anropar xVirtualMachine sammansatta resursen om du vill skapa en virtuell dator och anropar sedan den **xComputer** resurs att byta namn på den.

```powershell

configuration RenameVM
{

    Import-DscResource -Module xVirtualMachine
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

## <a name="supporting-psdscrunascredential"></a>Stöd för PsDscRunAsCredential

>**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5.0 och senare.

Den **PsDscRunAsCredential** egenskapen kan användas i [DSC-konfigurationer](../configurations/configurations.md) resource förhindra om du vill ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.
Mer information finns i [kör DSC med autentiseringsuppgifterna för användaren](../configurations/runAsUser.md).

Du kan använda automatiska variabeln för att komma åt användarkontext från inom en anpassad resurs `$PsDscContext`.

Följande kod skulle till exempel skriva användarkontext där resursen körs till en dataström med utförliga utdata:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Se även
### <a name="concepts"></a>Begrepp
* [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
* [Kom igång med Windows PowerShell Desired State Configuration](../overview/overview.md)