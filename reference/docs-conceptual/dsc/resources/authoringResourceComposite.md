---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Sammansatta resurser – använda en DSC-konfiguration som en resurs
ms.openlocfilehash: 7fa6ee56d4706b96fb47123c7aa00c4df6256492
ms.sourcegitcommit: 14b50e5446f69729f72231f5dc6f536cdd1084c3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73933830"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="7ce86-103">Sammansatta resurser: använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="7ce86-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="7ce86-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="7ce86-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7ce86-105">I verkliga situationer kan konfigurationer bli långa och komplexa, anropa många olika resurser och ange ett stort antal egenskaper.</span><span class="sxs-lookup"><span data-stu-id="7ce86-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="7ce86-106">För att hjälpa dig att hantera den här komplexiteten kan du använda en Windows PowerShell-konfiguration för Desired State Configuration (DSC) som resurs för andra konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="7ce86-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="7ce86-107">Vi kallar den här sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="7ce86-107">We call this a composite resource.</span></span> <span data-ttu-id="7ce86-108">En sammansatt resurs är en DSC-konfiguration som tar parametrar.</span><span class="sxs-lookup"><span data-stu-id="7ce86-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="7ce86-109">Konfigurationens parametrar fungerar som egenskaper för resursen.</span><span class="sxs-lookup"><span data-stu-id="7ce86-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="7ce86-110">Konfigurationen sparas som en fil med fil namns tillägget **. schema. psm1** , och i stället för både MOF-schemat och resurs skriptet i en typisk DSC-resurs (mer information om DSC-resurser finns i [Windows PowerShell Desired State Configuration Resources](resources.md).</span><span class="sxs-lookup"><span data-stu-id="7ce86-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="7ce86-111">Skapar den sammansatta resursen</span><span class="sxs-lookup"><span data-stu-id="7ce86-111">Creating the composite resource</span></span>

<span data-ttu-id="7ce86-112">I vårt exempel skapar vi en konfiguration som anropar ett antal befintliga resurser för att konfigurera virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="7ce86-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="7ce86-113">I stället för att ange de värden som ska anges i konfigurations blocken tar konfigurationen ett antal parametrar som sedan används i konfigurations blocken.</span><span class="sxs-lookup"><span data-stu-id="7ce86-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="7ce86-114">Spara konfigurationen som en sammansatt resurs</span><span class="sxs-lookup"><span data-stu-id="7ce86-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="7ce86-115">Om du vill använda den parameterstyrda konfigurationen som en DSC-resurs, sparar du den i en katalog struktur som andra MOF-baserade resurser och namnger den med fil namns tillägget **. schema. psm1** .</span><span class="sxs-lookup"><span data-stu-id="7ce86-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="7ce86-116">I det här exemplet ska vi ge filen namnet **xVirtualMachine. schema. psm1**.</span><span class="sxs-lookup"><span data-stu-id="7ce86-116">For this example, we'll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="7ce86-117">Du måste också skapa ett manifest med namnet **xVirtualMachine. psd1** som innehåller följande rad.</span><span class="sxs-lookup"><span data-stu-id="7ce86-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="7ce86-118">Observera att detta är utöver **MyDscResources. psd1**-modulen manifest för alla resurser under mappen **MyDscResources** .</span><span class="sxs-lookup"><span data-stu-id="7ce86-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="7ce86-119">När du är färdig bör mappstrukturen vara följande:</span><span class="sxs-lookup"><span data-stu-id="7ce86-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="7ce86-120">Resursen kan nu upptäckas med hjälp av cmdleten Get-Dscresource Keyword Supports och dess egenskaper kan identifieras av antingen cmdleten eller genom att använda **CTRL + blank steg** komplettera i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7ce86-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="7ce86-121">Använda den sammansatta resursen</span><span class="sxs-lookup"><span data-stu-id="7ce86-121">Using the composite resource</span></span>

<span data-ttu-id="7ce86-122">Nu ska vi skapa en konfiguration som anropar den sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="7ce86-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="7ce86-123">Den här konfigurationen anropar den sammansatta xVirtualMachine-resursen för att skapa en virtuell dator och anropar sedan **xComputer** -resursen för att byta namn på den.</span><span class="sxs-lookup"><span data-stu-id="7ce86-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

<span data-ttu-id="7ce86-124">Du kan också använda den här resursen för att skapa flera virtuella datorer genom att skicka en matris med namn på virtuella datorer till xVirtualMachine-resursen.</span><span class="sxs-lookup"><span data-stu-id="7ce86-124">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="7ce86-125">Stöd för PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7ce86-125">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="7ce86-126">**PsDscRunAsCredential** stöds i PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7ce86-126">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="7ce86-127">Du kan använda egenskapen **PsDscRunAsCredential** i resurs blocket [DSC-konfigurationer](../configurations/configurations.md) för att ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7ce86-127">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="7ce86-128">Mer information finns i [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7ce86-128">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="7ce86-129">Om du vill komma åt användar kontexten inifrån en anpassad resurs kan du använda den automatiska variabeln `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="7ce86-129">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="7ce86-130">Till exempel kan följande kod skriva användar kontexten som resursen körs till i utförlig utdataström:</span><span class="sxs-lookup"><span data-stu-id="7ce86-130">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="7ce86-131">Se även</span><span class="sxs-lookup"><span data-stu-id="7ce86-131">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="7ce86-132">Begrepp</span><span class="sxs-lookup"><span data-stu-id="7ce86-132">Concepts</span></span>
* [<span data-ttu-id="7ce86-133">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="7ce86-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="7ce86-134">Kom igång med önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ce86-134">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
