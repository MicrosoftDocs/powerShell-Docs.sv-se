---
title: Skapa en Windows PowerShell-providern för navigering | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055078"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="39266-102">Skapa en Windows PowerShell-navigeringsprovider</span><span class="sxs-lookup"><span data-stu-id="39266-102">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="39266-103">Det här avsnittet beskriver hur du skapar en provider för Windows PowerShell navigering som kan navigera till datalagret.</span><span class="sxs-lookup"><span data-stu-id="39266-103">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="39266-104">Den här typen av providern har stöd för rekursiv kommandon, kapslade behållare och relativa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="39266-104">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="39266-105">Du kan ladda ned den C# källfilen (AccessDBSampleProvider05.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter.</span><span class="sxs-lookup"><span data-stu-id="39266-105">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="39266-106">Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="39266-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="39266-107">Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.</span><span class="sxs-lookup"><span data-stu-id="39266-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="39266-108">Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="39266-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="39266-109">Providern som beskrivs här kan Användarhanteraren en Access-databas som en enhet så att användaren kan navigera till datatabeller i databasen.</span><span class="sxs-lookup"><span data-stu-id="39266-109">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="39266-110">När du skapar en egen provider för navigering, kan du implementera metoder som kan göra enhet kvalificerade sökvägar som krävs för navigering, normalisera relativa sökvägar, flytta objekt i datalagret, samt metoder som hämta underordnade namnen, hämta den överordnade sökvägen för ett objekt och testa är en behållare för att identifiera om ett objekt.</span><span class="sxs-lookup"><span data-stu-id="39266-110">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="39266-111">Tänk på att den här designen förutsätter en databas som har ett fält med namn-ID och att fältet är LongInteger.</span><span class="sxs-lookup"><span data-stu-id="39266-111">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

