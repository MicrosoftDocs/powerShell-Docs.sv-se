---
title: Skapa en Provider för Windows PowerShell-enhet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 2696d78cae7739310b7684161b597ce436dabe92
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855209"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="1017d-102">Skapa en Windows PowerShell-enhetsprovider</span><span class="sxs-lookup"><span data-stu-id="1017d-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="1017d-103">Det här avsnittet beskriver hur du skapar en provider för Windows PowerShell-enhet som är ett sätt att komma åt ett datalager genom en Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="1017d-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="1017d-104">Den här typen av providern kallas också Windows PowerShell-enhet providers.</span><span class="sxs-lookup"><span data-stu-id="1017d-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="1017d-105">Windows PowerShell-enheter som används av providern ger metoder för att ansluta till datalagret.</span><span class="sxs-lookup"><span data-stu-id="1017d-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="1017d-106">Windows PowerShell-enhet-providern som beskrivs här ger åtkomst till en Microsoft Access-databas.</span><span class="sxs-lookup"><span data-stu-id="1017d-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="1017d-107">För den här providern Windows PowerShell-enhet är databasen (det är möjligt att lägga till valfritt antal enheter till en leverantör av enhet), de översta behållarna rotmapp representerar tabeller i databasen och objekten i behållarna representerar raderna i tabeller.</span><span class="sxs-lookup"><span data-stu-id="1017d-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="1017d-108">Definiera klassen Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="1017d-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="1017d-109">Din enhet-provider måste definiera en .NET-klass som härleds från den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basklassen.</span><span class="sxs-lookup"><span data-stu-id="1017d-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="1017d-110">Här är klassdefinitionen för den här enhetsprovidern:</span><span class="sxs-lookup"><span data-stu-id="1017d-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="1017d-111">Observera att i det här exemplet på [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributet anger ett användarvänligt namn för providern och de specifika funktionerna i Windows PowerShell som providern Visar Windows PowerShell-runtime under bearbetning av kommandot.</span><span class="sxs-lookup"><span data-stu-id="1017d-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="1017d-112">De möjliga värdena för funktioner för providern definieras av den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning.</span><span class="sxs-lookup"><span data-stu-id="1017d-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="1017d-113">Den här enhetsprovidern stöder inte någon av dessa funktioner.</span><span class="sxs-lookup"><span data-stu-id="1017d-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="1017d-114">Definiera grundfunktionen</span><span class="sxs-lookup"><span data-stu-id="1017d-114">Defining Base Functionality</span></span>

<span data-ttu-id="1017d-115">Mer information finns i [Design Your Windows PowerShell-providern](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klassen härleds från den [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basklassen som definierar de metoder som behövs för att initiera och Avinitierar providern.</span><span class="sxs-lookup"><span data-stu-id="1017d-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="1017d-116">Om du vill implementera funktioner för att lägga till sessionen-specifika initieringsinformation och för att frisläppa resurser som används av providern, se [skapar en grundläggande Windows PowerShell-providern](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1017d-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="1017d-117">De flesta leverantörer (inklusive providern som beskrivs här) kan dock använda standardimplementering av den här funktionen som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1017d-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="1017d-118">Skapar statusinformation för enhet</span><span class="sxs-lookup"><span data-stu-id="1017d-118">Creating Drive State Information</span></span>

<span data-ttu-id="1017d-119">Alla Windows PowerShell-leverantörer anses vara tillståndslösa, vilket innebär att din enhet-provider måste skapa all tillståndsinformation som krävs av Windows PowerShell-körningen när anropas av din provider.</span><span class="sxs-lookup"><span data-stu-id="1017d-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="1017d-120">För den här enhetsprovidern innehåller information om tillstånd anslutningen till databasen som sparas som en del av enhetsinformationen.</span><span class="sxs-lookup"><span data-stu-id="1017d-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="1017d-121">Här är kod som visar hur den här informationen lagras i den [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objekt som beskriver enheten:</span><span class="sxs-lookup"><span data-stu-id="1017d-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="1017d-122">Skapa en enhet</span><span class="sxs-lookup"><span data-stu-id="1017d-122">Creating a Drive</span></span>

<span data-ttu-id="1017d-123">För att Windows PowerShell-körning för att skapa en enhet måste enheten-leverantören måste implementera de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metod.</span><span class="sxs-lookup"><span data-stu-id="1017d-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="1017d-124">Följande kod visar implementeringen av den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metod för den här enhetsprovidern:</span><span class="sxs-lookup"><span data-stu-id="1017d-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="1017d-125">Åsidosättningen av den här metoden bör göra följande:</span><span class="sxs-lookup"><span data-stu-id="1017d-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="1017d-126">Kontrollera att den [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) medlem finns och att en anslutning till datalagret kan göras.</span><span class="sxs-lookup"><span data-stu-id="1017d-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="1017d-127">Skapa en enhet och fylla i medlemmen anslutning stöd i `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1017d-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="1017d-128">Verifiera den [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objekt för den föreslagna enheten.</span><span class="sxs-lookup"><span data-stu-id="1017d-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="1017d-129">Ändra den [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objekt som beskriver enheten som har nödvändiga prestanda eller tillförlitlighetsinformation eller extra data för anropare som använder enheten.</span><span class="sxs-lookup"><span data-stu-id="1017d-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="1017d-130">Hantera fel med den [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metoden och sedan återgå `null`.</span><span class="sxs-lookup"><span data-stu-id="1017d-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="1017d-131">Den här metoden returnerar antingen enhetsinformationen som skickades till metoden eller en provider-specifik version av den.</span><span class="sxs-lookup"><span data-stu-id="1017d-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="1017d-132">Bifoga dynamiska parametrar till NewDrive</span><span class="sxs-lookup"><span data-stu-id="1017d-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="1017d-133">Den `New-PSDrive` cmdlet som stöds av din enhetsprovidern kan kräva ytterligare parametrar.</span><span class="sxs-lookup"><span data-stu-id="1017d-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="1017d-134">Om du vill koppla dessa dynamiska parametrar till cmdleten providern implementerar den [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metod.</span><span class="sxs-lookup"><span data-stu-id="1017d-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="1017d-135">Den här metoden returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt.</span><span class="sxs-lookup"><span data-stu-id="1017d-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="1017d-136">Den här enhetsprovidern åsidosätts inte den här metoden.</span><span class="sxs-lookup"><span data-stu-id="1017d-136">This drive provider does not override this method.</span></span> <span data-ttu-id="1017d-137">Följande kod visar dock standardimplementering av den här metoden:</span><span class="sxs-lookup"><span data-stu-id="1017d-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="1017d-138">Ta bort en enhet</span><span class="sxs-lookup"><span data-stu-id="1017d-138">Removing a Drive</span></span>

<span data-ttu-id="1017d-139">Om du vill stänga anslutningen till databasen, enhetsprovidern måste implementera de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metod.</span><span class="sxs-lookup"><span data-stu-id="1017d-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="1017d-140">Den här metoden stängs anslutningen till enheten när du rensar provider-specifik information.</span><span class="sxs-lookup"><span data-stu-id="1017d-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="1017d-141">Följande kod visar implementeringen av den [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metod för den här enhetsprovidern:</span><span class="sxs-lookup"><span data-stu-id="1017d-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="1017d-142">Om enheten kan tas bort, ska metoden returnera information som skickas till metoden via den `drive` parametern.</span><span class="sxs-lookup"><span data-stu-id="1017d-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="1017d-143">Om enheten inte kan tas bort, metoden ska skriva ett undantag och returnerar sedan `null`.</span><span class="sxs-lookup"><span data-stu-id="1017d-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="1017d-144">Om din leverantör inte åsidosätter den här metoden returnerar standardimplementering av den här metoden bara enhetsinformationen angavs som indata.</span><span class="sxs-lookup"><span data-stu-id="1017d-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="1017d-145">Initiering av standard-enheter</span><span class="sxs-lookup"><span data-stu-id="1017d-145">Initializing Default Drives</span></span>

<span data-ttu-id="1017d-146">Din enhet providern implementerar den [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metoden att montera enheter.</span><span class="sxs-lookup"><span data-stu-id="1017d-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="1017d-147">Providern för Active Directory kan till exempel montera en enhet för standardnamngivningskontext om datorn är ansluten till en domän.</span><span class="sxs-lookup"><span data-stu-id="1017d-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="1017d-148">Den här metoden returnerar en samling med enhetsinformationen om initierad enheter eller en tom samling.</span><span class="sxs-lookup"><span data-stu-id="1017d-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="1017d-149">Anrop till den här metoden görs efter anrop för Windows PowerShell-runtime den [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metod för att initiera providern.</span><span class="sxs-lookup"><span data-stu-id="1017d-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="1017d-150">Den här enhetsprovidern åsidosätts inte den [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metod.</span><span class="sxs-lookup"><span data-stu-id="1017d-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="1017d-151">Följande kod visar dock standardimplementering som returnerar en tom enhet samling:</span><span class="sxs-lookup"><span data-stu-id="1017d-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="1017d-152">Kom ihåg följande om hur du implementerar InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="1017d-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="1017d-153">Alla leverantörer av enheten ska ansluta ett rotenhet som hjälper användaren med identifieringsmöjlighet.</span><span class="sxs-lookup"><span data-stu-id="1017d-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="1017d-154">Rotenheten kan en lista över platser som fungerar som rötter för andra monterade enheter.</span><span class="sxs-lookup"><span data-stu-id="1017d-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="1017d-155">Providern för Active Directory kan till exempel skapa en enhet som visar en lista över namngivningskontexterna som finns i den `namingContext` attribut rot distribuerade systemmiljö (DSE).</span><span class="sxs-lookup"><span data-stu-id="1017d-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="1017d-156">Detta hjälper användare att identifiera monteringspunkter för andra enheter.</span><span class="sxs-lookup"><span data-stu-id="1017d-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1017d-157">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="1017d-157">Code Sample</span></span>

<span data-ttu-id="1017d-158">Komplett exempel finns i [AccessDbProviderSample02 kodexempel](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1017d-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="1017d-159">Testa Provider för Windows PowerShell-enhet</span><span class="sxs-lookup"><span data-stu-id="1017d-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="1017d-160">När din Windows PowerShell-provider har registrerats med Windows PowerShell kan testa du den genom att köra cmdletarna stöds på kommandoraden, inklusive alla cmdletar som gjorts tillgängliga av härledning.</span><span class="sxs-lookup"><span data-stu-id="1017d-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="1017d-161">Nu ska vi testa enhetsprovidern exemplet.</span><span class="sxs-lookup"><span data-stu-id="1017d-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="1017d-162">Kör den `Get-PSProvider` cmdlet för att hämta listan med providers för att säkerställa att enhetsprovidern AccessDB finns:</span><span class="sxs-lookup"><span data-stu-id="1017d-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="1017d-163">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="1017d-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="1017d-164">Följande utdata visas:</span><span class="sxs-lookup"><span data-stu-id="1017d-164">The following output appears:</span></span>

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="1017d-165">Kontrollera att Databasservernamnet (DSN) finns för databasen genom att öppna den **datakällor** delen av den **Administrationsverktyg** för operativsystemet.</span><span class="sxs-lookup"><span data-stu-id="1017d-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="1017d-166">I den **användar-DSN** tabellen genom att dubbelklicka på **MS Access-databas** och Lägg till enhetssökväg C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="1017d-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="1017d-167">Skapa en ny enhet med hjälp av exemplet enhetsprovidern:</span><span class="sxs-lookup"><span data-stu-id="1017d-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="1017d-168">**PS > Ny psdrive-namnet mindb-rot c:\ps\northwind.mdb - psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="1017d-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="1017d-169">Följande utdata visas:</span><span class="sxs-lookup"><span data-stu-id="1017d-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="1017d-170">Verifiera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="1017d-170">Validate the connection.</span></span> <span data-ttu-id="1017d-171">Eftersom anslutningen har definierats som en medlem i enheten kan kontrollera du den med hjälp av cmdleten Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="1017d-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1017d-172">Användaren kan inte ännu interagera med leverantören som en enhet som providern måste behållare funktioner för den interaktionen.</span><span class="sxs-lookup"><span data-stu-id="1017d-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="1017d-173">Mer information finns i [skapar en Windows PowerShell-providern för behållaren](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1017d-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="1017d-174">**PS > (get-psdrive mindb) .connection**</span><span class="sxs-lookup"><span data-stu-id="1017d-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="1017d-175">Följande utdata visas:</span><span class="sxs-lookup"><span data-stu-id="1017d-175">The following output appears:</span></span>

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. <span data-ttu-id="1017d-176">Ta bort enheten och lämna gränssnittet:</span><span class="sxs-lookup"><span data-stu-id="1017d-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="1017d-177">**PS > Ta bort psdrive mindb**</span><span class="sxs-lookup"><span data-stu-id="1017d-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="1017d-178">**PS > Avsluta**</span><span class="sxs-lookup"><span data-stu-id="1017d-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="1017d-179">Se även</span><span class="sxs-lookup"><span data-stu-id="1017d-179">See Also</span></span>

[<span data-ttu-id="1017d-180">Skapa Windows PowerShell-Providers</span><span class="sxs-lookup"><span data-stu-id="1017d-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="1017d-181">Utforma din Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="1017d-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="1017d-182">Skapa en grundläggande Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="1017d-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)