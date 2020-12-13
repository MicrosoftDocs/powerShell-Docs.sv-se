---
ms.date: 08/21/2019
ms.topic: reference
title: Utöka egenskaper för objekt
description: Utöka egenskaper för objekt
ms.openlocfilehash: 37803d9fd87319204565c2abde62f269744481b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652888"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="5e1ff-103">Utöka egenskaper för objekt</span><span class="sxs-lookup"><span data-stu-id="5e1ff-103">Extending Properties for Objects</span></span>

<span data-ttu-id="5e1ff-104">När du utökar .NET Framework objekt kan du lägga till egenskaper för alias, kod egenskaper, antecknings egenskaper, skript egenskaper och egenskaps uppsättningar för objekten.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-104">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="5e1ff-105">XML-filen som definierar dessa egenskaper beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-105">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="5e1ff-106">Exemplen i följande avsnitt är från standard `Types.ps1xml` fil filen i installations katalogen för PowerShell ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="5e1ff-106">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="5e1ff-107">Mer information finns i [About Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="5e1ff-107">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="5e1ff-108">Egenskaper för alias</span><span class="sxs-lookup"><span data-stu-id="5e1ff-108">Alias properties</span></span>

<span data-ttu-id="5e1ff-109">En alias-egenskap definierar ett nytt namn för en befintlig egenskap.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-109">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="5e1ff-110">I följande exempel läggs **Count** -egenskapen till i [system. mat ris](/dotnet/api/System.Array) typen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-110">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="5e1ff-111">[AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -elementet definierar den utökade egenskapen som en alias-egenskap.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-111">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="5e1ff-112">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger det nya namnet.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-112">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="5e1ff-113">Och [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) -elementet anger den befintliga egenskapen som aliaset refererar till.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-113">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="5e1ff-114">Du kan också lägga till `AliasProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-114">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="5e1ff-115">Kod egenskaper</span><span class="sxs-lookup"><span data-stu-id="5e1ff-115">Code properties</span></span>

<span data-ttu-id="5e1ff-116">En kod egenskap refererar till en statisk egenskap för ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-116">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="5e1ff-117">I följande exempel läggs egenskapen **mode** till i typen [system. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="5e1ff-117">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="5e1ff-118">[CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -elementet definierar den utökade egenskapen som en kod egenskap.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-118">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="5e1ff-119">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-119">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="5e1ff-120">Och [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) -elementet definierar den statiska metoden som den utökade egenskapen refererar till.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-120">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="5e1ff-121">Du kan också lägga till `CodeProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-121">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="5e1ff-122">Antecknings egenskaper</span><span class="sxs-lookup"><span data-stu-id="5e1ff-122">Note properties</span></span>

<span data-ttu-id="5e1ff-123">En antecknings egenskap definierar en egenskap med ett statiskt värde.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-123">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="5e1ff-124">I följande exempel läggs **status** egenskapen, vars värde alltid **lyckas**, till i [system. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) -typen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-124">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="5e1ff-125">[NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -elementet definierar den utökade egenskapen som en antecknings egenskap.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-125">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="5e1ff-126">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-126">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="5e1ff-127">[Värdet](/dotnet/api/system.management.automation.psnoteproperty.value) -elementet anger det statiska värdet för den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-127">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="5e1ff-128">`NoteProperty`Elementet kan också läggas till i medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-128">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="5e1ff-129">Skript egenskaper</span><span class="sxs-lookup"><span data-stu-id="5e1ff-129">Script properties</span></span>

<span data-ttu-id="5e1ff-130">En skript egenskap definierar en egenskap vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-130">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="5e1ff-131">I följande exempel läggs egenskapen **VersionInfo** till i typen [system. io. fileinfo](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="5e1ff-131">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="5e1ff-132">[ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -elementet definierar den utökade egenskapen som en skript egenskap.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-132">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="5e1ff-133">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-133">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="5e1ff-134">Och [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) -elementet anger det skript som genererar egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-134">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="5e1ff-135">Du kan också lägga till `ScriptProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-135">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="5e1ff-136">Egenskaps uppsättningar</span><span class="sxs-lookup"><span data-stu-id="5e1ff-136">Property sets</span></span>

<span data-ttu-id="5e1ff-137">En egenskaps uppsättning definierar en grupp utökade egenskaper som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-137">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="5e1ff-138">Egenskaps parametern [format-tabell](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) 
  kan till exempel ange att en speciell egenskaps uppsättning ska visas.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-138">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="5e1ff-139">När en egenskaps uppsättning anges visas endast de egenskaper som tillhör uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-139">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="5e1ff-140">Det finns ingen begränsning för antalet egenskaps uppsättningar som kan definieras för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-140">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="5e1ff-141">Egenskaps uppsättningarna som används för att definiera standard visnings egenskaperna för ett objekt måste dock anges i **PSStandardMembers** -medlems uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-141">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="5e1ff-142">I `Types.ps1xml` typ filen inkluderar standard egenskaperna för egenskaps uppsättning namn **DefaultDisplayProperty**, **DefaultDisplayPropertySet** och **DefaultKeyPropertySet**.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-142">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="5e1ff-143">Eventuella ytterligare egenskaps uppsättningar som du lägger till i **PSStandardMembers** -medlems uppsättningen ignoreras.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-143">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="5e1ff-144">I följande exempel läggs egenskaps uppsättningen **DefaultDisplayPropertySet** till i **PSStandardMembers** -medlems uppsättningen för [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -typen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-144">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="5e1ff-145">[PropertySet](/dotnet/api/system.management.automation.pspropertyset) -elementet definierar gruppen med egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-145">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="5e1ff-146">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på egenskaps uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-146">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="5e1ff-147">Och [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) -elementet anger egenskaperna för uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-147">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="5e1ff-148">Du kan också lägga till `PropertySet` elementet i medlemmar av [typen](/dotnet/api/system.management.automation.pstypename) element.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-148">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5e1ff-149">Se även</span><span class="sxs-lookup"><span data-stu-id="5e1ff-149">See also</span></span>

[<span data-ttu-id="5e1ff-150">Om Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="5e1ff-150">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="5e1ff-151">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="5e1ff-151">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="5e1ff-152">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="5e1ff-152">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
