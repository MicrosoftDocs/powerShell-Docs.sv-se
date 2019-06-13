---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Visa objektstrukturen Get-Member
ms.openlocfilehash: 80b36abd303a708195f12d96511e616178d11b5a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030715"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="5f44d-103">Visa objektstrukturen (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="5f44d-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="5f44d-104">Eftersom objekt spelar en central roll i Windows PowerShell, det finns flera inbyggda kommandon som utformats för att fungera med godtyckliga objekttyper.</span><span class="sxs-lookup"><span data-stu-id="5f44d-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="5f44d-105">Den viktigaste är den **Get-Member** kommando.</span><span class="sxs-lookup"><span data-stu-id="5f44d-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="5f44d-106">Den enklaste tekniken för att analysera de objekt som returnerar ett kommando är att skicka utdata från kommandot den **Get-Member** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f44d-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="5f44d-107">Den **Get-Member** cmdlet visar formella namnet på objekttypen och en fullständig lista över dess medlemmar.</span><span class="sxs-lookup"><span data-stu-id="5f44d-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="5f44d-108">Antalet element som returneras kan ibland vara överväldigande.</span><span class="sxs-lookup"><span data-stu-id="5f44d-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="5f44d-109">Ett processobjekt kan exempelvis ha fler än 100 medlemmar.</span><span class="sxs-lookup"><span data-stu-id="5f44d-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="5f44d-110">Om du vill se alla medlemmar i en processobjektet och sidan utdata så att du kan visa allt det, skriver du:</span><span class="sxs-lookup"><span data-stu-id="5f44d-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="5f44d-111">Utdata från det här kommandot ska se ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="5f44d-111">The output from this command will look something like this:</span></span>

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

<span data-ttu-id="5f44d-112">Vi kan göra den här lång lista med information mer användbara genom att filtrera för element som vi vill se.</span><span class="sxs-lookup"><span data-stu-id="5f44d-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="5f44d-113">Den **Get-Member** kommandot kan du visa endast medlemmar som är egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5f44d-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="5f44d-114">Det finns flera typer av egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5f44d-114">There are several forms of properties.</span></span> <span data-ttu-id="5f44d-115">Cmdlet visar egenskaper för alla typer av om vi ger den **Get-Member MemberType** parametern till värdet **egenskaper**.</span><span class="sxs-lookup"><span data-stu-id="5f44d-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="5f44d-116">Den resulterande listan är fortfarande mycket långa, men lite mer hanterbara:</span><span class="sxs-lookup"><span data-stu-id="5f44d-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="5f44d-117">Tillåtna värden för MemberType är AliasProperty, CodeProperty, egenskapen, NoteProperty, ScriptProperty, egenskaper, PropertySet, metod, CodeMethod, ScriptMethod, metoder, ParameterizedProperty, delmängd och alla.</span><span class="sxs-lookup"><span data-stu-id="5f44d-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="5f44d-118">Det finns över 60 egenskaper för en process.</span><span class="sxs-lookup"><span data-stu-id="5f44d-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="5f44d-119">Orsaken till Windows PowerShell ofta visar endast ett fåtal egenskaper för alla välkända objekt som visar alla resulterar i ett svårhanterligt mängd information.</span><span class="sxs-lookup"><span data-stu-id="5f44d-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="5f44d-120">Windows PowerShell avgör hur du vill visa en objekttyp med hjälp av information som lagras i XML-filer som har namn som slutar på. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="5f44d-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="5f44d-121">Formatering data för process-objekt, vilket är .NET System.Diagnostics.Process objekt, lagras i DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="5f44d-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="5f44d-122">Om du vill titta på andra egenskaper än de som Windows PowerShell visar som standard kommer du behöva formatera utdata själv.</span><span class="sxs-lookup"><span data-stu-id="5f44d-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="5f44d-123">Detta kan göras med hjälp av format-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5f44d-123">This can be done by using the format cmdlets.</span></span>
