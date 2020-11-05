---
ms.date: 09/13/2016
ms.topic: reference
title: Definiera standardmetoder för objekt
description: Definiera standardmetoder för objekt
ms.openlocfilehash: c65ca91a7038f32d8c3ef62cfe7881e5ad4dba5a
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355535"
---
# <a name="defining-default-methods-for-objects"></a>Definiera standardmetoder för objekt

När du utökar .NET Framework objekt kan du lägga till kod metoder och skript metoder i objekten.
Den XML som används för att definiera dessa metoder beskrivs i följande avsnitt.

> [!NOTE]
> Exemplen i följande avsnitt är från `Types.ps1xml` typ filen i installations katalogen för Windows PowerShell ( `$PSHOME` ). Mer information finns i [About Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Kod metoder

En kod metod refererar till en statisk metod för ett .NET Framework-objekt.

I följande exempel läggs metoden **toString** till i den [System.Xml.Xmlnodtypen](/dotnet/api/System.Xml.XmlNode) . [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -elementet definierar den utökade metoden som en Code-metod. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) anger namnet på den utökade metoden. Och [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference#System_Management_Automation_PSCodeMethod_CodeReference) -elementet anger den statiska metoden. Du kan också lägga till elementet [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) i medlemmarna i [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) -elementet.

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>Skript metoder

En skript metod definierar en metod vars värde är utdata från ett skript. I följande exempel läggs **ConvertToDateTime** -metoden till i typen [system. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) -elementet definierar den utökade metoden som en skript metod. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) anger namnet på den utökade metoden. Och [skript](/dotnet/api/system.management.automation.psscriptmethod.script#System_Management_Automation_PSScriptMethod_Script) elementet anger det skript som genererar metod svärdet. Du kan också lägga till elementet [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) i medlemmarna i [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) -elementet.

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
