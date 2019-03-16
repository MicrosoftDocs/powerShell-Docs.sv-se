---
title: Cmdlet klassdeklarationen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055095"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet-klassdeklaration

En Microsoft .NET Framework-klass deklareras som en cmdlet genom att ange den **Cmdlet** attribut som metadata för klassen. (Den **Cmdlet** attributet är det enda obligatoriska attributet för alla cmdletar). När du anger den **Cmdlet** attribut, måste du ange verb och substantiv-paret som identifierar cmdlet: en för användaren. Och du måste beskriver funktioner i Windows PowerShell som har stöd för cmdleten. Mer information om deklarationssyntax som används för att ange den **Cmdlet** attributet, se [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Den **Cmdlet** attributet definieras av den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klass. Egenskaperna för den här klassen motsvarar deklarationsparametrar som ska användas när du deklarerar attributet.

## <a name="nouns"></a>Substantiv

Substantiv-cmdlet: ens anger vilka resurser som cmdlet: en fungerar. Substantivet särskiljer dina cmdletar från andra cmdlet: ar.

Substantiv i cmdlet-namn måste vara specifikt, och när det gäller allmän substantiv som *server*, är det bäst att lägga till ett kort prefix som särskiljer resursen från andra liknande resurser. Till exempel en cmdlet-namn som innehåller ett substantiv med prefixet är `Get-SQLServer`. Kombinationen av en specifik substantiv med en mer allmän verbet kan användaren snabbt kan hitta cmdlet: en av dess åtgärden och identifiera cmdlet: en av dess resurs samtidigt som du undviker onödiga cmdlet namn duplicering.

En lista över specialtecken som inte kan användas i cmdlet-namnen finns i [krävs utveckling riktlinjer](./required-development-guidelines.md).

## <a name="verbs"></a>Verb

När du anger ett verb, kräver riktlinjer för utveckling att du använder någon av de fördefinierade verb som tillhandahålls av Windows PowerShell. Med någon av dessa fördefinierade verb, säkerställer konsekvens mellan de cmdletar som du skriver och som har skrivits av Microsoft och andra cmdletar. Till exempel används ”Get”-verb för cmdletar som hämtar data.

Läs mer om riktlinjer för verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md). En lista över specialtecken som inte kan användas i cmdlet-namnen finns i [krävs utveckling riktlinjer](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Stöd för Windows PowerShell-funktioner

Den **Cmdlet** attribut kan du ange att din cmdlet har stöd för några av de vanliga funktioner som tillhandahålls av Windows PowerShell. Detta inkluderar stöd för vanliga funktioner, till exempel feedback Användarbekräftelse (kallas stöd för ShouldProcess-funktionen) och stöd för transaktioner. (Stöd för transaktioner introducerades i Windows PowerShell 2.0).

Mer information om deklarationssyntax som används för att ange den **Cmdlet** attributet, se [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Cmdlet-klassdefinition

Följande kod är definitionen för en GetProc cmdlet-klass. Observera att Pascal gemener och versaler används och att namnet på klassen innehåller verb och substantiv-cmdlet: ens.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Pascal gemener och versaler

När du namnger cmdlet: ar, använda Pascal gemener och versaler. Till exempel den `Get-Item` och `Get-ItemProperty` cmdletar visar det korrekta sättet att använda versaler när du namnger cmdletar.

## <a name="see-also"></a>Se även

[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute deklaration](./cmdlet-attribute-declaration.md)

[Cmdlet Verb namn](./approved-verbs-for-windows-powershell-commands.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
