---
title: Utöka egenskaper för objekt | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355540"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="b2094-102">Utöka egenskaper för objekt</span><span class="sxs-lookup"><span data-stu-id="b2094-102">Extending Properties for Objects</span></span>

<span data-ttu-id="b2094-103">När du utökar .NET Framework objekt kan du lägga till egenskaper för alias, kod egenskaper, antecknings egenskaper, skript egenskaper och egenskaps uppsättningar för objekten.</span><span class="sxs-lookup"><span data-stu-id="b2094-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="b2094-104">XML-filen som definierar dessa egenskaper beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="b2094-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="b2094-105">Exemplen i följande avsnitt är från standard `Types.ps1xml`-filtypen i installations katalogen för PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="b2094-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="b2094-106">Mer information finns i [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="b2094-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="b2094-107">Egenskaper för alias</span><span class="sxs-lookup"><span data-stu-id="b2094-107">Alias properties</span></span>

<span data-ttu-id="b2094-108">En alias-egenskap definierar ett nytt namn för en befintlig egenskap.</span><span class="sxs-lookup"><span data-stu-id="b2094-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="b2094-109">I följande exempel läggs **Count** -egenskapen till i [system. mat ris](/dotnet/api/System.Array) typen.</span><span class="sxs-lookup"><span data-stu-id="b2094-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="b2094-110">[AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -elementet definierar den utökade egenskapen som en alias-egenskap.</span><span class="sxs-lookup"><span data-stu-id="b2094-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="b2094-111">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger det nya namnet.</span><span class="sxs-lookup"><span data-stu-id="b2094-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="b2094-112">Och [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) -elementet anger den befintliga egenskapen som aliaset refererar till.</span><span class="sxs-lookup"><span data-stu-id="b2094-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="b2094-113">Du kan också lägga till elementet `AliasProperty` till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="b2094-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="b2094-114">Kod egenskaper</span><span class="sxs-lookup"><span data-stu-id="b2094-114">Code properties</span></span>

<span data-ttu-id="b2094-115">En kod egenskap refererar till en statisk egenskap för ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="b2094-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="b2094-116">I följande exempel läggs egenskapen **mode** till i typen [system. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="b2094-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="b2094-117">[CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -elementet definierar den utökade egenskapen som en kod egenskap.</span><span class="sxs-lookup"><span data-stu-id="b2094-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="b2094-118">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b2094-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="b2094-119">Och [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) -elementet definierar den statiska metoden som den utökade egenskapen refererar till.</span><span class="sxs-lookup"><span data-stu-id="b2094-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="b2094-120">Du kan också lägga till elementet `CodeProperty` till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="b2094-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="b2094-121">Antecknings egenskaper</span><span class="sxs-lookup"><span data-stu-id="b2094-121">Note properties</span></span>

<span data-ttu-id="b2094-122">En antecknings egenskap definierar en egenskap med ett statiskt värde.</span><span class="sxs-lookup"><span data-stu-id="b2094-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="b2094-123">I följande exempel läggs **status** egenskapen, vars värde alltid **lyckas**, till i [system. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) -typen.</span><span class="sxs-lookup"><span data-stu-id="b2094-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="b2094-124">[NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -elementet definierar den utökade egenskapen som en antecknings egenskap.</span><span class="sxs-lookup"><span data-stu-id="b2094-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="b2094-125">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b2094-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="b2094-126">[Värdet](/dotnet/api/system.management.automation.psnoteproperty.value) -elementet anger det statiska värdet för den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b2094-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="b2094-127">Du kan också lägga till elementet `NoteProperty` i medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="b2094-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a><span data-ttu-id="b2094-128">Skript egenskaper</span><span class="sxs-lookup"><span data-stu-id="b2094-128">Script properties</span></span>

<span data-ttu-id="b2094-129">En skript egenskap definierar en egenskap vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="b2094-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="b2094-130">I följande exempel läggs egenskapen **VersionInfo** till i typen [system. io. fileinfo](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="b2094-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="b2094-131">[ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -elementet definierar den utökade egenskapen som en skript egenskap.</span><span class="sxs-lookup"><span data-stu-id="b2094-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="b2094-132">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b2094-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="b2094-133">Och [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) -elementet anger det skript som genererar egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="b2094-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="b2094-134">Du kan också lägga till elementet `ScriptProperty` till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="b2094-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a><span data-ttu-id="b2094-135">Egenskaps uppsättningar</span><span class="sxs-lookup"><span data-stu-id="b2094-135">Property sets</span></span>

<span data-ttu-id="b2094-136">En egenskaps uppsättning definierar en grupp utökade egenskaper som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="b2094-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="b2094-137">**Egenskaps** parametern [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
 kan till exempel ange en speciell egenskaps uppsättning som ska visas.</span><span class="sxs-lookup"><span data-stu-id="b2094-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="b2094-138">När en egenskaps uppsättning anges visas endast de egenskaper som tillhör uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b2094-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="b2094-139">Det finns ingen begränsning för antalet egenskaps uppsättningar som kan definieras för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="b2094-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="b2094-140">Egenskaps uppsättningarna som används för att definiera standard visnings egenskaperna för ett objekt måste dock anges i **PSStandardMembers** -medlems uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b2094-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="b2094-141">I filen `Types.ps1xml` skriver du standard namnen för egenskaps uppsättningar, inklusive **DefaultDisplayProperty**, **DefaultDisplayPropertySet**och **DefaultKeyPropertySet**.</span><span class="sxs-lookup"><span data-stu-id="b2094-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="b2094-142">Eventuella ytterligare egenskaps uppsättningar som du lägger till i **PSStandardMembers** -medlems uppsättningen ignoreras.</span><span class="sxs-lookup"><span data-stu-id="b2094-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="b2094-143">I följande exempel läggs egenskaps uppsättningen **DefaultDisplayPropertySet** till i **PSStandardMembers** -medlems uppsättningen för [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -typen.</span><span class="sxs-lookup"><span data-stu-id="b2094-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="b2094-144">[PropertySet](/dotnet/api/system.management.automation.pspropertyset) -elementet definierar gruppen med egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b2094-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="b2094-145">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på egenskaps uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b2094-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="b2094-146">Och [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) -elementet anger egenskaperna för uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b2094-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="b2094-147">Du kan också lägga till elementet `PropertySet` till medlemmarna i [typ](/dotnet/api/system.management.automation.pstypename) elementet.</span><span class="sxs-lookup"><span data-stu-id="b2094-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="b2094-148">Se även</span><span class="sxs-lookup"><span data-stu-id="b2094-148">See also</span></span>

[<span data-ttu-id="b2094-149">Om types. ps1xml</span><span class="sxs-lookup"><span data-stu-id="b2094-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="b2094-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="b2094-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="b2094-151">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="b2094-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
