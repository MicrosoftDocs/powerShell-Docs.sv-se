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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850598"
---
# <a name="defining-default-methods-for-objects"></a>Definiera standardmetoder för objekt

När du utökar .NET Framework-objekt kan du lägga till kod metoder och skript metoder till objekt. XML-filen som används för att definiera dessa metoder beskrivs i följande avsnitt.

> [!NOTE]
> Exemplen i följande avsnitt kommer från filen Types.ps1xml typer i installationskatalogen för Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Kod metoder

En metod som koden refererar till en statisk metod för ett .NET Framework-objekt.

I följande exempel visas den **ConvertLargeIntegerToInt64** metod har lagts till i den [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) typen. Den [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elementet definierar metoden utökade som en metod för kod. Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade metoden. Och [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) elementet anger metoden som statisk. (Du kan också lägga till den [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

En metod för skriptet definierar en metod som vars värde är utdata från ett skript. I följande exempel visas den **ConvertToDateTime** metod har lagts till i den [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) typen. Den [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elementet definierar metoden utökade som en metod för skriptet. Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade metoden. Och [skriptet](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) elementet anger det skript som genererar metoden värdet. (Du kan också lägga till den [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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