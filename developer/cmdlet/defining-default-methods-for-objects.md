---
title: Definiera standard metoder för objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215289"
---
# <a name="defining-default-methods-for-objects"></a>Definiera standardmetoder för objekt

När du utökar .NET Framework objekt kan du lägga till kod metoder och skript metoder i objekten.
Den XML som används för att definiera dessa metoder beskrivs i följande avsnitt.

> [!NOTE]
> Exemplen i följande avsnitt är från `Types.ps1xml` typ filen i installations katalogen för Windows PowerShell (`$PSHOME`). Mer information finns i [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Kod metoder

En kod metod refererar till en statisk metod för ett .NET Framework-objekt.

I följande exempel läggs metoden **toString** till i typen [system. xml. XmlNode](/dotnet/api/System.Xml.XmlNode) . [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -elementet definierar den utökade metoden som en Code-metod. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) anger namnet på den utökade metoden. Och [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) -elementet anger den statiska metoden. Du kan också lägga till elementet [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) i medlemmarna i [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) -elementet.

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

En skript metod definierar en metod vars värde är utdata från ett skript. I följande exempel läggs **ConvertToDateTime** -metoden till i typen [system. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) -elementet definierar den utökade metoden som en skript metod. Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) anger namnet på den utökade metoden. Och [skript](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elementet anger det skript som genererar metod svärdet. Du kan också lägga till elementet [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) i medlemmarna i [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) -elementet.

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
