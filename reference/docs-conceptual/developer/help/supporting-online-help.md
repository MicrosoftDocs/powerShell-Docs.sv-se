---
ms.date: 09/13/2016
ms.topic: reference
title: Stöd för onlinehjälp
description: Stöd för onlinehjälp
ms.openlocfilehash: 0164b5e6c6c8d66a6ab2467a8adfb7efffe0fe17
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645424"
---
# <a name="supporting-online-help"></a><span data-ttu-id="8b686-103">Stöd för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="8b686-103">Supporting Online Help</span></span>

<span data-ttu-id="8b686-104">Från och med PowerShell 3,0 finns det två sätt att stödja `Get-Help` funktionen online för PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="8b686-104">Beginning in PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for PowerShell commands.</span></span> <span data-ttu-id="8b686-105">I det här avsnittet beskrivs hur du implementerar den här funktionen för olika kommando typer.</span><span class="sxs-lookup"><span data-stu-id="8b686-105">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="8b686-106">Om onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="8b686-106">About Online Help</span></span>

<span data-ttu-id="8b686-107">Direkt hjälpen har alltid varit en viktig del av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b686-107">Online help has always been a vital part of PowerShell.</span></span> <span data-ttu-id="8b686-108">Även om `Get-Help` cmdlet: en visar hjälp avsnitt i kommando tolken, föredrar många användare upplevelsen av att läsa online, inklusive färg kodning, hyperlänkar och dela idéer i Community-innehåll och wiki-baserade dokument.</span><span class="sxs-lookup"><span data-stu-id="8b686-108">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="8b686-109">För det viktigaste, före ankomsten av den uppdaterings bara hjälpen, tillhandahöll online-hjälpen den senaste versionen av hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="8b686-109">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="8b686-110">Med ankomsten för uppdaterings bar hjälp i PowerShell 3,0 spelar onlinehjälpen fortfarande en viktig roll.</span><span class="sxs-lookup"><span data-stu-id="8b686-110">With the advent of Updatable Help in PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="8b686-111">Förutom den flexibla användar upplevelsen ger online-hjälpen hjälp till användare som inte kan använda uppdaterings bara hjälp för att hämta hjälp ämnen.</span><span class="sxs-lookup"><span data-stu-id="8b686-111">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="8b686-112">Så här fungerar Get-Help – online</span><span class="sxs-lookup"><span data-stu-id="8b686-112">How Get-Help -Online Works</span></span>

<span data-ttu-id="8b686-113">För att hjälpa användarna att hitta Onlines hjälp avsnitt för kommandon, `Get-Help` har kommandot en online-version som öppnar online-versionen av hjälp avsnittet för ett kommando i användarens standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="8b686-113">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default internet browser.</span></span>

<span data-ttu-id="8b686-114">Följande kommando öppnar till exempel hjälp avsnittet online för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b686-114">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="8b686-115">För att implementera `Get-Help -Online` `Get-Help` söker cmdleten efter en Uniform Resource Identifier (URI) för hjälp avsnittet online-version på följande platser.</span><span class="sxs-lookup"><span data-stu-id="8b686-115">To implement `Get-Help -Online`, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="8b686-116">Den första länken i avsnittet **relaterade länkar** i hjälp avsnittet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b686-116">The first link in the **Related Links** section of the help topic for the command.</span></span> <span data-ttu-id="8b686-117">Hjälp avsnittet måste vara installerat på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="8b686-117">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="8b686-118">Den här funktionen introducerades i PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="8b686-118">This feature was introduced in PowerShell 2.0.</span></span>