<span data-ttu-id="39266-112">I följande lista innehåller avsnitt i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="39266-112">The following list includes sections in this topic.</span></span> <span data-ttu-id="39266-113">Om du är bekant med att skriva en Windows PowerShell-providern för navigering, kan du läsa informationen i den ordning som det visas.</span><span class="sxs-lookup"><span data-stu-id="39266-113">If you are unfamiliar with writing a Windows PowerShell navigation provider, read this information in the order that it appears.</span></span> <span data-ttu-id="39266-114">Men om du är bekant med att skriva en Windows PowerShell-providern för navigering, gå direkt till den information du behöver.</span><span class="sxs-lookup"><span data-stu-id="39266-114">However, if you are familiar with writing a Windows PowerShell navigation provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="39266-115">Definiera en PS navigering providerklass</span><span class="sxs-lookup"><span data-stu-id="39266-115">Defining a PS Navigation Provider Class</span></span>](#Define-the-Windows-PowerShell-provider)

- [<span data-ttu-id="39266-116">Definiera grundfunktionen</span><span class="sxs-lookup"><span data-stu-id="39266-116">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="39266-117">Skapa en PS-sökväg</span><span class="sxs-lookup"><span data-stu-id="39266-117">Creating a PS Path</span></span>](#Creating-a-Windows-PowerShell-Path)

- [<span data-ttu-id="39266-118">Hämtning av den överordnade sökvägen</span><span class="sxs-lookup"><span data-stu-id="39266-118">Retrieving the Parent Path</span></span>](#Retrieving-the-Parent-Path)

- [<span data-ttu-id="39266-119">Hämtar namnet på underordnade sökväg</span><span class="sxs-lookup"><span data-stu-id="39266-119">Retrieving the Child Path Name</span></span>](#Retrieve-the-Child-Path-Name)

- [<span data-ttu-id="39266-120">Avgör om ett objekt är en behållare</span><span class="sxs-lookup"><span data-stu-id="39266-120">Determining if an Item is a Container</span></span>](#Determining-if-an-Item-is-a-Container)

- [<span data-ttu-id="39266-121">Flyttar ett objekt</span><span class="sxs-lookup"><span data-stu-id="39266-121">Moving an Item</span></span>](#Moving-an-Item)

- [<span data-ttu-id="39266-122">Koppla dynamiska parametrar till den `Move-Item` Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39266-122">Attaching Dynamic Parameters to the `Move-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [<span data-ttu-id="39266-123">Normaliserar en relativ sökväg</span><span class="sxs-lookup"><span data-stu-id="39266-123">Normalizing a Relative Path</span></span>](#Normalizing-a-Relative-Path)

- [<span data-ttu-id="39266-124">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="39266-124">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="39266-125">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="39266-125">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="39266-126">Att skapa Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="39266-126">Building the Windows PowerShell Provider</span></span>](#Building-the-Windows-PowerShell-provider)

- [<span data-ttu-id="39266-127">Testa Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="39266-127">Testing the Windows PowerShell Provider</span></span>](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="39266-128">Definiera Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="39266-128">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="39266-129">En Windows PowerShell-providern för navigering måste skapa en .NET-klass som härleds från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basklassen.</span><span class="sxs-lookup"><span data-stu-id="39266-129">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="39266-130">Här är klassdefinitionen för navigering-providern som beskrivs i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="39266-130">Here is the class definition for the navigation provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

<span data-ttu-id="39266-131">Observera att i den här providern den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut innehåller två parametrar.</span><span class="sxs-lookup"><span data-stu-id="39266-131">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="39266-132">Den första parametern anger ett användarvänligt namn för providern som används av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39266-132">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="39266-133">Den andra parametern anger de specifika funktioner i Windows PowerShell som providern visar Windows PowerShell-runtime under bearbetning av kommandot.</span><span class="sxs-lookup"><span data-stu-id="39266-133">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="39266-134">Det finns inga specifika Windows PowerShell-funktioner som har lagts till för den här providern.</span><span class="sxs-lookup"><span data-stu-id="39266-134">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="39266-135">Definiera grundfunktionen</span><span class="sxs-lookup"><span data-stu-id="39266-135">Defining Base Functionality</span></span>

<span data-ttu-id="39266-136">Mer information finns i [Design Your PS-Provider](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basklass härleds från flera klasser som angetts annan provider CRL-funktionalitet.</span><span class="sxs-lookup"><span data-stu-id="39266-136">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="39266-137">En provider för Windows PowerShell navigering, därför måste definiera alla funktioner som tillhandahålls av dessa klasser.</span><span class="sxs-lookup"><span data-stu-id="39266-137">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="39266-138">Om du vill implementera funktioner för att lägga till sessionen-specifika initieringsinformation och för att frisläppa resurser som används av providern, se [skapar en grundläggande PS-Provider](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="39266-138">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="39266-139">De flesta leverantörer (inklusive providern som beskrivs här) kan dock använda standardimplementering av den här funktionen tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39266-139">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="39266-140">För att få åtkomst till datalagret via en Windows PowerShell-enhet, måste du implementera-metoderna i den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basklassen.</span><span class="sxs-lookup"><span data-stu-id="39266-140">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="39266-141">Läs mer om hur du implementerar dessa metoder, [skapar en Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="39266-141">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="39266-142">Om du vill manipulera objekten i ett datalager, till exempel komma, inställningen och rensar objekt providern måste implementera de metoder som tillhandahålls av den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basklassen.</span><span class="sxs-lookup"><span data-stu-id="39266-142">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="39266-143">Läs mer om hur du implementerar dessa metoder, [skapa en Windows PowerShell-Provider för objektet](./creating-a-windows-powershell-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="39266-143">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="39266-144">För att komma till de underordnade objekten eller namnen i datalagret, samt metoder som kan skapa, kopiera, byta namn på och ta bort objekt, måste du implementera de metoder som tillhandahålls av den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)basklassen.</span><span class="sxs-lookup"><span data-stu-id="39266-144">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="39266-145">Läs mer om hur du implementerar dessa metoder, [skapar en Windows PowerShell-providern för behållaren](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="39266-145">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="39266-146">Skapa en Windows PowerShell-sökväg</span><span class="sxs-lookup"><span data-stu-id="39266-146">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="39266-147">Windows PowerShell-providern för navigering använda en provider-internt Windows PowerShell-sökväg för att navigera objekten i datalagret.</span><span class="sxs-lookup"><span data-stu-id="39266-147">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="39266-148">Skapa en provider-internt sökväg providern måste implementera de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) till stöder anropar från kombinera-Path-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39266-148">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="39266-149">Den här metoden kombinerar en över- och underordnade sökväg till en provider-internt sökväg, med hjälp av en provider-specifik sökvägsavdelare mellan överordnade och underordnade sökvägar.</span><span class="sxs-lookup"><span data-stu-id="39266-149">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="39266-150">Standardimplementering tar sökvägar med ”/” eller ”\\” som avgränsare för sökvägen normaliserar avgränsare för sökvägen till ”\\” kombinerar sögvägar överordnade och underordnade med avgränsare mellan dem och returnerar en sträng som innehåller den kombinerade sökvägar.</span><span class="sxs-lookup"><span data-stu-id="39266-150">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="39266-151">Den här providern för navigering implementerar inte den här metoden.</span><span class="sxs-lookup"><span data-stu-id="39266-151">This navigation provider does not implement this method.</span></span> <span data-ttu-id="39266-152">Följande kod är dock standardimplementering av den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metod.</span><span class="sxs-lookup"><span data-stu-id="39266-152">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="39266-153">Kom ihåg följande om hur du implementerar MakePath</span><span class="sxs-lookup"><span data-stu-id="39266-153">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="39266-154">Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span><span class="sxs-lookup"><span data-stu-id="39266-154">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="39266-155">Implementeringen av den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metoden bör inte verifiera sökvägen som en juridiska fullständiga sökväg i providernamnområde.</span><span class="sxs-lookup"><span data-stu-id="39266-155">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="39266-156">Tänk på att varje parameter kan bara representera en del av en sökväg och de kombinerade delarna kan inte generera en fullständig sökväg.</span><span class="sxs-lookup"><span data-stu-id="39266-156">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="39266-157">Till exempel den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metod för filsystem-providern få ”windows\system32” i den `parent` parametern och ”abc.dll” i `child` parametern.</span><span class="sxs-lookup"><span data-stu-id="39266-157">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="39266-158">Metoden kopplar ihop dessa värden med den ”\\” avgränsare och returnerar ”windows\system32\abc.dll” som inte är en fullständigt kvalificerad sökväg i filsystemet.</span><span class="sxs-lookup"><span data-stu-id="39266-158">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="39266-159">Sögvägar som angetts i anropet till [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) kan innehålla tecken tillåts inte i providernamnområde.</span><span class="sxs-lookup"><span data-stu-id="39266-159">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="39266-160">De här tecknen används mest sannolikt för jokertecken expansion och implementeringen av den här metoden bör inte ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="39266-160">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="39266-161">Hämtning av den överordnade sökvägen</span><span class="sxs-lookup"><span data-stu-id="39266-161">Retrieving the Parent Path</span></span>

<span data-ttu-id="39266-162">Windows PowerShell navigering providers implementerar den [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metod för att hämta den överordnade delen av den angivna fullständigt eller partiellt provider-specifik sökväg.</span><span class="sxs-lookup"><span data-stu-id="39266-162">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="39266-163">Metoden tar bort den underordnade delen av sökvägen och returnerar överordnat sökvägen del.</span><span class="sxs-lookup"><span data-stu-id="39266-163">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="39266-164">Den `root` parametern anger den fullständiga sökvägen till roten för en enhet.</span><span class="sxs-lookup"><span data-stu-id="39266-164">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="39266-165">Den här parametern kan vara null eller tomt om en monterad enhet inte används för åtgärd för hämtning.</span><span class="sxs-lookup"><span data-stu-id="39266-165">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="39266-166">Om en rotcertifikatutfärdare anges returnera metoden en sökväg till en behållare i samma träd som roten.</span><span class="sxs-lookup"><span data-stu-id="39266-166">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="39266-167">Exemplet navigering providern åsidosätter inte den här metoden, men använder standardimplementering.</span><span class="sxs-lookup"><span data-stu-id="39266-167">The sample navigation provider does not override this method, but uses the default implementation.</span></span> <span data-ttu-id="39266-168">Den accepterar sökvägar som använder både ”/” och ”\\” som avgränsare för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="39266-168">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="39266-169">Den första normaliserar sökvägen till endast ha ”\\” skiljetecken, delar sedan upp den överordnade sökvägen ut på sist ”\\” och returnerar den överordnade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="39266-169">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="39266-170">Du bör tänka på att implementera GetParentPath</span><span class="sxs-lookup"><span data-stu-id="39266-170">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="39266-171">Implementeringen av den [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metoden bör dela upp sökvägen lexically på sökvägsavdelare för leverantörens namnområde.</span><span class="sxs-lookup"><span data-stu-id="39266-171">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="39266-172">Till exempel filsystem-providern använder den här metoden för att söka efter senaste ”\\” och returnerar allt till vänster om avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="39266-172">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="39266-173">Hämta namnet på underordnade sökväg</span><span class="sxs-lookup"><span data-stu-id="39266-173">Retrieve the Child Path Name</span></span>

<span data-ttu-id="39266-174">Din navigering providern implementerar den [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metod för att hämta namnet (lövelement) på underordnat objektets finns på den angivna fullständiga eller ofullständig provider-specifik sökväg.</span><span class="sxs-lookup"><span data-stu-id="39266-174">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="39266-175">Exemplet navigering providern åsidosätts inte den här metoden.</span><span class="sxs-lookup"><span data-stu-id="39266-175">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="39266-176">Standardimplementering visas nedan.</span><span class="sxs-lookup"><span data-stu-id="39266-176">The default implementation is shown below.</span></span> <span data-ttu-id="39266-177">Den accepterar sökvägar som använder både ”/” och ”\\” som avgränsare för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="39266-177">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="39266-178">Den första normaliserar sökvägen till endast ha ”\\” skiljetecken, delar sedan upp den överordnade sökvägen ut på sist ”\\” och returnerar namnet på underordnat del av filsökväg.</span><span class="sxs-lookup"><span data-stu-id="39266-178">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="39266-179">Kom ihåg följande om hur du implementerar GetChildName</span><span class="sxs-lookup"><span data-stu-id="39266-179">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="39266-180">Implementeringen av den [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metoden bör dela upp sökvägen lexically på avgränsare för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="39266-180">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="39266-181">Om den angivna sökvägen innehåller ingen avgränsarna, ska metoden returnera den sökväg som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="39266-181">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39266-182">Den sökväg som angavs i anropet till den här metoden kan innehålla tecken som är ogiltiga i providernamnområde.</span><span class="sxs-lookup"><span data-stu-id="39266-182">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="39266-183">Följande tecken är mest sannolika används för jokertecken expansion eller matchning med reguljära uttryck och implementeringen av den här metoden bör inte ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="39266-183">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="39266-184">Avgör om ett objekt är en behållare</span><span class="sxs-lookup"><span data-stu-id="39266-184">Determining if an Item is a Container</span></span>

<span data-ttu-id="39266-185">Navigering providern kan implementera den [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metod för att avgöra om den angivna sökvägen indikerar en behållare.</span><span class="sxs-lookup"><span data-stu-id="39266-185">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="39266-186">Den returnerar true om sökvägen representerar en behållare och false i annat.</span><span class="sxs-lookup"><span data-stu-id="39266-186">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="39266-187">Användaren behöver den här metoden för att kunna använda den `Test-Path` cmdlet: en för den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="39266-187">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="39266-188">Följande kod visar den [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementering i vårt exempel navigering providern.</span><span class="sxs-lookup"><span data-stu-id="39266-188">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="39266-189">Metoden kontrollerar att den angivna sökvägen är korrekt och om tabellen finns och returnerar true om sökvägen anger en behållare.</span><span class="sxs-lookup"><span data-stu-id="39266-189">The method verifies that  the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="39266-190">Kom ihåg följande om hur du implementerar IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="39266-190">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="39266-191">Navigering leverantören .NET-klass kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning.</span><span class="sxs-lookup"><span data-stu-id="39266-191">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="39266-192">I det här fallet implementeringen av [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) måste se till att sökvägen skickas uppfyller kraven.</span><span class="sxs-lookup"><span data-stu-id="39266-192">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="39266-193">Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) egenskapen.</span><span class="sxs-lookup"><span data-stu-id="39266-193">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="39266-194">Flyttar ett objekt</span><span class="sxs-lookup"><span data-stu-id="39266-194">Moving an Item</span></span>

<span data-ttu-id="39266-195">Stöd i `Move-Item` cmdlet, navigering leverantören implementerar den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metod.</span><span class="sxs-lookup"><span data-stu-id="39266-195">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="39266-196">Den här metoden flyttar objektet som specificeras av den `path` parametern till behållaren på den sökväg som anges i den `destination` parametern.</span><span class="sxs-lookup"><span data-stu-id="39266-196">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="39266-197">Exemplet navigering providern inte åsidosätter den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metod.</span><span class="sxs-lookup"><span data-stu-id="39266-197">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="39266-198">Följande är standardimplementering.</span><span class="sxs-lookup"><span data-stu-id="39266-198">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="39266-199">Kom ihåg följande om hur du implementerar MoveItem</span><span class="sxs-lookup"><span data-stu-id="39266-199">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="39266-200">Navigering leverantören .NET-klass kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning.</span><span class="sxs-lookup"><span data-stu-id="39266-200">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="39266-201">I det här fallet implementeringen av [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) måste se till att sökvägen skickas uppfyller kraven.</span><span class="sxs-lookup"><span data-stu-id="39266-201">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="39266-202">Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, **CmdletProvider.Exclude** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="39266-202">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="39266-203">Som standard åsidosättningar av den här metoden bör inte flytta objekt över befintliga objekt om de [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`.</span><span class="sxs-lookup"><span data-stu-id="39266-203">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="39266-204">Till exempel filsystem providern kopierar inte c:\temp\abc.txt över en befintlig c:\bar.txt-fil, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`.</span><span class="sxs-lookup"><span data-stu-id="39266-204">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="39266-205">Om sökvägen som angetts i den `destination` parametern finns och är en behållare i [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen är inte obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="39266-205">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="39266-206">I det här fallet [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) ska flytta det objektet som anges av den `path` parametern till behållaren som anges av den `destination` parametern som en underordnad.</span><span class="sxs-lookup"><span data-stu-id="39266-206">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="39266-207">Implementeringen av den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrollera dess returvärdet innan du gör några ändringar i datalagret.</span><span class="sxs-lookup"><span data-stu-id="39266-207">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="39266-208">Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i systemtillståndet, till exempel ta bort filer.</span><span class="sxs-lookup"><span data-stu-id="39266-208">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span> <span data-ttu-id="39266-209">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med hänsyn till alla inställningar för kommandoraden eller variabler i Windows PowerShell-körningsmiljön bestämma vad som ska visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="39266-209">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="39266-210">Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod.</span><span class="sxs-lookup"><span data-stu-id="39266-210">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="39266-211">Den här metoden skickar ett meddelande till användaren att godkänna feedback att säga om åtgärden bör behållas.</span><span class="sxs-lookup"><span data-stu-id="39266-211">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="39266-212">Leverantören bör anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) som ytterligare en kontroll efter ändringar av potentiellt skadliga system.</span><span class="sxs-lookup"><span data-stu-id="39266-212">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="39266-213">Bifoga dynamiska parametrar till cmdleten Move-objekt</span><span class="sxs-lookup"><span data-stu-id="39266-213">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="39266-214">Ibland den `Move-Item` cmdlet kräver ytterligare parametrar som tillhandahålls dynamiskt vid körning.</span><span class="sxs-lookup"><span data-stu-id="39266-214">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="39266-215">För att ge dessa dynamiska parametrar, navigering-leverantören måste implementera de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) metod för att hämta de obligatoriska parametervärdena från objektet på den angivna sökvägen och returnera ett objekt med egenskaper och fält med parsning attribut liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt.</span><span class="sxs-lookup"><span data-stu-id="39266-215">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="39266-216">Den här providern för navigering implementerar inte den här metoden.</span><span class="sxs-lookup"><span data-stu-id="39266-216">This navigation provider does not implement this method.</span></span> <span data-ttu-id="39266-217">Följande kod är dock standardimplementering av [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="39266-217">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="39266-218">Normaliserar en relativ sökväg</span><span class="sxs-lookup"><span data-stu-id="39266-218">Normalizing a Relative Path</span></span>

<span data-ttu-id="39266-219">Din navigering providern implementerar den [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metod för att normalisera den fullständiga sökvägen som anges i den `path` parameter är i förhållande till sökvägen som angetts av den `basePath` parametern.</span><span class="sxs-lookup"><span data-stu-id="39266-219">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="39266-220">Metoden returnerar en strängrepresentation av normaliserade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="39266-220">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="39266-221">Den skriver ett fel om de `path` parametern anger en sökväg som inte finns.</span><span class="sxs-lookup"><span data-stu-id="39266-221">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="39266-222">Exemplet navigering providern åsidosätts inte den här metoden.</span><span class="sxs-lookup"><span data-stu-id="39266-222">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="39266-223">Följande är standardimplementering.</span><span class="sxs-lookup"><span data-stu-id="39266-223">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="39266-224">Kom ihåg följande om hur du implementerar NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="39266-224">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="39266-225">Implementeringen av [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) ska tolka den `path` parametern, men det behöver inte använda helt och hållet syntaktiska parsning.</span><span class="sxs-lookup"><span data-stu-id="39266-225">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="39266-226">Du bör utforma den här metoden för att använda sökvägen för att leta upp sökvägsinformation i datalagret och skapa en väg som matchar gemener och versaler och standardiserade sökvägssyntaxen.</span><span class="sxs-lookup"><span data-stu-id="39266-226">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="39266-227">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="39266-227">Code Sample</span></span>

<span data-ttu-id="39266-228">Komplett exempel finns i [AccessDbProviderSample05 kodexempel](./accessdbprovidersample05-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="39266-228">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="39266-229">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="39266-229">Defining Object Types and Formatting</span></span>

<span data-ttu-id="39266-230">Det är möjligt för en provider för att lägga till medlemmar i befintliga objekt eller definiera nya objekt.</span><span class="sxs-lookup"><span data-stu-id="39266-230">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="39266-231">Mer information finns i[utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="39266-231">For more information, see[Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="39266-232">Att skapa Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="39266-232">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="39266-233">Mer information finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="39266-233">For more information, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="39266-234">Testa Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="39266-234">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="39266-235">När din Windows PowerShell-provider har registrerats med Windows PowerShell kan testa du den genom att köra cmdletarna stöds på kommandoraden, inklusive cmdlet: ar som gjorts tillgängliga av härledning.</span><span class="sxs-lookup"><span data-stu-id="39266-235">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="39266-236">Det här exemplet kommer att testa exemplet navigering providern.</span><span class="sxs-lookup"><span data-stu-id="39266-236">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="39266-237">Kör ditt nya gränssnitt och använder den `Set-Location` cmdlet för att ange sökvägen till indikerar Access-databas.</span><span class="sxs-lookup"><span data-stu-id="39266-237">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="39266-238">Kör nu den `Get-Childitem` cmdlet för att hämta en lista över de databasen, som är tillgängliga databastabeller.</span><span class="sxs-lookup"><span data-stu-id="39266-238">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="39266-239">Denna cmdlet hämtar också antalet rader för varje tabell.</span><span class="sxs-lookup"><span data-stu-id="39266-239">For each table, this cmdlet also retrieves the number of table rows.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. <span data-ttu-id="39266-240">Använd den `Set-Location` cmdleten igen för att ange platsen för tabellen Anställda data.</span><span class="sxs-lookup"><span data-stu-id="39266-240">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="39266-241">Nu använder vi den `Get-Location` cmdlet för att hämta sökvägen till tabellen Anställda.</span><span class="sxs-lookup"><span data-stu-id="39266-241">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="39266-242">Nu använda den `Get-Childitem` cmdlet skickas till den `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39266-242">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="39266-243">Den här uppsättningen cmdlet: ar hämtar objekt för tabellen Anställda data som är tabellraderna.</span><span class="sxs-lookup"><span data-stu-id="39266-243">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="39266-244">Formateras som angetts av den `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39266-244">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. <span data-ttu-id="39266-245">Nu kan du köra den `Get-Item` cmdlet för att hämta objekt för rad 0 i tabellen Anställda data.</span><span class="sxs-lookup"><span data-stu-id="39266-245">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. <span data-ttu-id="39266-246">Använd den `Get-Item` cmdleten igen för att hämta medarbetardata för objekten i rad 0.</span><span class="sxs-lookup"><span data-stu-id="39266-246">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a><span data-ttu-id="39266-247">Se även</span><span class="sxs-lookup"><span data-stu-id="39266-247">See Also</span></span>

[<span data-ttu-id="39266-248">Skapa Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="39266-248">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="39266-249">Utforma din Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="39266-249">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="39266-250">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="39266-250">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="39266-251">Implementera en behållare Windows PowerShell-providern</span><span class="sxs-lookup"><span data-stu-id="39266-251">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

[<span data-ttu-id="39266-252">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="39266-252">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="39266-253">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="39266-253">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="39266-254">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="39266-254">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)