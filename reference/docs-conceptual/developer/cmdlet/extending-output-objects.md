---
ms.date: 09/13/2016
ms.topic: reference
title: Utöka utdataobjekt
description: Utöka utdataobjekt
ms.openlocfilehash: 9fea476e3032002bd206609313581cc6373dfddc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652896"
---
# <a name="extending-output-objects"></a><span data-ttu-id="f72db-103">Utöka utdataobjekt</span><span class="sxs-lookup"><span data-stu-id="f72db-103">Extending Output Objects</span></span>

<span data-ttu-id="f72db-104">Du kan utöka .NET Framework objekt som returneras av cmdlets, Functions och scripts genom att använda typer filer (. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="f72db-104">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="f72db-105">Filtyper är XML-baserade filer som gör att du kan lägga till egenskaper och metoder i befintliga objekt.</span><span class="sxs-lookup"><span data-stu-id="f72db-105">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="f72db-106">Windows PowerShell tillhandahåller till exempel XML-filen Types.ps1, som lägger till element i flera befintliga .NET Framework objekt.</span><span class="sxs-lookup"><span data-stu-id="f72db-106">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="f72db-107">XML-filen Types.ps1finns i installations katalogen för Windows PowerShell ( `$pshome` ).</span><span class="sxs-lookup"><span data-stu-id="f72db-107">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="f72db-108">Du kan skapa en egen typ fil för att ytterligare utöka objekten eller för att utöka andra objekt.</span><span class="sxs-lookup"><span data-stu-id="f72db-108">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="f72db-109">När du utökar ett objekt med hjälp av en typ fil utökas alla instanser av objektet med de nya elementen.</span><span class="sxs-lookup"><span data-stu-id="f72db-109">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="f72db-110">Utöka system. Array-objektet</span><span class="sxs-lookup"><span data-stu-id="f72db-110">Extending the System.Array Object</span></span>

<span data-ttu-id="f72db-111">I följande exempel visas hur Windows PowerShell utökar [system. Array](/dotnet/api/System.Array) -objektet i Types.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="f72db-111">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="f72db-112">Som standard har [system. Array](/dotnet/api/System.Array) -objekt en `Length` egenskap som visar antalet objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="f72db-112">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="f72db-113">Men eftersom namnet "Length" inte tydligt beskriver egenskapen, lägger Windows PowerShell till `Count` egenskapen alias som visar samma värde som `Length` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f72db-113">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="f72db-114">Följande XML lägger till `Count` egenskapen i [system. mat ris](/dotnet/api/System.Array) typen.</span><span class="sxs-lookup"><span data-stu-id="f72db-114">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="f72db-115">Om du vill se den nya egenskapen alias använder du kommandot [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) på valfri matris, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="f72db-115">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="f72db-116">Kommandot returnerar följande resultat.</span><span class="sxs-lookup"><span data-stu-id="f72db-116">The command returns the following results.</span></span>

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

<span data-ttu-id="f72db-117">Du kan använda antingen `Count` egenskapen eller `Length` egenskapen för att avgöra hur många objekt som finns i en matris.</span><span class="sxs-lookup"><span data-stu-id="f72db-117">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="f72db-118">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f72db-118">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="f72db-119">Filer för anpassade typer</span><span class="sxs-lookup"><span data-stu-id="f72db-119">Custom Types Files</span></span>

<span data-ttu-id="f72db-120">Börja med att kopiera en befintlig typ fil för att skapa en anpassad typ.</span><span class="sxs-lookup"><span data-stu-id="f72db-120">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="f72db-121">Den nya filen kan ha vilket namn som helst, men den måste ha fil namns tillägget. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="f72db-121">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="f72db-122">När du kopierar filen kan du placera den nya filen i valfri katalog som är tillgänglig för Windows PowerShell, men det är användbart att placera filerna i installations katalogen för Windows PowerShell ( `$pshome` ) eller i en under katalog i installations katalogen.</span><span class="sxs-lookup"><span data-stu-id="f72db-122">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="f72db-123">Om du vill lägga till dina egna utökade typer i filen lägger du till ett typ element för varje objekt som du vill utöka.</span><span class="sxs-lookup"><span data-stu-id="f72db-123">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="f72db-124">I följande avsnitt finns exempel.</span><span class="sxs-lookup"><span data-stu-id="f72db-124">The following topics provide examples.</span></span>

- <span data-ttu-id="f72db-125">Mer information om hur du lägger till egenskaper och egenskaps uppsättningar finns i [utökade egenskaper](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="f72db-125">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="f72db-126">Mer information om hur du lägger till metoder finns i [utökade metoder](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f72db-126">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="f72db-127">Mer information om hur du lägger till medlems uppsättningar finns i [utökade medlems uppsättningar](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f72db-127">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="f72db-128">När du har definierat dina egna utökade typer kan du använda någon av följande metoder för att göra dina utökade objekt tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="f72db-128">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="f72db-129">Använd cmdleten [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) för att lägga till den nya filen för att göra din utökade typ av fil tillgänglig för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f72db-129">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="f72db-130">Om du vill att dina typer ska prioriteras över de typer som har definierats i andra typer av filer (inklusive Types.ps1XML-fil) använder du `PrependData` parametern för cmdleten [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .</span><span class="sxs-lookup"><span data-stu-id="f72db-130">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="f72db-131">Om du vill göra din utöknings bara fil tillgänglig för alla framtida sessioner lägger du till typ filen i en modul, exporterar den aktuella sessionen eller lägger till kommandot [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="f72db-131">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="f72db-132">Filer för signerings typer</span><span class="sxs-lookup"><span data-stu-id="f72db-132">Signing Types Files</span></span>

<span data-ttu-id="f72db-133">Filtyper ska signeras digitalt för att förhindra manipulering eftersom XML-filen kan innehålla skript block.</span><span class="sxs-lookup"><span data-stu-id="f72db-133">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="f72db-134">Mer information om hur du lägger till digitala signaturer finns [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="f72db-134">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="f72db-135">Se även</span><span class="sxs-lookup"><span data-stu-id="f72db-135">See Also</span></span>

[<span data-ttu-id="f72db-136">Definiera standard egenskaper för objekt</span><span class="sxs-lookup"><span data-stu-id="f72db-136">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="f72db-137">Definiera standardmetoder för objekt</span><span class="sxs-lookup"><span data-stu-id="f72db-137">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="f72db-138">Definiera standardmedlemsuppsättningar för objekt</span><span class="sxs-lookup"><span data-stu-id="f72db-138">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="f72db-139">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f72db-139">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
