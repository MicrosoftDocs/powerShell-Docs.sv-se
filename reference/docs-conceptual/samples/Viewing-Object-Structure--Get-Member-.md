---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Visa objekt strukturen Hämta medlem
description: Get-Member är ett kraftfullt verktyg som gör det möjligt att se objektets typ och struktur i PowerShell.
ms.openlocfilehash: 3c294fe47294e2cf8daf125aac55661dd38cf9bb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501226"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="9f382-104">Visa objektstrukturen (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="9f382-104">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="9f382-105">Eftersom objekt spelar en sådan central roll i Windows PowerShell finns det flera inbyggda kommandon som är utformade för att fungera med valfria objekt typer.</span><span class="sxs-lookup"><span data-stu-id="9f382-105">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="9f382-106">Den viktigaste en är kommandot **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="9f382-106">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="9f382-107">Den enklaste metoden för att analysera de objekt som ett kommando returnerar är att skicka tillbaka kommandots utdata till cmdleten **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="9f382-107">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="9f382-108">Cmdleten **Get-Member** visar det formella namnet på objekt typen och en fullständig lista över dess medlemmar.</span><span class="sxs-lookup"><span data-stu-id="9f382-108">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="9f382-109">Antalet element som returneras kan ibland vara överbelastat.</span><span class="sxs-lookup"><span data-stu-id="9f382-109">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="9f382-110">Ett process objekt kan till exempel ha över 100 medlemmar.</span><span class="sxs-lookup"><span data-stu-id="9f382-110">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="9f382-111">Om du vill se alla medlemmar i ett process objekt och sidan utdata så att du kan visa allt, skriver du:</span><span class="sxs-lookup"><span data-stu-id="9f382-111">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="9f382-112">Utdata från det här kommandot ser ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="9f382-112">The output from this command will look something like this:</span></span>

```Output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="9f382-113">Vi kan göra den här långa listan över information mer användbar genom filtrering av element som vi vill se.</span><span class="sxs-lookup"><span data-stu-id="9f382-113">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="9f382-114">Med kommandot **Get-Member** kan du bara lista medlemmar som är egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9f382-114">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="9f382-115">Det finns flera typer av egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9f382-115">There are several forms of properties.</span></span> <span data-ttu-id="9f382-116">Cmdleten visar egenskaper av valfri typ om vi ställer in parametern **Get-Member MemberType** på värde **egenskaperna**.</span><span class="sxs-lookup"><span data-stu-id="9f382-116">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="9f382-117">Den resulterande listan är fortfarande mycket lång, men en lite mer hanterbar:</span><span class="sxs-lookup"><span data-stu-id="9f382-117">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="9f382-118">De tillåtna värdena för MemberType är AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, metoder, ParameterizedProperty, MemberSet och alla.</span><span class="sxs-lookup"><span data-stu-id="9f382-118">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="9f382-119">Det finns över 60 egenskaper för en process.</span><span class="sxs-lookup"><span data-stu-id="9f382-119">There are over 60 properties for a process.</span></span> <span data-ttu-id="9f382-120">Orsaken till att Windows PowerShell ofta visar att det bara finns en fåtal av egenskaperna för ett välkänt objekt är att alla kan ge en ohanterad mängd information.</span><span class="sxs-lookup"><span data-stu-id="9f382-120">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="9f382-121">Windows PowerShell avgör hur du visar en objekt typ genom att använda information som lagras i XML-filer med namn som slutar på .format.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="9f382-121">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="9f382-122">Formatering av data för process objekt, som är .NET system. Diagnostics. process-objekt, lagras i DotNetTypes.format.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="9f382-122">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="9f382-123">Om du behöver titta på andra egenskaper än de som Windows PowerShell visar som standard, behöver du bara formatera utdata.</span><span class="sxs-lookup"><span data-stu-id="9f382-123">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="9f382-124">Detta kan göras med hjälp av format-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="9f382-124">This can be done by using the format cmdlets.</span></span>
