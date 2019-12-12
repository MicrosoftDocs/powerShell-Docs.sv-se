---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Visa objekt strukturen Hämta medlem
ms.openlocfilehash: 80b36abd303a708195f12d96511e616178d11b5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030715"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="d0390-103">Visa objekt struktur (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="d0390-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="d0390-104">Eftersom objekt spelar en sådan central roll i Windows PowerShell finns det flera inbyggda kommandon som är utformade för att fungera med valfria objekt typer.</span><span class="sxs-lookup"><span data-stu-id="d0390-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="d0390-105">Den viktigaste en är kommandot **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="d0390-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="d0390-106">Den enklaste metoden för att analysera de objekt som ett kommando returnerar är att skicka tillbaka kommandots utdata till cmdleten **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="d0390-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="d0390-107">Cmdleten **Get-Member** visar det formella namnet på objekt typen och en fullständig lista över dess medlemmar.</span><span class="sxs-lookup"><span data-stu-id="d0390-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="d0390-108">Antalet element som returneras kan ibland vara överbelastat.</span><span class="sxs-lookup"><span data-stu-id="d0390-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="d0390-109">Ett process objekt kan till exempel ha över 100 medlemmar.</span><span class="sxs-lookup"><span data-stu-id="d0390-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="d0390-110">Om du vill se alla medlemmar i ett process objekt och sidan utdata så att du kan visa allt, skriver du:</span><span class="sxs-lookup"><span data-stu-id="d0390-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="d0390-111">Utdata från det här kommandot ser ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="d0390-111">The output from this command will look something like this:</span></span>

```output
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

<span data-ttu-id="d0390-112">Vi kan göra den här långa listan över information mer användbar genom filtrering av element som vi vill se.</span><span class="sxs-lookup"><span data-stu-id="d0390-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="d0390-113">Med kommandot **Get-Member** kan du bara lista medlemmar som är egenskaper.</span><span class="sxs-lookup"><span data-stu-id="d0390-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="d0390-114">Det finns flera typer av egenskaper.</span><span class="sxs-lookup"><span data-stu-id="d0390-114">There are several forms of properties.</span></span> <span data-ttu-id="d0390-115">Cmdleten visar egenskaper av valfri typ om vi ställer in parametern **Get-Member MemberType** på värde **egenskaperna**.</span><span class="sxs-lookup"><span data-stu-id="d0390-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="d0390-116">Den resulterande listan är fortfarande mycket lång, men en lite mer hanterbar:</span><span class="sxs-lookup"><span data-stu-id="d0390-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="d0390-117">De tillåtna värdena för MemberType är AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, metoder, ParameterizedProperty, MemberSet och alla.</span><span class="sxs-lookup"><span data-stu-id="d0390-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="d0390-118">Det finns över 60 egenskaper för en process.</span><span class="sxs-lookup"><span data-stu-id="d0390-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="d0390-119">Orsaken till att Windows PowerShell ofta visar att det bara finns en fåtal av egenskaperna för ett välkänt objekt är att alla kan ge en ohanterad mängd information.</span><span class="sxs-lookup"><span data-stu-id="d0390-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="d0390-120">Windows PowerShell avgör hur du visar en objekt typ genom att använda information som lagras i XML-filer med namn som slutar med. format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="d0390-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="d0390-121">Formatering av data för process objekt, som är .NET system. Diagnostics. process-objekt, lagras i DotNetTypes. format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="d0390-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="d0390-122">Om du behöver titta på andra egenskaper än de som Windows PowerShell visar som standard, behöver du bara formatera utdata.</span><span class="sxs-lookup"><span data-stu-id="d0390-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="d0390-123">Detta kan göras med hjälp av format-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="d0390-123">This can be done by using the format cmdlets.</span></span>
