---
title: Cmdlet-klass deklaration | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.openlocfilehash: 96ce8144795346b6f46878ee6163ce69cdb1799a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784511"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet-klassdeklaration

En Microsoft .NET Framework-klass deklareras som en cmdlet genom att ange **cmdlet** -attributet som metadata för klassen. ( **Cmdlet** -attributet är det enda obligatoriska attributet för alla cmdletar).
När du anger **cmdlet** -attributet måste du ange verb-och-Substantiv-paret som identifierar cmdleten för användaren. Och du måste beskriva de Windows PowerShell-funktioner som stöds av cmdlet: en. Mer information om den deklarationssyntax som används för att ange **cmdlet** -attributet finns i deklaration av [cmdlet-attribut](./cmdlet-attribute-declaration.md).

> [!NOTE]
> **Cmdlet** -attributet definieras av klassen [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Egenskaperna för den här klassen motsvarar de deklarations parametrar som används när du deklarerar attributet.

## <a name="nouns"></a>Substantiv

Substantiv för cmdleten anger de resurser som cmdleten fungerar på. Substantivet särskiljer dina cmdletar från andra cmdletar.

Substantiv i cmdlet-namn måste vara unika, och när det gäller generiska substantiv, till exempel *Server*, är det bäst att lägga till ett kort prefix som särskiljer din resurs från andra liknande resurser. Till exempel är ett cmdlet-namn som innehåller ett substantiv med ett prefix `Get-SQLServer` . Kombinationen av ett visst substantiv med ett mer allmänt verb gör det möjligt för användaren att snabbt hitta cmdleten genom sin åtgärd och sedan identifiera cmdleten med dess resurs samtidigt som den undviker onödiga cmdlet-namnmatchning.

En lista med specialtecken som inte kan användas i cmdlet-namn finns i [nödvändiga utvecklings rikt linjer](./required-development-guidelines.md).

## <a name="verbs"></a>Verb

När du anger ett verb kräver utvecklings rikt linjerna att du använder ett av de fördefinierade verben som tillhandahålls av Windows PowerShell. Genom att använda någon av dessa fördefinierade verb säkerställer du konsekvensen mellan de cmdletar som du skriver och de cmdletar som skrivs av Microsoft och andra. Till exempel används verbet "Get" för cmdlets som hämtar data.

Mer information om rikt linjer för verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md). En lista med specialtecken som inte kan användas i cmdlet-namn finns i [nödvändiga utvecklings rikt linjer](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Stöd för Windows PowerShell-funktioner

Med **cmdlet** -attributet kan du också ange att din cmdlet stöder några av de vanliga funktioner som tillhandahålls av Windows PowerShell. Detta omfattar stöd för vanliga funktioner, till exempel bekräftelse av användar feedback (kallas stöd för ShouldProcess-funktionen) och stöd för transaktioner. (Stöd för transaktioner infördes i Windows PowerShell 2,0).

Mer information om den deklarationssyntax som används för att ange **cmdlet** -attributet finns i deklaration av [cmdlet-attribut](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definition av cmdlet-klass

Följande kod är definitionen för en GetProc-cmdlet-klass. Observera att Pascal-höljet används och att namnet på klassen innehåller verbets verb och substantiv.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a>Pascal-hölje

När du namnger cmdletar använder du Pascal-Skift läge. Till exempel `Get-Item` `Get-ItemProperty` visar cmdletarna och det korrekta sättet att använda versaler när du namnger cmdletar.

## <a name="see-also"></a>Se även

[System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute-deklaration](./cmdlet-attribute-declaration.md)

[Cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
