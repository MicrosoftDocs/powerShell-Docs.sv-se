---
title: Utöka egenskaper för objekt | Microsoft Docs
ms.date: 08/21/2019
ms.openlocfilehash: acd20c7e2b6ef84a9c932538eb8e167d68c8a660
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784307"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="f90e0-102">Utöka egenskaper för objekt</span><span class="sxs-lookup"><span data-stu-id="f90e0-102">Extending Properties for Objects</span></span>

<span data-ttu-id="f90e0-103">När du utökar .NET Framework objekt kan du lägga till egenskaper för alias, kod egenskaper, antecknings egenskaper, skript egenskaper och egenskaps uppsättningar för objekten.</span><span class="sxs-lookup"><span data-stu-id="f90e0-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="f90e0-104">XML-filen som definierar dessa egenskaper beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="f90e0-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="f90e0-105">Exemplen i följande avsnitt är från standard `Types.ps1xml` fil filen i installations katalogen för PowerShell ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="f90e0-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="f90e0-106">Mer information finns i [About Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="f90e0-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="f90e0-107">Egenskaper för alias</span><span class="sxs-lookup"><span data-stu-id="f90e0-107">Alias properties</span></span>

<span data-ttu-id="f90e0-108">En alias-egenskap definierar ett nytt namn för en befintlig egenskap.</span><span class="sxs-lookup"><span data-stu-id="f90e0-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="f90e0-109">I följande exempel läggs **Count** -egenskapen till i [system. mat ris](/dotnet/api/System.Array) typen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="f90e0-110">[AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -elementet definierar den utökade egenskapen som en alias-egenskap.</span><span class="sxs-lookup"><span data-stu-id="f90e0-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="f90e0-111">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger det nya namnet.</span><span class="sxs-lookup"><span data-stu-id="f90e0-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="f90e0-112">Och [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) -elementet anger den befintliga egenskapen som aliaset refererar till.</span><span class="sxs-lookup"><span data-stu-id="f90e0-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="f90e0-113">Du kan också lägga till `AliasProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="f90e0-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="f90e0-114">Kod egenskaper</span><span class="sxs-lookup"><span data-stu-id="f90e0-114">Code properties</span></span>

<span data-ttu-id="f90e0-115">En kod egenskap refererar till en statisk egenskap för ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="f90e0-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="f90e0-116">I följande exempel läggs egenskapen **mode** till i typen [system. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="f90e0-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="f90e0-117">[CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -elementet definierar den utökade egenskapen som en kod egenskap.</span><span class="sxs-lookup"><span data-stu-id="f90e0-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="f90e0-118">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="f90e0-119">Och [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) -elementet definierar den statiska metoden som den utökade egenskapen refererar till.</span><span class="sxs-lookup"><span data-stu-id="f90e0-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="f90e0-120">Du kan också lägga till `CodeProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="f90e0-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="f90e0-121">Antecknings egenskaper</span><span class="sxs-lookup"><span data-stu-id="f90e0-121">Note properties</span></span>

<span data-ttu-id="f90e0-122">En antecknings egenskap definierar en egenskap med ett statiskt värde.</span><span class="sxs-lookup"><span data-stu-id="f90e0-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="f90e0-123">I följande exempel läggs **status** egenskapen, vars värde alltid **lyckas**, till i [system. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) -typen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="f90e0-124">[NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -elementet definierar den utökade egenskapen som en antecknings egenskap.</span><span class="sxs-lookup"><span data-stu-id="f90e0-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="f90e0-125">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="f90e0-126">[Värdet](/dotnet/api/system.management.automation.psnoteproperty.value) -elementet anger det statiska värdet för den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="f90e0-127">`NoteProperty`Elementet kan också läggas till i medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="f90e0-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="f90e0-128">Skript egenskaper</span><span class="sxs-lookup"><span data-stu-id="f90e0-128">Script properties</span></span>

<span data-ttu-id="f90e0-129">En skript egenskap definierar en egenskap vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="f90e0-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="f90e0-130">I följande exempel läggs egenskapen **VersionInfo** till i typen [system. io. fileinfo](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="f90e0-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="f90e0-131">[ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -elementet definierar den utökade egenskapen som en skript egenskap.</span><span class="sxs-lookup"><span data-stu-id="f90e0-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="f90e0-132">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="f90e0-133">Och [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) -elementet anger det skript som genererar egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="f90e0-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="f90e0-134">Du kan också lägga till `ScriptProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.</span><span class="sxs-lookup"><span data-stu-id="f90e0-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="f90e0-135">Egenskaps uppsättningar</span><span class="sxs-lookup"><span data-stu-id="f90e0-135">Property sets</span></span>

<span data-ttu-id="f90e0-136">En egenskaps uppsättning definierar en grupp utökade egenskaper som kan refereras till i uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="f90e0-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="f90e0-137">Egenskaps parametern [format-tabell](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) 
 **Property** kan till exempel ange att en speciell egenskaps uppsättning ska visas.</span><span class="sxs-lookup"><span data-stu-id="f90e0-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="f90e0-138">När en egenskaps uppsättning anges visas endast de egenskaper som tillhör uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="f90e0-139">Det finns ingen begränsning för antalet egenskaps uppsättningar som kan definieras för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="f90e0-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="f90e0-140">Egenskaps uppsättningarna som används för att definiera standard visnings egenskaperna för ett objekt måste dock anges i **PSStandardMembers** -medlems uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="f90e0-141">I `Types.ps1xml` typ filen inkluderar standard egenskaperna för egenskaps uppsättning namn **DefaultDisplayProperty**, **DefaultDisplayPropertySet**och **DefaultKeyPropertySet**.</span><span class="sxs-lookup"><span data-stu-id="f90e0-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="f90e0-142">Eventuella ytterligare egenskaps uppsättningar som du lägger till i **PSStandardMembers** -medlems uppsättningen ignoreras.</span><span class="sxs-lookup"><span data-stu-id="f90e0-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="f90e0-143">I följande exempel läggs egenskaps uppsättningen **DefaultDisplayPropertySet** till i **PSStandardMembers** -medlems uppsättningen för [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -typen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="f90e0-144">[PropertySet](/dotnet/api/system.management.automation.pspropertyset) -elementet definierar gruppen med egenskaper.</span><span class="sxs-lookup"><span data-stu-id="f90e0-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="f90e0-145">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på egenskaps uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="f90e0-146">Och [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) -elementet anger egenskaperna för uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f90e0-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="f90e0-147">Du kan också lägga till `PropertySet` elementet i medlemmar av [typen](/dotnet/api/system.management.automation.pstypename) element.</span><span class="sxs-lookup"><span data-stu-id="f90e0-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f90e0-148">Se även</span><span class="sxs-lookup"><span data-stu-id="f90e0-148">See also</span></span>

[<span data-ttu-id="f90e0-149">Om Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="f90e0-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="f90e0-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="f90e0-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="f90e0-151">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f90e0-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
