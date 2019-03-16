---
title: Utöka egenskaper för objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 496e363b041194563d46c09eee67a12055bb54b0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057305"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="9ab3b-102">Utöka egenskaper för objekt</span><span class="sxs-lookup"><span data-stu-id="9ab3b-102">Extending Properties for Objects</span></span>

<span data-ttu-id="9ab3b-103">När du utökar .NET Framework-objekt du kan lägga till alias egenskaper, kodegenskaper, Observera egenskaper, skriptegenskaper och egenskapsuppsättningar objekten.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="9ab3b-104">XML-filen som används för att definiera egenskaperna beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="9ab3b-105">Exemplen i följande avsnitt kommer från filen standard Types.ps1xml typer i installationskatalogen för Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="9ab3b-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="9ab3b-106">Alias-egenskaper</span><span class="sxs-lookup"><span data-stu-id="9ab3b-106">Alias Properties</span></span>

<span data-ttu-id="9ab3b-107">Ett nytt namn för en befintlig egenskap definierar en alias-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="9ab3b-108">I följande exempel visas den `Count` egenskapen har lagts till i den [System.Array? Displayproperty = Fullname](/dotnet/api/System.Array) typen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="9ab3b-109">Den [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) elementet definierar den utökade egenskapen som ett alias-egenskap.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="9ab3b-110">Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger ett nytt namn.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="9ab3b-111">Och [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) elementet anger den befintliga egenskap som refereras av alias.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="9ab3b-112">(Du kan också lägga till den [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="9ab3b-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="9ab3b-113">Kodegenskaper för</span><span class="sxs-lookup"><span data-stu-id="9ab3b-113">Code Properties</span></span>

<span data-ttu-id="9ab3b-114">En egenskap för felkod refererar till en statisk egenskap för ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="9ab3b-115">I följande exempel visas den `Node` egenskapen har lagts till i den [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) typen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="9ab3b-116">Den [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elementet definierar den utökade egenskapen som en egenskap för felkod.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="9ab3b-117">Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="9ab3b-118">Och [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) elementet definierar den statiska metoden som refereras av den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="9ab3b-119">(Du kan också lägga till den [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="9ab3b-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="9ab3b-120">Obs egenskaper</span><span class="sxs-lookup"><span data-stu-id="9ab3b-120">Note Properties</span></span>

<span data-ttu-id="9ab3b-121">En Obs egenskapen definierar en egenskap som har ett statiskt värde.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="9ab3b-122">I följande exempel visas den `Status` egenskapen (vars värde är alltid ”lyckades”) har lagts till i den [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) typen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="9ab3b-123">Den [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elementet definierar den utökade egenskapen som en anteckning-egenskap; den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade egenskapen; och [värdet](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element Anger det statiska värdet för den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="9ab3b-124">(Den [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element kan också läggas till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="9ab3b-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="9ab3b-125">Skriptegenskaper</span><span class="sxs-lookup"><span data-stu-id="9ab3b-125">Script Properties</span></span>

<span data-ttu-id="9ab3b-126">En egenskap för skriptet definierar en egenskap vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="9ab3b-127">I följande exempel visas den `VersionInfo` egenskapen har lagts till i den [System.IO.FileInfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) typen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-127">In the following example, the `VersionInfo` property is added to the [System.IO.FileInfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="9ab3b-128">Den [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elementet definierar den utökade egenskapen som en egenskap för skriptet.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="9ab3b-129">Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="9ab3b-130">Och [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elementet anger det skript som genererar egenskapsvärdet.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="9ab3b-131">(Du kan också lägga till den [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="9ab3b-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="9ab3b-132">Egenskapsuppsättningar</span><span class="sxs-lookup"><span data-stu-id="9ab3b-132">Property Sets</span></span>

<span data-ttu-id="9ab3b-133">En egenskapsuppsättning definierar en grupp av utökade egenskaper som kan refereras av namnet på uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="9ab3b-134">Till exempel den `Property` -parametern för den [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) ange en specifik egenskapsuppsättning som ska visas.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="9ab3b-135">När du anger en egenskapsuppsättning visas endast de egenskaper som tillhör uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="9ab3b-136">Det finns ingen begränsning för hur många uppsättningar med egenskaper som kan definieras för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-136">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="9ab3b-137">Men måste de egenskaperna som används för att definiera standardegenskaperna för visning av ett objekt anges inom PSStandardMembers uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-137">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="9ab3b-138">I filen Types.ps1xml typer är standard set egenskapsnamn DefaultDisplayProperty, DefaultDisplayPropertySet och DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-138">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="9ab3b-139">Eventuella ytterligare egenskaper som du lägger till PSStandardMembers uppsättningen ignoreras.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-139">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="9ab3b-140">I följande exempel egenskapsuppsättning DefaultDisplayPropertySet läggs till PSStandardMembers uppsättningen av den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) typen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-140">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="9ab3b-141">Den [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elementet definierar gruppen egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-141">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="9ab3b-142">Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på egenskapsuppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-142">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="9ab3b-143">Och [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) elementet anger egenskaperna för uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="9ab3b-143">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="9ab3b-144">(Du kan också lägga till den [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element till medlemmarna i den [typ](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span><span class="sxs-lookup"><span data-stu-id="9ab3b-144">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9ab3b-145">Se även</span><span class="sxs-lookup"><span data-stu-id="9ab3b-145">See Also</span></span>

[<span data-ttu-id="9ab3b-146">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9ab3b-146">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
