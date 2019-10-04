---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Sammansatta resurser – använda en DSC-konfiguration som en resurs
ms.openlocfilehash: ef8d5665e552da01977c2f21a43246c72bb7155f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942225"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Sammansatta resurser: Använda en DSC-konfiguration som en resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

I verkliga situationer kan konfigurationer bli långa och komplexa, anropa många olika resurser och ange ett stort antal egenskaper. För att hjälpa dig att hantera den här komplexiteten kan du använda en Windows PowerShell-konfiguration för Desired State Configuration (DSC) som resurs för andra konfigurationer. Vi kallar den här sammansatta resursen. En sammansatt resurs är en DSC-konfiguration som tar parametrar. Konfigurationens parametrar fungerar som egenskaper för resursen. Konfigurationen sparas som en fil med fil namns tillägget **. schema. psm1** , och i stället för både MOF-schemat och resurs skriptet i en typisk DSC-resurs (mer information om DSC-resurser finns i [Windows PowerShell Desired State Konfigurations resurser](resources.md).

## <a name="creating-the-composite-resource"></a>Skapar den sammansatta resursen

I vårt exempel skapar vi en konfiguration som anropar ett antal befintliga resurser för att konfigurera virtuella datorer. I stället för att ange de värden som ska anges i konfigurations blocken tar konfigurationen ett antal parametrar som sedan används i konfigurations blocken.

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

Om du vill använda den parameterstyrda konfigurationen som en DSC-resurs, sparar du den i en katalog struktur som andra MOF-baserade resurser och namnger den med fil namns tillägget **. schema. psm1** . I det här exemplet ska vi ge filen namnet **xVirtualMachine. schema. psm1**. Du måste också skapa ett manifest med namnet **xVirtualMachine. psd1** som innehåller följande rad. Observera att detta är utöver **MyDscResources. psd1**-modulen manifest för alla resurser under mappen **MyDscResources** .

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

När du är färdig bör mappstrukturen vara följande:

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

Resursen kan nu upptäckas med hjälp av cmdleten Get-Dscresource Keyword Supports och dess egenskaper kan identifieras av antingen cmdleten eller genom att använda **CTRL + blank steg** komplettera i Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>Använda den sammansatta resursen

Nu ska vi skapa en konfiguration som anropar den sammansatta resursen. Den här konfigurationen anropar den sammansatta xVirtualMachine-resursen för att skapa en virtuell dator och anropar sedan **xComputer** -resursen för att byta namn på den.

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

>**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5,0 och senare.

Du kan använda egenskapen **PsDscRunAsCredential** i resurs blocket [DSC-konfigurationer](../configurations/configurations.md) för att ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.
Mer information finns i [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter.

Om du vill komma åt användar kontexten inifrån en anpassad resurs kan du använda den `$PsDscContext`automatiska variabeln.

Till exempel kan följande kod skriva användar kontexten som resursen körs till i utförlig utdataström:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Se även
### <a name="concepts"></a>Begrepp
* [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
* [Kom igång med önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md)