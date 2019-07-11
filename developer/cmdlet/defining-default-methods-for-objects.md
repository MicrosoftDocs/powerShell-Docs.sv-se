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
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733973"
---
# <a name="defining-default-methods-for-objects"></a>Definiera standardmetoder för objekt

När du utökar .NET Framework-objekt kan du lägga till kod metoder och skript metoder till objekt. XML-filen som används för att definiera dessa metoder beskrivs i följande avsnitt.

> [!NOTE]
> Exemplen i följande avsnitt kommer från filen Types.ps1xml typer i installationskatalogen för Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Kod metoder

En metod som koden refererar till en statisk metod för ett .NET Framework-objekt.

I följande exempel visas den **ConvertLargeIntegerToInt64** metod har lagts till i den [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) typen. Den [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elementet definierar metoden utökade som en metod för kod. Den [namn](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elementet anger namnet på den utökade metoden. Och [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) elementet anger metoden som statisk. (Du kan också lägga till den [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element till medlemmarna i den [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>Skript-metoder

En metod för skriptet definierar en metod som vars värde är utdata från ett skript. I följande exempel visas den **ConvertToDateTime** metod har lagts till i den [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) typen. Den [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elementet definierar metoden utökade som en metod för skriptet. Den [namn](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elementet anger namnet på den utökade metoden. Och [skriptet](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elementet anger det skript som genererar metoden värdet. (Du kan också lägga till den [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element till medlemmarna i den [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)

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

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
