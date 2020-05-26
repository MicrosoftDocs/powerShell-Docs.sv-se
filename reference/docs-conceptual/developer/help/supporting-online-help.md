---
title: Support online-hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: de25b099e61f82891daff87c4c73bb8cad9111a4
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810129"
---
# <a name="supporting-online-help"></a><span data-ttu-id="21699-102">Stöd för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="21699-102">Supporting Online Help</span></span>

<span data-ttu-id="21699-103">Från och med Windows PowerShell 3,0 finns det två sätt att stödja `Get-Help` funktionen online för Windows PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="21699-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="21699-104">I det här avsnittet beskrivs hur du implementerar den här funktionen för olika kommando typer.</span><span class="sxs-lookup"><span data-stu-id="21699-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="21699-105">Om onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="21699-105">About Online Help</span></span>

<span data-ttu-id="21699-106">Direkt hjälpen har alltid varit en viktig del av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21699-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="21699-107">Även om `Get-Help` cmdlet: en visar hjälp avsnitt i kommando tolken, föredrar många användare upplevelsen av att läsa online, inklusive färg kodning, hyperlänkar och dela idéer i Community-innehåll och wiki-baserade dokument.</span><span class="sxs-lookup"><span data-stu-id="21699-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="21699-108">För det viktigaste, före ankomsten av den uppdaterings bara hjälpen, tillhandahöll online-hjälpen den senaste versionen av hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="21699-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="21699-109">Med ankomsten för uppdaterings bar hjälp i Windows PowerShell 3,0 spelar online-hjälpen fortfarande en viktig roll.</span><span class="sxs-lookup"><span data-stu-id="21699-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="21699-110">Förutom den flexibla användar upplevelsen ger online-hjälpen hjälp till användare som inte kan använda uppdaterings bara hjälp för att hämta hjälp ämnen.</span><span class="sxs-lookup"><span data-stu-id="21699-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="21699-111">Hur Get-Help – Online fungerar</span><span class="sxs-lookup"><span data-stu-id="21699-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="21699-112">För att hjälpa användarna att hitta Onlines hjälp avsnitt för kommandon, `Get-Help` har kommandot en online-version som öppnar online-versionen av hjälp avsnittet för ett kommando i användarens standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="21699-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="21699-113">Följande kommando öppnar till exempel hjälp avsnittet online för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="21699-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="21699-114">För att implementera `Get-Help` – online `Get-Help` söker cmdleten efter en Uniform Resource Identifier (URI) i hjälp avsnittet online-version på följande platser.</span><span class="sxs-lookup"><span data-stu-id="21699-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="21699-115">Den första länken i avsnittet relaterade länkar i hjälp avsnittet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="21699-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="21699-116">Hjälp avsnittet måste vara installerat på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="21699-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="21699-117">Den här funktionen introducerades i Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="21699-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="21699-118">Egenskapen HelpUri för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="21699-118">The HelpUri property of any command.</span></span> <span data-ttu-id="21699-119">Egenskapen HelpUri är tillgänglig även om hjälp avsnittet för kommandot inte är installerat på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="21699-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="21699-120">Den här funktionen introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="21699-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="21699-121">`Get-Help`söker efter en URI i den första posten i avsnittet relaterade länkar innan du hämtar värdet för egenskapen HelpUri.</span><span class="sxs-lookup"><span data-stu-id="21699-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="21699-122">Om egenskap svärdet är felaktigt eller har ändrats kan du åsidosätta det genom att ange ett annat värde i den första relaterade länken.</span><span class="sxs-lookup"><span data-stu-id="21699-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="21699-123">Den första relaterade länken fungerar dock bara när hjälp avsnitten är installerade på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="21699-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="21699-124">Lägga till en URI till den första relaterade länken i ett kommando hjälp avsnitt</span><span class="sxs-lookup"><span data-stu-id="21699-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="21699-125">Du kan stödja `Get-Help` – online för alla kommandon genom att lägga till en giltig URI till den första posten i avsnittet relaterade länkar i det XML-baserade hjälp avsnittet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="21699-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="21699-126">Det här alternativet är endast giltigt i XML-baserade hjälp avsnitt och fungerar bara när hjälp avsnittet är installerat på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="21699-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="21699-127">När hjälp avsnittet är installerat och URI fylls i, prioriteras det här värdet framför kommandots **HelpUri** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="21699-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="21699-128">För att stödja den här funktionen måste URI: n visas i `maml:uri` elementet under det första `maml:relatedLinks/maml:navigationLink` elementet i `maml:relatedLinks` elementet.</span><span class="sxs-lookup"><span data-stu-id="21699-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="21699-129">Följande XML visar rätt placering av URI: n.</span><span class="sxs-lookup"><span data-stu-id="21699-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="21699-130">Texten "online version:" i `maml:linkText` elementet är bästa praxis, men det är inte obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="21699-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="21699-131">Lägga till egenskapen HelpUri i ett kommando</span><span class="sxs-lookup"><span data-stu-id="21699-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="21699-132">I det här avsnittet visas hur du lägger till egenskapen HelpUri i kommandon av olika typer.</span><span class="sxs-lookup"><span data-stu-id="21699-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="21699-133">Lägga till en HelpUri-egenskap till en cmdlet</span><span class="sxs-lookup"><span data-stu-id="21699-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="21699-134">För cmdletar skrivna i C# lägger du till ett **HelpUri** -attribut i cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="21699-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="21699-135">Värdet för attributet måste vara en URI som börjar med "http" eller "https".</span><span class="sxs-lookup"><span data-stu-id="21699-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="21699-136">Följande kod visar HelpUri-attributet för cmdlet- `Get-History` klassen.</span><span class="sxs-lookup"><span data-stu-id="21699-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="21699-137">Lägga till en HelpUri-egenskap i en avancerad funktion</span><span class="sxs-lookup"><span data-stu-id="21699-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="21699-138">För avancerade funktioner lägger du till en **HelpUri** -egenskap till attributet **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="21699-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="21699-139">Värdet för egenskapen måste vara en URI som börjar med "http" eller "https".</span><span class="sxs-lookup"><span data-stu-id="21699-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="21699-140">Följande kod visar attributet HelpUri för funktionen New-Calendar</span><span class="sxs-lookup"><span data-stu-id="21699-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="21699-141">Lägga till ett HelpUri-attribut till ett CIM-kommando</span><span class="sxs-lookup"><span data-stu-id="21699-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="21699-142">För CIM-kommandon lägger du till ett **HelpUri** -attribut till **CmdletMetadata** -elementet i cdxlm-filen.</span><span class="sxs-lookup"><span data-stu-id="21699-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="21699-143">Värdet för attributet måste vara en URI som börjar med "http" eller "https".</span><span class="sxs-lookup"><span data-stu-id="21699-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="21699-144">Följande kod visar attributet HelpUri för CIM-kommandot start-debug</span><span class="sxs-lookup"><span data-stu-id="21699-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="21699-145">Lägga till ett HelpUri-attribut i ett arbets flöde</span><span class="sxs-lookup"><span data-stu-id="21699-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="21699-146">För arbets flöden som är skrivna på Windows PowerShell-språket lägger du till ett **. ExternalHelp** kommentars direktiv till arbets flödes koden.</span><span class="sxs-lookup"><span data-stu-id="21699-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="21699-147">Värdet för direktivet måste vara en URI som börjar med "http" eller "https".</span><span class="sxs-lookup"><span data-stu-id="21699-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="21699-148">Egenskapen HelpUri stöds inte för XAML-baserade arbets flöden i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21699-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="21699-149">Följande kod visar. ExternalHelp-direktiv i en arbets flödes fil.</span><span class="sxs-lookup"><span data-stu-id="21699-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
