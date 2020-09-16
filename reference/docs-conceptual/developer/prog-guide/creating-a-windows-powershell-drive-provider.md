---
title: Skapa en provider för Windows PowerShell-enheter | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.openlocfilehash: 2a2178714ed548986fe1a1a4de8828e8e0a938cb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787197"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="512f0-102">Skapa en Windows PowerShell-enhetsprovider</span><span class="sxs-lookup"><span data-stu-id="512f0-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="512f0-103">I det här avsnittet beskrivs hur du skapar en Windows PowerShell-provider som ger ett sätt att komma åt ett data lager via en Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="512f0-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="512f0-104">Den här typen av Provider kallas även för Windows PowerShell-tjänstleverantörer.</span><span class="sxs-lookup"><span data-stu-id="512f0-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="512f0-105">De Windows PowerShell-enheter som används av providern ger möjlighet att ansluta till data lagret.</span><span class="sxs-lookup"><span data-stu-id="512f0-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="512f0-106">Leverantören av Windows PowerShell-enheten som beskrivs här ger åtkomst till en Microsoft Access-databas.</span><span class="sxs-lookup"><span data-stu-id="512f0-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span>
<span data-ttu-id="512f0-107">För den här providern representerar Windows PowerShell-enheten databasen (det går att lägga till valfritt antal enheter i en enhets leverantör), behållare på den översta nivån på enheten representerar tabellerna i databasen och objekten i behållarna representerar raderna i tabellerna.</span><span class="sxs-lookup"><span data-stu-id="512f0-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="512f0-108">Definiera klassen Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="512f0-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="512f0-109">Leverantören av enheten måste definiera en .NET-klass som är härledd från Bask Lassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="512f0-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="512f0-110">Här är klass definitionen för den här enhets leverantören:</span><span class="sxs-lookup"><span data-stu-id="512f0-110">Here is the class definition for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="29-30":::

<span data-ttu-id="512f0-111">Observera att i det här exemplet anger attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) ett användarvänligt namn för providern och de Windows PowerShell-funktioner som providern exponerar för Windows PowerShell-körningsmiljön under kommando bearbetning.</span><span class="sxs-lookup"><span data-stu-id="512f0-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span>
<span data-ttu-id="512f0-112">Möjliga värden för providerns funktioner definieras av [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="512f0-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="512f0-113">Den här enhets leverantören stöder inte någon av dessa funktioner.</span><span class="sxs-lookup"><span data-stu-id="512f0-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="512f0-114">Definiera grundläggande funktioner</span><span class="sxs-lookup"><span data-stu-id="512f0-114">Defining Base Functionality</span></span>

<span data-ttu-id="512f0-115">Som det beskrivs i [utforma Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)härleds klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) från Bask Lassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) som definierar de metoder som behövs för att initiera och avinitiera providern.</span><span class="sxs-lookup"><span data-stu-id="512f0-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="512f0-116">Om du vill implementera funktioner för att lägga till datorspecifik initierings information och släppa resurser som används av providern, se [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="512f0-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="512f0-117">De flesta leverantörer (inklusive providern som beskrivs här) kan dock använda standard implementeringen av den här funktionen som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="512f0-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="512f0-118">Skapar information om enhets tillstånd</span><span class="sxs-lookup"><span data-stu-id="512f0-118">Creating Drive State Information</span></span>

<span data-ttu-id="512f0-119">Alla Windows PowerShell-leverantörer betraktas som tillstånds lösa, vilket innebär att din enhets leverantör måste skapa all statusinformation som krävs av Windows PowerShell-körningsmiljön när den anropar din Provider.</span><span class="sxs-lookup"><span data-stu-id="512f0-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="512f0-120">I den här enhets leverantören inkluderar tillståndsinformation anslutningen till databasen som behålls som en del av enhets informationen.</span><span class="sxs-lookup"><span data-stu-id="512f0-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="512f0-121">Här är koden som visar hur informationen lagras i det [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -objekt som beskriver enheten:</span><span class="sxs-lookup"><span data-stu-id="512f0-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="130-151":::

## <a name="creating-a-drive"></a><span data-ttu-id="512f0-122">Skapa en enhet</span><span class="sxs-lookup"><span data-stu-id="512f0-122">Creating a Drive</span></span>

<span data-ttu-id="512f0-123">För att Windows PowerShell-körningsmiljön ska kunna skapa en enhet måste providern implementera metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) .</span><span class="sxs-lookup"><span data-stu-id="512f0-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="512f0-124">Följande kod visar implementeringen av metoden [system. Management. Automation. Provider. Drivecmdletprovider. NewDrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) för den här enhets leverantören:</span><span class="sxs-lookup"><span data-stu-id="512f0-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="42-84":::

