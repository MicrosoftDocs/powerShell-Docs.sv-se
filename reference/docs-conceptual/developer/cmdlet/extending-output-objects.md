---
title: Utökar utmatnings objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 12a826363221b8a7ce06245c787a7bd0529e42f8
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690896"
---
# <a name="extending-output-objects"></a><span data-ttu-id="b9e3b-102">Utöka utdataobjekt</span><span class="sxs-lookup"><span data-stu-id="b9e3b-102">Extending Output Objects</span></span>

<span data-ttu-id="b9e3b-103">Du kan utöka .NET Framework objekt som returneras av cmdlets, Functions och scripts genom att använda typer filer (. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="b9e3b-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="b9e3b-104">Filtyper är XML-baserade filer som gör att du kan lägga till egenskaper och metoder i befintliga objekt.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="b9e3b-105">Windows PowerShell tillhandahåller till exempel filen types. ps1xml, som lägger till element i flera befintliga .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="b9e3b-106">Filen types. ps1xml finns i installations katalogen för Windows PowerShell ( `$pshome` ).</span><span class="sxs-lookup"><span data-stu-id="b9e3b-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="b9e3b-107">Du kan skapa en egen typ fil för att ytterligare utöka objekten eller för att utöka andra objekt.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="b9e3b-108">När du utökar ett objekt med hjälp av en typ fil utökas alla instanser av objektet med de nya elementen.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="b9e3b-109">Utöka system. Array-objektet</span><span class="sxs-lookup"><span data-stu-id="b9e3b-109">Extending the System.Array Object</span></span>

<span data-ttu-id="b9e3b-110">I följande exempel visas hur Windows PowerShell utökar [system. Array](/dotnet/api/System.Array) -objektet i filen types. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="b9e3b-111">Som standard har [system. Array](/dotnet/api/System.Array) -objekt en `Length` egenskap som visar antalet objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="b9e3b-112">Men eftersom namnet "Length" inte tydligt beskriver egenskapen, lägger Windows PowerShell till `Count` egenskapen alias som visar samma värde som `Length` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="b9e3b-113">Följande XML lägger till `Count` egenskapen i [system. mat ris](/dotnet/api/System.Array) typen.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="b9e3b-114">Om du vill se den nya egenskapen alias använder du kommandot [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) på valfri matris, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="b9e3b-115">Kommandot returnerar följande resultat.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-115">The command returns the following results.</span></span>

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

<span data-ttu-id="b9e3b-116">Du kan använda antingen `Count` egenskapen eller `Length` egenskapen för att avgöra hur många objekt som finns i en matris.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="b9e3b-117">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="b9e3b-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="b9e3b-118">Filer för anpassade typer</span><span class="sxs-lookup"><span data-stu-id="b9e3b-118">Custom Types Files</span></span>

<span data-ttu-id="b9e3b-119">Börja med att kopiera en befintlig typ fil för att skapa en anpassad typ.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="b9e3b-120">Den nya filen kan ha vilket namn som helst, men den måste ha fil namns tillägget. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="b9e3b-121">När du kopierar filen kan du placera den nya filen i valfri katalog som är tillgänglig för Windows PowerShell, men det är användbart att placera filerna i installations katalogen för Windows PowerShell ( `$pshome` ) eller i en under katalog i installations katalogen.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="b9e3b-122">Om du vill lägga till dina egna utökade typer i filen lägger du till ett typ element för varje objekt som du vill utöka.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="b9e3b-123">I följande avsnitt finns exempel.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-123">The following topics provide examples.</span></span>

- <span data-ttu-id="b9e3b-124">Mer information om hur du lägger till egenskaper och egenskaps uppsättningar finns i [utökade egenskaper](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="b9e3b-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="b9e3b-125">Mer information om hur du lägger till metoder finns i [utökade metoder](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b9e3b-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="b9e3b-126">Mer information om hur du lägger till medlems uppsättningar finns i [utökade medlems uppsättningar](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b9e3b-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="b9e3b-127">När du har definierat dina egna utökade typer kan du använda någon av följande metoder för att göra dina utökade objekt tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="b9e3b-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="b9e3b-128">Använd cmdleten [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) för att lägga till den nya filen för att göra din utökade typ av fil tillgänglig för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="b9e3b-129">Om du vill att typerna ska prioriteras över de typer som har definierats i andra typer av filer (inklusive filen types. ps1xml) använder du `PrependData` parametern för cmdleten [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .</span><span class="sxs-lookup"><span data-stu-id="b9e3b-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="b9e3b-130">Om du vill göra din utöknings bara fil tillgänglig för alla framtida sessioner lägger du till typ filen i en modul, exporterar den aktuella sessionen eller lägger till kommandot [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="b9e3b-131">Filer för signerings typer</span><span class="sxs-lookup"><span data-stu-id="b9e3b-131">Signing Types Files</span></span>

<span data-ttu-id="b9e3b-132">Filtyper ska signeras digitalt för att förhindra manipulering eftersom XML-filen kan innehålla skript block.</span><span class="sxs-lookup"><span data-stu-id="b9e3b-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="b9e3b-133">Mer information om hur du lägger till digitala signaturer finns [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="b9e3b-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="b9e3b-134">Se även</span><span class="sxs-lookup"><span data-stu-id="b9e3b-134">See Also</span></span>

[<span data-ttu-id="b9e3b-135">Definiera standard egenskaper för objekt</span><span class="sxs-lookup"><span data-stu-id="b9e3b-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="b9e3b-136">Definiera standardmetoder för objekt</span><span class="sxs-lookup"><span data-stu-id="b9e3b-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="b9e3b-137">Definiera standardmedlemsuppsättningar för objekt</span><span class="sxs-lookup"><span data-stu-id="b9e3b-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="b9e3b-138">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="b9e3b-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
