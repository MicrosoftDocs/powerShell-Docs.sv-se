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
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="562c0-103">Sammansatta resurser: Använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="562c0-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="562c0-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="562c0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="562c0-105">I verkliga situationer, kan konfigurationer bli långa och komplexa, anropa många olika resurser och anger ett stort antal egenskaper.</span><span class="sxs-lookup"><span data-stu-id="562c0-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="562c0-106">För att åtgärda det här enklare, kan du använda en konfiguration för Windows PowerShell Desired State Configuration (DSC) som en resurs för andra konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="562c0-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="562c0-107">Vi kallar detta en sammansatt resurs.</span><span class="sxs-lookup"><span data-stu-id="562c0-107">We call this a composite resource.</span></span> <span data-ttu-id="562c0-108">En sammansatt resurs är en DSC-konfiguration som tar parametrar.</span><span class="sxs-lookup"><span data-stu-id="562c0-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="562c0-109">Parametrarna för konfigurationen fungerar som egenskaper för resursen.</span><span class="sxs-lookup"><span data-stu-id="562c0-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="562c0-110">Konfigurationen sparas som en fil med en **. schema.psm1** tillägget och tar för både MOF-schema- och resursen skript i en typisk DSC-resurs (Mer information om DSC-resurser finns i [Windows PowerShell Desired State Configuration resurser](resources.md).</span><span class="sxs-lookup"><span data-stu-id="562c0-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="562c0-111">Skapa en sammansatt resurs</span><span class="sxs-lookup"><span data-stu-id="562c0-111">Creating the composite resource</span></span>

<span data-ttu-id="562c0-112">I vårt exempel skapar vi en konfiguration som anropar ett antal befintliga resurser för att konfigurera virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="562c0-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="562c0-113">I stället för att ange värden anges i block om konfigurationen, tar konfigurationen ett antal parametrar som sedan används i configuration-block.</span><span class="sxs-lookup"><span data-stu-id="562c0-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="562c0-114">Spara konfigurationen som en sammansatt resurs</span><span class="sxs-lookup"><span data-stu-id="562c0-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="562c0-115">Om du vill använda parametriserade konfigurationen som en DSC-resurs, spara den i en katalogstruktur som som någon annan MOF-baserad resurs och namnge den med en **. schema.psm1** tillägget.</span><span class="sxs-lookup"><span data-stu-id="562c0-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="562c0-116">I det här exemplet ska vi namnge filen **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="562c0-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="562c0-117">Du måste också skapa ett manifest med namnet **xVirtualMachine.psd1** som innehåller följande rad.</span><span class="sxs-lookup"><span data-stu-id="562c0-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="562c0-118">Observera att detta förutom **MyDscResources.psd1**, modulmanifestet för alla resurser under den **MyDscResources** mapp.</span><span class="sxs-lookup"><span data-stu-id="562c0-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="562c0-119">När du är klar ska mappstrukturen på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="562c0-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="562c0-120">Resursen är nu identifierbart med hjälp av cmdleten Get-DscResource och dess egenskaper kan upptäckas genom att antingen cmdleten eller **Ctrl + blanksteg** Komplettera automatiskt i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="562c0-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="562c0-121">Med hjälp av sammansatt resurs</span><span class="sxs-lookup"><span data-stu-id="562c0-121">Using the composite resource</span></span>

<span data-ttu-id="562c0-122">Därefter skapar vi en konfiguration som anropar den sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="562c0-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="562c0-123">Den här konfigurationen anropar xVirtualMachine sammansatta resursen om du vill skapa en virtuell dator och anropar sedan den **xComputer** resurs att byta namn på den.</span><span class="sxs-lookup"><span data-stu-id="562c0-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="562c0-124">Stöd för PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="562c0-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="562c0-125">**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="562c0-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="562c0-126">Den **PsDscRunAsCredential** egenskapen kan användas i [DSC-konfigurationer](../configurations/configurations.md) resource förhindra om du vill ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="562c0-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="562c0-127">Mer information finns i [kör DSC med autentiseringsuppgifterna för användaren](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="562c0-127">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="562c0-128">Du kan använda automatiska variabeln för att komma åt användarkontext från inom en anpassad resurs `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="562c0-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="562c0-129">Följande kod skulle till exempel skriva användarkontext där resursen körs till en dataström med utförliga utdata:</span><span class="sxs-lookup"><span data-stu-id="562c0-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="562c0-130">Se även</span><span class="sxs-lookup"><span data-stu-id="562c0-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="562c0-131">Begrepp</span><span class="sxs-lookup"><span data-stu-id="562c0-131">Concepts</span></span>
* [<span data-ttu-id="562c0-132">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="562c0-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="562c0-133">Kom igång med Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="562c0-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)