<span data-ttu-id="512f0-125">Din åsidosättning av den här metoden bör göra följande:</span><span class="sxs-lookup"><span data-stu-id="512f0-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="512f0-126">Verifiera att [System.Management.Automation.PSDriveinfo. Rot \*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) medlem finns och att det går att upprätta en anslutning till data lagret.</span><span class="sxs-lookup"><span data-stu-id="512f0-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>
- <span data-ttu-id="512f0-127">Skapa en enhet och fyll i anslutnings medlemmen i stöd för `New-PSDrive` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="512f0-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>
- <span data-ttu-id="512f0-128">Verifiera [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -objektet för den föreslagna enheten.</span><span class="sxs-lookup"><span data-stu-id="512f0-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>
- <span data-ttu-id="512f0-129">Ändra [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -objektet som beskriver enheten med nödvändig prestanda-eller Tillförlitlighets information, eller ange extra data för anropare som använder enheten.</span><span class="sxs-lookup"><span data-stu-id="512f0-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>
- <span data-ttu-id="512f0-130">Hantera felen med metoden [system. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) och returnera sedan `null` .</span><span class="sxs-lookup"><span data-stu-id="512f0-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="512f0-131">Den här metoden returnerar antingen enhets informationen som skickades till metoden eller en leverantörsspecifik version av den.</span><span class="sxs-lookup"><span data-stu-id="512f0-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="512f0-132">Koppla dynamiska parametrar till NewDrive</span><span class="sxs-lookup"><span data-stu-id="512f0-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="512f0-133">Den `New-PSDrive` cmdlet som stöds av din enhets leverantör kan behöva ytterligare parametrar.</span><span class="sxs-lookup"><span data-stu-id="512f0-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="512f0-134">För att koppla dessa dynamiska parametrar till-cmdleten implementerar providern metoden [system. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="512f0-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="512f0-135">Den här metoden returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt.</span><span class="sxs-lookup"><span data-stu-id="512f0-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="512f0-136">Den här enhets leverantören åsidosätter inte den här metoden.</span><span class="sxs-lookup"><span data-stu-id="512f0-136">This drive provider does not override this method.</span></span> <span data-ttu-id="512f0-137">Följande kod visar dock standard implementeringen av den här metoden:</span><span class="sxs-lookup"><span data-stu-id="512f0-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="512f0-138">Ta bort en enhet</span><span class="sxs-lookup"><span data-stu-id="512f0-138">Removing a Drive</span></span>

<span data-ttu-id="512f0-139">För att stänga databas anslutningen måste enhets leverantören implementera metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .</span><span class="sxs-lookup"><span data-stu-id="512f0-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="512f0-140">Den här metoden stänger anslutningen till enheten när all leverantörsspecifik information har rensats.</span><span class="sxs-lookup"><span data-stu-id="512f0-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="512f0-141">Följande kod visar implementeringen av metoden [system. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) för den här enhets leverantören:</span><span class="sxs-lookup"><span data-stu-id="512f0-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="91-116":::

<span data-ttu-id="512f0-142">Om enheten kan tas bort ska metoden returnera den information som skickas till metoden via `drive` parametern.</span><span class="sxs-lookup"><span data-stu-id="512f0-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="512f0-143">Om enheten inte kan tas bort ska metoden skriva ett undantag och sedan returnera `null` .</span><span class="sxs-lookup"><span data-stu-id="512f0-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="512f0-144">Om din Provider inte åsidosätter den här metoden returnerar standard implementeringen av den här metoden bara enhets informationen som skickas som indata.</span><span class="sxs-lookup"><span data-stu-id="512f0-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="512f0-145">Initierar standard enheter</span><span class="sxs-lookup"><span data-stu-id="512f0-145">Initializing Default Drives</span></span>

<span data-ttu-id="512f0-146">Din enhets leverantör implementerar [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) -metoden för att montera enheter.</span><span class="sxs-lookup"><span data-stu-id="512f0-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="512f0-147">Active Directory leverantören kan till exempel montera en enhet för standard namngivnings kontexten om datorn är ansluten till en domän.</span><span class="sxs-lookup"><span data-stu-id="512f0-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="512f0-148">Den här metoden returnerar en samling enhets information om de initierade enheterna eller en tom samling.</span><span class="sxs-lookup"><span data-stu-id="512f0-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="512f0-149">Anropet till den här metoden görs efter att Windows PowerShell-körningen anropar metoden [system. Management. Automation. Provider. Cmdletprovider. start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) för att initiera providern.</span><span class="sxs-lookup"><span data-stu-id="512f0-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="512f0-150">Den här enhets leverantören åsidosätter inte metoden [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) .</span><span class="sxs-lookup"><span data-stu-id="512f0-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="512f0-151">Följande kod visar dock standard implementeringen, som returnerar en tom enhets samling:</span><span class="sxs-lookup"><span data-stu-id="512f0-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="512f0-152">Saker att komma ihåg om att implementera InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="512f0-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="512f0-153">Alla enhets leverantörer ska montera en rot enhet som hjälper användaren att identifiera sig.</span><span class="sxs-lookup"><span data-stu-id="512f0-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="512f0-154">Rot enheten kan ange platser som fungerar som rötter för andra monterade enheter.</span><span class="sxs-lookup"><span data-stu-id="512f0-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="512f0-155">Active Directory leverantören kan till exempel skapa en enhet som visar namngivnings kontexterna som finns i `namingContext` attributen för root Distributed system Environment (DSE).</span><span class="sxs-lookup"><span data-stu-id="512f0-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="512f0-156">Detta hjälper användarna att identifiera monterings punkter för andra enheter.</span><span class="sxs-lookup"><span data-stu-id="512f0-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="512f0-157">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="512f0-157">Code Sample</span></span>

<span data-ttu-id="512f0-158">Fullständig exempel kod finns i [kod exemplet för AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="512f0-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="512f0-159">Testa providern för Windows PowerShell-enheter</span><span class="sxs-lookup"><span data-stu-id="512f0-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="512f0-160">När din Windows PowerShell-provider har registrerats med Windows PowerShell kan du testa den genom att köra cmdlets som stöds på kommando raden, inklusive alla cmdletar som gjorts tillgängliga av härledning.</span><span class="sxs-lookup"><span data-stu-id="512f0-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="512f0-161">Nu ska vi testa leverantören av exempel enheten.</span><span class="sxs-lookup"><span data-stu-id="512f0-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="512f0-162">Kör `Get-PSProvider` cmdleten för att hämta listan över providrar för att säkerställa att AccessDB-providern finns:</span><span class="sxs-lookup"><span data-stu-id="512f0-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="512f0-163">**PS-> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="512f0-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="512f0-164">Följande utdata visas:</span><span class="sxs-lookup"><span data-stu-id="512f0-164">The following output appears:</span></span>

   ```Output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="512f0-165">Se till att det finns ett databas server namn (DSN) för databasen genom att komma åt **data källorna** i **administrations verktyg** för operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="512f0-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="512f0-166">I tabellen **användar-DSN** dubbelklickar du på **MS Access-databas** och lägger till sökvägen till enheten `C:\ps\northwind.mdb` .</span><span class="sxs-lookup"><span data-stu-id="512f0-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path `C:\ps\northwind.mdb`.</span></span>

3. <span data-ttu-id="512f0-167">Skapa en ny enhet med hjälp av exempel enhets leverantören:</span><span class="sxs-lookup"><span data-stu-id="512f0-167">Create a new drive using the sample drive provider:</span></span>

   ```powershell
   new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb`
   ```

   <span data-ttu-id="512f0-168">Följande utdata visas:</span><span class="sxs-lookup"><span data-stu-id="512f0-168">The following output appears:</span></span>

   ```Output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="512f0-169">Verifiera anslutningen.</span><span class="sxs-lookup"><span data-stu-id="512f0-169">Validate the connection.</span></span> <span data-ttu-id="512f0-170">Eftersom anslutningen definieras som medlem i enheten kan du kontrol lera den med hjälp av cmdleten Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="512f0-170">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="512f0-171">Användaren kan ännu inte interagera med providern som en enhet eftersom providern behöver container funktioner för interaktionen.</span><span class="sxs-lookup"><span data-stu-id="512f0-171">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="512f0-172">Mer information finns i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="512f0-172">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="512f0-173">**PS> (Get-PSDrive mindb). anslutning**</span><span class="sxs-lookup"><span data-stu-id="512f0-173">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="512f0-174">Följande utdata visas:</span><span class="sxs-lookup"><span data-stu-id="512f0-174">The following output appears:</span></span>

   ```Output
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

5. <span data-ttu-id="512f0-175">Ta bort enheten och avsluta gränssnittet:</span><span class="sxs-lookup"><span data-stu-id="512f0-175">Remove the drive and exit the shell:</span></span>

   ```powershell
   PS> remove-psdrive mydb
   PS> exit
   ```

## <a name="see-also"></a><span data-ttu-id="512f0-176">Se även</span><span class="sxs-lookup"><span data-stu-id="512f0-176">See Also</span></span>

[<span data-ttu-id="512f0-177">Skapa Windows PowerShell-leverantörer</span><span class="sxs-lookup"><span data-stu-id="512f0-177">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="512f0-178">Utforma din Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="512f0-178">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="512f0-179">Skapa en grundläggande Windows PowerShell-provider</span><span class="sxs-lookup"><span data-stu-id="512f0-179">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)
