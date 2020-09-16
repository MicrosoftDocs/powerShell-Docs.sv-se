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
# <a name="extending-properties-for-objects"></a>Utöka egenskaper för objekt

När du utökar .NET Framework objekt kan du lägga till egenskaper för alias, kod egenskaper, antecknings egenskaper, skript egenskaper och egenskaps uppsättningar för objekten. XML-filen som definierar dessa egenskaper beskrivs i följande avsnitt.

> [!NOTE]
> Exemplen i följande avsnitt är från standard `Types.ps1xml` fil filen i installations katalogen för PowerShell ( `$PSHOME` ). Mer information finns i [About Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="alias-properties"></a>Egenskaper för alias

En alias-egenskap definierar ett nytt namn för en befintlig egenskap.

I följande exempel läggs **Count** -egenskapen till i [system. mat ris](/dotnet/api/System.Array) typen. [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -elementet definierar den utökade egenskapen som en alias-egenskap. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger det nya namnet. Och [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) -elementet anger den befintliga egenskapen som aliaset refererar till. Du kan också lägga till `AliasProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.

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

## <a name="code-properties"></a>Kod egenskaper

En kod egenskap refererar till en statisk egenskap för ett .NET Framework-objekt.

I följande exempel läggs egenskapen **mode** till i typen [system. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -elementet definierar den utökade egenskapen som en kod egenskap. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen. Och [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) -elementet definierar den statiska metoden som den utökade egenskapen refererar till. Du kan också lägga till `CodeProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.

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

## <a name="note-properties"></a>Antecknings egenskaper

En antecknings egenskap definierar en egenskap med ett statiskt värde.

I följande exempel läggs **status** egenskapen, vars värde alltid **lyckas**, till i [system. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) -typen. [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -elementet definierar den utökade egenskapen som en antecknings egenskap. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen. [Värdet](/dotnet/api/system.management.automation.psnoteproperty.value) -elementet anger det statiska värdet för den utökade egenskapen. `NoteProperty`Elementet kan också läggas till i medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.

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

## <a name="script-properties"></a>Skript egenskaper

En skript egenskap definierar en egenskap vars värde är utdata från ett skript.

I följande exempel läggs egenskapen **VersionInfo** till i typen [system. io. fileinfo](/dotnet/api/System.IO.FileInfo) . [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -elementet definierar den utökade egenskapen som en skript egenskap. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på den utökade egenskapen. Och [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) -elementet anger det skript som genererar egenskap svärdet. Du kan också lägga till `ScriptProperty` elementet till medlemmarna i [MemberSet](/dotnet/api/system.management.automation.psmemberset) -elementet.

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

## <a name="property-sets"></a>Egenskaps uppsättningar

En egenskaps uppsättning definierar en grupp utökade egenskaper som kan refereras till i uppsättningens namn.
Egenskaps parametern [format-tabell](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) 
 **Property** kan till exempel ange att en speciell egenskaps uppsättning ska visas. När en egenskaps uppsättning anges visas endast de egenskaper som tillhör uppsättningen.

Det finns ingen begränsning för antalet egenskaps uppsättningar som kan definieras för ett objekt. Egenskaps uppsättningarna som används för att definiera standard visnings egenskaperna för ett objekt måste dock anges i **PSStandardMembers** -medlems uppsättningen. I `Types.ps1xml` typ filen inkluderar standard egenskaperna för egenskaps uppsättning namn **DefaultDisplayProperty**, **DefaultDisplayPropertySet**och **DefaultKeyPropertySet**. Eventuella ytterligare egenskaps uppsättningar som du lägger till i **PSStandardMembers** -medlems uppsättningen ignoreras.

I följande exempel läggs egenskaps uppsättningen **DefaultDisplayPropertySet** till i **PSStandardMembers** -medlems uppsättningen för [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -typen. [PropertySet](/dotnet/api/system.management.automation.pspropertyset) -elementet definierar gruppen med egenskaper. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name) anger namnet på egenskaps uppsättningen. Och [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) -elementet anger egenskaperna för uppsättningen. Du kan också lägga till `PropertySet` elementet i medlemmar av [typen](/dotnet/api/system.management.automation.pstypename) element.

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

## <a name="see-also"></a>Se även

[Om Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
