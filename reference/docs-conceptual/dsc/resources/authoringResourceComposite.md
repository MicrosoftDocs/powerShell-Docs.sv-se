---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Sammansatta resurser – använda en DSC-konfiguration som en resurs
ms.openlocfilehash: 79fe94bd5bab8fa460714e5994d2e2487f302410
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75415893"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="a52af-103">Sammansatta resurser: använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="a52af-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="a52af-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="a52af-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a52af-105">I verkliga situationer kan konfigurationer bli långa och komplexa, anropa många olika resurser och ange ett stort antal egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a52af-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="a52af-106">För att hjälpa dig att hantera den här komplexiteten kan du använda en Windows PowerShell-konfiguration för Desired State Configuration (DSC) som resurs för andra konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="a52af-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="a52af-107">Detta kallas för en sammansatt resurs.</span><span class="sxs-lookup"><span data-stu-id="a52af-107">This is called a composite resource.</span></span> <span data-ttu-id="a52af-108">En sammansatt resurs är en DSC-konfiguration som tar parametrar.</span><span class="sxs-lookup"><span data-stu-id="a52af-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="a52af-109">Konfigurationens parametrar fungerar som egenskaper för resursen.</span><span class="sxs-lookup"><span data-stu-id="a52af-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="a52af-110">Konfigurationen sparas som en fil med ett `.schema.psm1` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="a52af-110">The configuration is saved as a file with a `.schema.psm1` extension.</span></span> <span data-ttu-id="a52af-111">Det tar både MOF-schemat och resurs skriptet i en typisk DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="a52af-111">It takes the place of both the MOF schema, and the resource script in a typical DSC resource.</span></span> <span data-ttu-id="a52af-112">Mer information om DSC-resurser finns i [Windows PowerShell Desired State Configuration-resurser](resources.md).</span><span class="sxs-lookup"><span data-stu-id="a52af-112">For more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="a52af-113">Skapar den sammansatta resursen</span><span class="sxs-lookup"><span data-stu-id="a52af-113">Creating the composite resource</span></span>

<span data-ttu-id="a52af-114">I vårt exempel skapar vi en konfiguration som anropar ett antal befintliga resurser för att konfigurera virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="a52af-114">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="a52af-115">I stället för att ange de värden som ska anges i konfigurations blocken tar konfigurationen i parametrar som sedan används i konfigurations blocken.</span><span class="sxs-lookup"><span data-stu-id="a52af-115">Instead of specifying the values to be set in configuration blocks, the configuration takes in parameters that are then used in the configuration blocks.</span></span>

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

> [!NOTE]
> <span data-ttu-id="a52af-116">DSC har för närvarande inte stöd för att placera sammansatta resurser eller kapslade konfigurationer i en sammansatt resurs.</span><span class="sxs-lookup"><span data-stu-id="a52af-116">DSC doesn't currently support placing composite resources or nested configurations within a composite resource.</span></span>

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="a52af-117">Spara konfigurationen som en sammansatt resurs</span><span class="sxs-lookup"><span data-stu-id="a52af-117">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="a52af-118">Om du vill använda den parameterstyrda konfigurationen som en DSC-resurs, sparar du den i en katalog struktur som andra MOF-baserade resurser och namnger den med ett `.schema.psm1` tillägg.</span><span class="sxs-lookup"><span data-stu-id="a52af-118">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a `.schema.psm1` extension.</span></span> <span data-ttu-id="a52af-119">I det här exemplet ska vi ge filen `xVirtualMachine.schema.psm1`ett namn.</span><span class="sxs-lookup"><span data-stu-id="a52af-119">For this example, we'll name the file `xVirtualMachine.schema.psm1`.</span></span> <span data-ttu-id="a52af-120">Du måste också skapa ett manifest med namnet `xVirtualMachine.psd1` som innehåller följande rad.</span><span class="sxs-lookup"><span data-stu-id="a52af-120">You also need to create a manifest named `xVirtualMachine.psd1` that contains the following line.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> <span data-ttu-id="a52af-121">Detta är förutom `MyDscResources.psd1`modulen manifest för alla resurser i `MyDscResources` mappen.</span><span class="sxs-lookup"><span data-stu-id="a52af-121">This is in addition to `MyDscResources.psd1`, the module manifest for all resources under the `MyDscResources` folder.</span></span>

<span data-ttu-id="a52af-122">När du är färdig bör mappstrukturen vara följande:</span><span class="sxs-lookup"><span data-stu-id="a52af-122">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="a52af-123">Resursen kan nu upptäckas med `Get-DscResource` hjälp av cmdleten och dess egenskaper kan upptäckas av antingen cmdleten eller genom att använda funktionen för automatisk komplettering av <kbd>CTRL</kbd>+-<kbd>utrymme</kbd> i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a52af-123">The resource is now discoverable by using the `Get-DscResource` cmdlet, and its properties are discoverable by either that cmdlet or by using <kbd>Ctrl</kbd>+<kbd>Space</kbd> autocomplete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="a52af-124">Använda den sammansatta resursen</span><span class="sxs-lookup"><span data-stu-id="a52af-124">Using the composite resource</span></span>

<span data-ttu-id="a52af-125">Nu ska vi skapa en konfiguration som anropar den sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="a52af-125">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="a52af-126">Den här konfigurationen anropar den sammansatta xVirtualMachine-resursen för att skapa en virtuell dator och anropar sedan **xComputer** -resursen för att byta namn på den.</span><span class="sxs-lookup"><span data-stu-id="a52af-126">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

<span data-ttu-id="a52af-127">Du kan också använda den här resursen för att skapa flera virtuella datorer genom att skicka en matris med namn på virtuella datorer till xVirtualMachine-resursen.</span><span class="sxs-lookup"><span data-stu-id="a52af-127">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="a52af-128">Stöd för PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a52af-128">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="a52af-129">**PsDscRunAsCredential** stöds i PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="a52af-129">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="a52af-130">Du kan använda egenskapen **PsDscRunAsCredential** i resurs blocket [DSC-konfigurationer](../configurations/configurations.md) för att ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a52af-130">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="a52af-131">Mer information finns i [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a52af-131">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="a52af-132">Om du vill komma åt användar kontexten inifrån en anpassad resurs kan du använda den `$PsDscContext`automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="a52af-132">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="a52af-133">Följande kod skulle till exempel skriva användar kontexten som resursen körs till i utförlig utdataström:</span><span class="sxs-lookup"><span data-stu-id="a52af-133">For example, the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="a52af-134">Se även</span><span class="sxs-lookup"><span data-stu-id="a52af-134">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="a52af-135">Begrepp</span><span class="sxs-lookup"><span data-stu-id="a52af-135">Concepts</span></span>

- [<span data-ttu-id="a52af-136">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="a52af-136">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="a52af-137">Kom igång med önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a52af-137">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
