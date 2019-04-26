---
title: Stöd för onlinehjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082149"
---
# <a name="supporting-online-help"></a><span data-ttu-id="09f25-102">Stöd för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="09f25-102">Supporting Online Help</span></span>

<span data-ttu-id="09f25-103">Från och med Windows PowerShell 3.0, det finns två sätt att stödja den `Get-Help` Online funktionen för Windows PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="09f25-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="09f25-104">Det här avsnittet förklarar hur du implementerar den här funktionen för olika kommandotyper.</span><span class="sxs-lookup"><span data-stu-id="09f25-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="09f25-105">Om onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="09f25-105">About Online Help</span></span>

<span data-ttu-id="09f25-106">Onlinehjälp har alltid varit en viktig del av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09f25-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="09f25-107">Även om den `Get-Help` cmdlet visar hjälpavsnitt i Kommandotolken, många användare föredrar upplevelsen läsa online, inklusive färgkodning, hyperlänkar och dela idéer i Community-innehåll och wiki-baserade dokument.</span><span class="sxs-lookup"><span data-stu-id="09f25-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="09f25-108">Innan du ankomsten av uppdateringsbar hjälp tillhandahålls onlinehjälp viktigast av allt, den senaste versionen av hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="09f25-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="09f25-109">Med ankomsten av uppdateringsbar hjälp i Windows PowerShell 3.0 spelar fortfarande en viktig roll i onlinehjälpen.</span><span class="sxs-lookup"><span data-stu-id="09f25-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="09f25-110">Förutom den flexibla användarupplevelsen hjälper onlinehjälp användare som inte vill eller kan inte använda uppdateringsbar hjälp för att hämta hjälpavsnitt.</span><span class="sxs-lookup"><span data-stu-id="09f25-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="09f25-111">Hur Get-Help-Online fungerar</span><span class="sxs-lookup"><span data-stu-id="09f25-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="09f25-112">Att hjälpa användarna att hitta online hjälpavsnitt för kommandon i `Get-Help` kommandot har en Online-parameter som öppnar onlineversionen av hjälpavsnittet för ett kommando i användarens standardwebbläsare.</span><span class="sxs-lookup"><span data-stu-id="09f25-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="09f25-113">Till exempel följande kommando öppnar hjälpen för den `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="09f25-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="09f25-114">Att implementera `Get-Help` -Online, den `Get-Help` cmdlet ser ut för en identifierare URI (Uniform Resource) för onlineversion hjälpavsnitt på följande platser.</span><span class="sxs-lookup"><span data-stu-id="09f25-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="09f25-115">Den första länken i avsnittet med länkar i hjälpavsnittet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="09f25-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="09f25-116">Hjälpavsnittet måste installeras på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="09f25-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="09f25-117">Den här funktionen introducerades i Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="09f25-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="09f25-118">HelpUri-egenskapen för alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="09f25-118">The HelpUri property of any command.</span></span> <span data-ttu-id="09f25-119">HelpUri-egenskapen är tillgänglig även när hjälpavsnittet för kommandot inte är installerad på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="09f25-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="09f25-120">Den här funktionen introducerades i Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="09f25-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="09f25-121">`Get-Help` söker efter en URI i den första posten i avsnittet länkarna innan du hämtar värdet för HelpUri-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="09f25-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="09f25-122">Du kan åsidosätta den genom att ange ett annat värde i den första relaterad länk om egenskapens värde är felaktig eller har ändrats.</span><span class="sxs-lookup"><span data-stu-id="09f25-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="09f25-123">Den första relaterade länken fungerar dock bara när hjälpavsnitten installeras på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="09f25-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="09f25-124">Att lägga till en URI för första relaterade länken i ett hjälpavsnitt för kommandot</span><span class="sxs-lookup"><span data-stu-id="09f25-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="09f25-125">Du kan använda `Get-Help` -Online för alla kommandon genom att lägga till en giltig URI till den första posten i avsnittet med länkar i XML-baserade hjälpavsnittet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="09f25-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="09f25-126">Det här alternativet är endast giltig i XML-baserade hjälpavsnitt och fungerar bara när hjälpavsnittet installeras på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="09f25-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="09f25-127">När hjälpavsnittet är installerad och URI: N har fyllts i det här värdet har företräde framför den **HelpUri** egenskapen för kommandot.</span><span class="sxs-lookup"><span data-stu-id="09f25-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="09f25-128">Information om XML-baserade hjälpavsnitt för kommandon finns i [Writing XML-Based hjälpavsnitt för kommandon](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="09f25-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="09f25-129">För att stödja den här funktionen, URI: N måste finnas i den `maml:uri` elementet under först `maml:relatedLinks/maml:navigationLink` elementet i den `maml:relatedLinks` element.</span><span class="sxs-lookup"><span data-stu-id="09f25-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="09f25-130">Följande XML visar korrekt placering av URI: N.</span><span class="sxs-lookup"><span data-stu-id="09f25-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="09f25-131">Den ”onlineversion”: texten i den `maml:linkText` element är en bra idé, men det är inte obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="09f25-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="09f25-132">Att lägga till HelpUri-egenskapen till ett kommando</span><span class="sxs-lookup"><span data-stu-id="09f25-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="09f25-133">Det här avsnittet visar hur du lägger till HelpUri-egenskapen till kommandon för olika typer.</span><span class="sxs-lookup"><span data-stu-id="09f25-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="09f25-134">Att lägga till HelpUri-egenskapen för en Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09f25-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="09f25-135">För cmdletar som skrivits i C#, lägga till en **HelpUri** attributet till Cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="09f25-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="09f25-136">Värdet för attributet måste vara en URI som börjar med ”http” eller ”https”.</span><span class="sxs-lookup"><span data-stu-id="09f25-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="09f25-137">Följande kod visar HelpUri-attributet för den `Get-History` cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="09f25-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="09f25-138">Att lägga till HelpUri-egenskapen i en avancerad funktion</span><span class="sxs-lookup"><span data-stu-id="09f25-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="09f25-139">För avancerade funktioner, lägger du till en **HelpUri** egenskap enligt den **CmdletBinding** attribut.</span><span class="sxs-lookup"><span data-stu-id="09f25-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="09f25-140">Värdet på egenskapen måste vara en URI som börjar med ”http” eller ”https”.</span><span class="sxs-lookup"><span data-stu-id="09f25-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="09f25-141">Följande kod visar HelpUri-attributet för funktionen New-kalender</span><span class="sxs-lookup"><span data-stu-id="09f25-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="09f25-142">Att lägga till HelpUri-attributet i en CIM-kommando</span><span class="sxs-lookup"><span data-stu-id="09f25-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="09f25-143">CIM-kommandon, lägger du till en **HelpUri** attributet den **CmdletMetadata** elementet i filen CDXLM.</span><span class="sxs-lookup"><span data-stu-id="09f25-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="09f25-144">Värdet för attributet måste vara en URI som börjar med ”http” eller ”https”.</span><span class="sxs-lookup"><span data-stu-id="09f25-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="09f25-145">Följande kod visar HelpUri-attributet Start-Debug CIM-kommandot</span><span class="sxs-lookup"><span data-stu-id="09f25-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="09f25-146">Att lägga till HelpUri-attributet i ett arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="09f25-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="09f25-147">Arbetsflöden som är skrivna i Windows PowerShell-språket, lägger du till en **. ExternalHelp** kommentar direktiv i arbetsflödet-koden.</span><span class="sxs-lookup"><span data-stu-id="09f25-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="09f25-148">Värdet för direktivet måste vara en URI som börjar med ”http” eller ”https”.</span><span class="sxs-lookup"><span data-stu-id="09f25-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="09f25-149">HelpUri-egenskapen stöds inte för XAML-baserade arbetsflöden i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09f25-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="09f25-150">Följande kod visar den. ExternalHelp direktiv i en arbetsflödesfil.</span><span class="sxs-lookup"><span data-stu-id="09f25-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```