- <span data-ttu-id="8b686-119">Egenskapen **HelpUri** för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="8b686-119">The **HelpUri** property of any command.</span></span> <span data-ttu-id="8b686-120">Egenskapen **HelpUri** är tillgänglig även om hjälp avsnittet för kommandot inte är installerat på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="8b686-120">The **HelpUri** property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="8b686-121">Den här funktionen introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8b686-121">This feature was introduced in PowerShell 3.0.</span></span>

  <span data-ttu-id="8b686-122">`Get-Help` söker efter en URI i den första posten i avsnittet **relaterade länkar** innan du hämtar värdet för egenskapen **HelpUri** .</span><span class="sxs-lookup"><span data-stu-id="8b686-122">`Get-Help` looks for a URI in the first entry in the **Related Links** section before getting the **HelpUri** property value.</span></span> <span data-ttu-id="8b686-123">Om egenskap svärdet är felaktigt eller har ändrats kan du åsidosätta det genom att ange ett annat värde i den första relaterade länken.</span><span class="sxs-lookup"><span data-stu-id="8b686-123">If the property value is incorrect or has changed, you can override it by entering a different value in the first related link.</span></span> <span data-ttu-id="8b686-124">Den första relaterade länken fungerar dock bara när hjälp avsnitten är installerade på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="8b686-124">However, the first related link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="8b686-125">Lägga till en URI till den första relaterade länken i ett kommando hjälp avsnitt</span><span class="sxs-lookup"><span data-stu-id="8b686-125">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="8b686-126">Du kan använda `Get-Help -Online` ett kommando genom att lägga till en giltig URI i den första posten i **avsnittet relaterade länkar** i det XML-baserade hjälp avsnittet för kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b686-126">You can support `Get-Help -Online` for any command by adding a valid URI to the first entry in the **Related Links** section of the XML-based help topic for the command.</span></span> <span data-ttu-id="8b686-127">Det här alternativet är endast giltigt i XML-baserade hjälp avsnitt och fungerar bara när hjälp avsnittet är installerat på användarens dator.</span><span class="sxs-lookup"><span data-stu-id="8b686-127">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="8b686-128">När hjälp avsnittet är installerat och URI fylls i, prioriteras det här värdet framför kommandots **HelpUri** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="8b686-128">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="8b686-129">För att stödja den här funktionen måste URI: n visas i `maml:uri` elementet under det första `maml:relatedLinks/maml:navigationLink` elementet i `maml:relatedLinks` elementet.</span><span class="sxs-lookup"><span data-stu-id="8b686-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="8b686-130">Följande XML visar rätt placering av URI: n.</span><span class="sxs-lookup"><span data-stu-id="8b686-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="8b686-131">`Online version:`Texten i `maml:linkText` elementet är bästa praxis, men det är inget krav.</span><span class="sxs-lookup"><span data-stu-id="8b686-131">The `Online version:` text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

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

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="8b686-132">Lägga till egenskapen HelpUri i ett kommando</span><span class="sxs-lookup"><span data-stu-id="8b686-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="8b686-133">I det här avsnittet visas hur du lägger till egenskapen HelpUri i kommandon av olika typer.</span><span class="sxs-lookup"><span data-stu-id="8b686-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="8b686-134">Lägga till en HelpUri-egenskap till en cmdlet</span><span class="sxs-lookup"><span data-stu-id="8b686-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="8b686-135">För cmdletar skrivna i C# lägger du till ett **HelpUri** -attribut i **cmdlet** -klassen.</span><span class="sxs-lookup"><span data-stu-id="8b686-135">For cmdlets written in C#, add a **HelpUri** attribute to the **Cmdlet** class.</span></span> <span data-ttu-id="8b686-136">Värdet för attributet måste vara en URI som börjar med `http` eller `https` .</span><span class="sxs-lookup"><span data-stu-id="8b686-136">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="8b686-137">Följande kod visar **HelpUri** -attributet för cmdlet- `Get-History` klassen.</span><span class="sxs-lookup"><span data-stu-id="8b686-137">The following code shows the **HelpUri** attribute of the `Get-History` cmdlet class.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="8b686-138">Lägga till en HelpUri-egenskap i en avancerad funktion</span><span class="sxs-lookup"><span data-stu-id="8b686-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="8b686-139">För avancerade funktioner lägger du till en **HelpUri** -egenskap till attributet **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="8b686-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="8b686-140">Värdet för egenskapen måste vara en URI som börjar med "http" eller "https".</span><span class="sxs-lookup"><span data-stu-id="8b686-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="8b686-141">Följande kod visar **HelpUri** -attributet för `New-Calendar` funktionen</span><span class="sxs-lookup"><span data-stu-id="8b686-141">The following code shows the **HelpUri** attribute of the `New-Calendar` function</span></span>

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="8b686-142">Lägga till ett HelpUri-attribut till ett CIM-kommando</span><span class="sxs-lookup"><span data-stu-id="8b686-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="8b686-143">För CIM-kommandon lägger du till ett **HelpUri** -attribut till **CmdletMetadata** -elementet i cdxlm-filen.</span><span class="sxs-lookup"><span data-stu-id="8b686-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span>
<span data-ttu-id="8b686-144">Värdet för attributet måste vara en URI som börjar med `http` eller `https` .</span><span class="sxs-lookup"><span data-stu-id="8b686-144">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="8b686-145">Följande kod visar attributet HelpUri för `Start-Debug` CIM-kommandot</span><span class="sxs-lookup"><span data-stu-id="8b686-145">The following code shows the HelpUri attribute of the `Start-Debug` CIM command</span></span>

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="8b686-146">Lägga till ett HelpUri-attribut i ett arbets flöde</span><span class="sxs-lookup"><span data-stu-id="8b686-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="8b686-147">För arbets flöden som är skrivna på PowerShell-språket lägger du till en **. ExternalHelp** kommentars direktiv till arbets flödes koden.</span><span class="sxs-lookup"><span data-stu-id="8b686-147">For workflows that are written in the PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="8b686-148">Värdet för direktivet måste vara en URI som börjar med `http` eller `https` .</span><span class="sxs-lookup"><span data-stu-id="8b686-148">The value of the directive must be a URI that begins with `http` or `https`.</span></span>

> [!NOTE]
> <span data-ttu-id="8b686-149">Egenskapen HelpUri stöds inte för XAML-baserade arbets flöden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b686-149">The HelpUri property is not supported for XAML-based workflows in PowerShell.</span></span>

<span data-ttu-id="8b686-150">Följande kod visar. ExternalHelp-direktiv i en arbets flödes fil.</span><span class="sxs-lookup"><span data-stu-id="8b686-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
