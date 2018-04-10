---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Visa objekt struktur Get medlem
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="27b2d-103">Visa objekt strukturen (Get-medlem)</span><span class="sxs-lookup"><span data-stu-id="27b2d-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="27b2d-104">Eftersom spelas upp på en central roll i Windows PowerShell, finns flera inbyggda kommandon som fungerar med valfri objekttyper.</span><span class="sxs-lookup"><span data-stu-id="27b2d-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="27b2d-105">Den viktigaste är den **Get-medlemmen** kommando.</span><span class="sxs-lookup"><span data-stu-id="27b2d-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="27b2d-106">Den enklaste metoden för att analysera objekten som returnerar ett kommando är att skicka utdata från kommandot den **Get-medlemmen** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27b2d-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="27b2d-107">Den **Get-medlemmen** cmdlet visar formella namnet på objekttypen och en fullständig lista över dess medlemmar.</span><span class="sxs-lookup"><span data-stu-id="27b2d-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="27b2d-108">Antalet element som returneras kan ibland vara överväldigande.</span><span class="sxs-lookup"><span data-stu-id="27b2d-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="27b2d-109">Till exempel kan en process-objektet ha fler än 100 medlemmar.</span><span class="sxs-lookup"><span data-stu-id="27b2d-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="27b2d-110">Om du vill se alla medlemmar i en Process-objektet och sidan utdata så att du kan visa alla, skriver du:</span><span class="sxs-lookup"><span data-stu-id="27b2d-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="27b2d-111">Utdata från kommandot ser ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="27b2d-111">The output from this command will look something like this:</span></span>

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

<span data-ttu-id="27b2d-112">Vi kan göra det här lång lista med information mer användbara genom att filtrera för element som vi vill se.</span><span class="sxs-lookup"><span data-stu-id="27b2d-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="27b2d-113">Den **Get-medlemmen** med kommandot kan du visa en lista med endast medlemmar som är egenskaper.</span><span class="sxs-lookup"><span data-stu-id="27b2d-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="27b2d-114">Det finns flera typer av egenskaper.</span><span class="sxs-lookup"><span data-stu-id="27b2d-114">There are several forms of properties.</span></span> <span data-ttu-id="27b2d-115">Cmdlet visar egenskaper för någon typ om vi har angetts i **Get-medlemmen MemberType** parametern med värdet **egenskaper**.</span><span class="sxs-lookup"><span data-stu-id="27b2d-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="27b2d-116">Listan är fortfarande mycket lång, men lite mer användarvänlig:</span><span class="sxs-lookup"><span data-stu-id="27b2d-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="27b2d-117">Tillåtna värden för MemberType är AliasProperty, CodeProperty, egenskapen, NoteProperty, ScriptProperty, egenskaper, PropertySet, metod, CodeMethod, ScriptMethod, metoder, ParameterizedProperty, delmängd och alla.</span><span class="sxs-lookup"><span data-stu-id="27b2d-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="27b2d-118">Det finns över 60 egenskaper för en process.</span><span class="sxs-lookup"><span data-stu-id="27b2d-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="27b2d-119">Orsaken till Windows PowerShell ofta visar bara ett fåtal av egenskaper för ett välkänt objekt som visar alla skulle skapa en svårhanterligt mängd information.</span><span class="sxs-lookup"><span data-stu-id="27b2d-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="27b2d-120">Windows PowerShell avgör hur du visar en objekttyp med hjälp av informationen i XML-filer som har namn som slutar på. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="27b2d-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="27b2d-121">Formatering data för process-objekt som är .NET System.Diagnostics.Process objekt, lagras i DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="27b2d-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="27b2d-122">Om du behöver titta i andra egenskaper än de som visas som standard i Windows PowerShell måste att formatera utdata själv.</span><span class="sxs-lookup"><span data-stu-id="27b2d-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="27b2d-123">Detta kan göras med hjälp av format-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="27b2d-123">This can be done by using the format cmdlets.</span></span>