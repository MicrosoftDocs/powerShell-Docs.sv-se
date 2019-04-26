---
title: Utöka utdata objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068172"
---
# <a name="extending-output-objects"></a><span data-ttu-id="8d7fa-102">Utöka utdataobjekt</span><span class="sxs-lookup"><span data-stu-id="8d7fa-102">Extending Output Objects</span></span>

<span data-ttu-id="8d7fa-103">Du kan utöka .NET Framework-objekt som returneras av cmdlet: ar, funktioner och skript med hjälp av typer filer (.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="8d7fa-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="8d7fa-104">Typer av filer är XML-baserade filer som låter dig lägga till egenskaper och metoder för befintliga objekt.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="8d7fa-105">Windows PowerShell innehåller till exempel filen Types.ps1xml, som lägger tillför element i flera befintliga .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="8d7fa-106">Filen Types.ps1xml finns i installationskatalogen för Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="8d7fa-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="8d7fa-107">Du kan skapa en egen typer fil att utöka dessa objekt eller utöka andra objekt.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="8d7fa-108">När du utökar ett objekt med hjälp av en typer har valfri instans av objektet utökats med de nya elementen.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="8d7fa-109">Utöka System.Array-objekt</span><span class="sxs-lookup"><span data-stu-id="8d7fa-109">Extending the System.Array Object</span></span>

<span data-ttu-id="8d7fa-110">I följande exempel visas hur Windows PowerShell utökar den [System.Array](/dotnet/api/System.Array) objekt i filen Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="8d7fa-111">Som standard [System.Array](/dotnet/api/System.Array) objekt har en `Length` egenskap som visar antalet objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="8d7fa-112">Men eftersom ”namnlängd” inte beskriver egenskapen tydligt, Windows PowerShell lägger till den `Count` alias-egenskapen, som visar samma värde som den `Length` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="8d7fa-113">Följande XML-filen lägger till den `Count` egenskap enligt den [System.Array](/dotnet/api/System.Array) typen.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

<span data-ttu-id="8d7fa-114">Om du vill se den nya egenskapen alias, använda en [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) kommandot på alla matris, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="8d7fa-115">Kommandot returnerar följande resultat.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-115">The command returns the following results.</span></span>
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
<span data-ttu-id="8d7fa-116">Du kan använda antingen den `Count` egenskapen eller `Length` egenskapen att avgöra hur många objekt som är i en matris.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="8d7fa-117">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="8d7fa-117">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="8d7fa-118">Anpassade filer</span><span class="sxs-lookup"><span data-stu-id="8d7fa-118">Custom Types Files</span></span>

<span data-ttu-id="8d7fa-119">Starta genom att kopiera en befintlig typer-fil för att skapa en fil för anpassade typer.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="8d7fa-120">Den nya filen kan ha vilket namn, men den måste ha filnamnstillägget .ps1xml.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="8d7fa-121">När du kopierar filen, du kan placera den nya filen i en katalog som är tillgänglig för Windows PowerShell, men det är bra att placera filerna i installationskatalogen för Windows PowerShell (`$pshome`) eller i en underkatalog till installationskatalogen.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="8d7fa-122">Om du vill lägga till egna utökade typer i filen, lägger du till en typer-element för varje objekt som du vill utöka.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="8d7fa-123">I följande avsnitt innehåller exempel.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-123">The following topics provide examples.</span></span>

- <span data-ttu-id="8d7fa-124">Läs mer om att lägga till egenskaper och egenskapsuppsättningar [utökade egenskaper](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="8d7fa-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="8d7fa-125">Läs mer om att lägga till metoder, [utökade metoder](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="8d7fa-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="8d7fa-126">Läs mer om att lägga till medlemmen uppsättningar [utökade medlem anger](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="8d7fa-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="8d7fa-127">När du har definierat dina egna utökade typer kan du använda någon av följande metoder för att tillgängliggöra dina utökade objekt:</span><span class="sxs-lookup"><span data-stu-id="8d7fa-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="8d7fa-128">Om du vill göra din fil för utökade typer som är tillgängliga för den aktuella sessionen, använda den [uppdatering TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet för att lägga till den nya filen.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="8d7fa-129">Om du vill att din typer för att få företräde framför de typer som definieras i andra typer (inklusive Types.ps1xml-fil), använder den `PrependData` -parametern för den [uppdatering TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="8d7fa-130">För att göra din fil för utökade typer tillgängliga för alla framtida sessioner, lägga till filen typer till en modul, exportera den aktuella sessionen eller Lägg till den [uppdatering TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) kommandot Windows PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="8d7fa-131">Signerar typer filer</span><span class="sxs-lookup"><span data-stu-id="8d7fa-131">Signing Types Files</span></span>

<span data-ttu-id="8d7fa-132">Typer av filer vara digitalt signerade att förhindra manipulation eftersom XML-filen kan innehålla skriptblock.</span><span class="sxs-lookup"><span data-stu-id="8d7fa-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="8d7fa-133">Läs mer om att lägga till digitala signaturer [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="8d7fa-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="8d7fa-134">Se även</span><span class="sxs-lookup"><span data-stu-id="8d7fa-134">See Also</span></span>

[<span data-ttu-id="8d7fa-135">Definiera standardegenskaperna för objekt</span><span class="sxs-lookup"><span data-stu-id="8d7fa-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="8d7fa-136">Definiera standard metoder för objekt</span><span class="sxs-lookup"><span data-stu-id="8d7fa-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="8d7fa-137">Definiera standard medlemsuppsättningar för objekt</span><span class="sxs-lookup"><span data-stu-id="8d7fa-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="8d7fa-138">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d7fa-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
