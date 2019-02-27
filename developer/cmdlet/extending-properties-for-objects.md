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
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845782"
---
# <a name="extending-properties-for-objects"></a>Utöka egenskaper för objekt

När du utökar .NET Framework-objekt du kan lägga till alias egenskaper, kodegenskaper, Observera egenskaper, skriptegenskaper och egenskapsuppsättningar objekten. XML-filen som används för att definiera egenskaperna beskrivs i följande avsnitt.

> [!NOTE]
> Exemplen i följande avsnitt kommer från filen standard Types.ps1xml typer i installationskatalogen för Windows PowerShell (`$pshome`).

## <a name="alias-properties"></a>Alias-egenskaper

Ett nytt namn för en befintlig egenskap definierar en alias-egenskapen.

I följande exempel visas den `Count` egenskapen har lagts till i den [System.Array? Displayproperty = Fullname](/dotnet/api/System.Array) typen. Den [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) elementet definierar den utökade egenskapen som ett alias-egenskap. Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger ett nytt namn. Och [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) elementet anger den befintliga egenskap som refereras av alias. (Du kan också lägga till den [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

## <a name="code-properties"></a>Kodegenskaper för

En egenskap för felkod refererar till en statisk egenskap för ett .NET Framework-objekt.

I följande exempel visas den `Node` egenskapen har lagts till i den [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) typen. Den [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elementet definierar den utökade egenskapen som en egenskap för felkod. Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade egenskapen. Och [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) elementet definierar den statiska metoden som refereras av den utökade egenskapen. (Du kan också lägga till den [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

## <a name="note-properties"></a>Obs egenskaper

En Obs egenskapen definierar en egenskap som har ett statiskt värde.

I följande exempel visas den `Status` egenskapen (vars värde är alltid ”lyckades”) har lagts till i den [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) typen. Den [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elementet definierar den utökade egenskapen som en anteckning-egenskap; den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade egenskapen; och [värdet](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element Anger det statiska värdet för den utökade egenskapen. (Den [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element kan också läggas till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

## <a name="script-properties"></a>Skriptegenskaper

En egenskap för skriptet definierar en egenskap vars värde är utdata från ett skript.

I följande exempel visas den `VersionInfo` egenskapen har lagts till i den [System.IO.Fileinfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) typen. Den [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elementet definierar den utökade egenskapen som en egenskap för skriptet. Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade egenskapen. Och [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elementet anger det skript som genererar egenskapsvärdet. (Du kan också lägga till den [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

## <a name="property-sets"></a>Egenskapsuppsättningar

En egenskapsuppsättning definierar en grupp av utökade egenskaper som kan refereras av namnet på uppsättningen. Till exempel den `Property` -parametern för den [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) ange en specifik egenskapsuppsättning som ska visas. När du anger en egenskapsuppsättning visas endast de egenskaper som tillhör uppsättningen.
En egenskapsuppsättning definierar en grupp av utökade egenskaper som kan refereras av namnet på uppsättningen. Till exempel den `Property` -parametern för den [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) ange en specifik egenskapsuppsättning som ska visas. När du anger en egenskapsuppsättning visas endast de egenskaper som tillhör uppsättningen.

Det finns ingen begränsning för hur många uppsättningar med egenskaper som kan definieras för ett objekt. Men måste de egenskaperna som används för att definiera standardegenskaperna för visning av ett objekt anges inom PSStandardMembers uppsättningen. I filen Types.ps1xml typer är standard set egenskapsnamn DefaultDisplayProperty, DefaultDisplayPropertySet och DefaultKeyPropertySet. Eventuella ytterligare egenskaper som du lägger till PSStandardMembers uppsättningen ignoreras.

I följande exempel egenskapsuppsättning DefaultDisplayPropertySet läggs till PSStandardMembers uppsättningen av den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) typen. Den [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elementet definierar gruppen egenskaper. Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på egenskapsuppsättningen. Och [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) elementet anger egenskaperna för uppsättningen. (Du kan också lägga till den [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element till medlemmarna i den [typ](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)

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

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
