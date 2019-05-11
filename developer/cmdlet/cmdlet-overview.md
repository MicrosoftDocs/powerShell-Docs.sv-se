---
title: 'Cmdlet: en översikt över | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229359"
---
# <a name="cmdlet-overview"></a>Översikt över cmdlets

En cmdlet är ett enkelt kommando som används i Windows PowerShell-miljö. Windows PowerShell-runtime anropar dessa cmdletar inom ramen för automatiseringsskript som finns på kommandoraden. Windows PowerShell-runtime också anropar dem programmässigt via Windows PowerShell APIs.

## <a name="cmdlets"></a>Cmdletar

Cmdlets utför en åtgärd och returnera vanligtvis ett Microsoft .NET Framework-objekt med nästa kommando i pipelinen. Om du vill skriva en cmdlet, måste du implementera en cmdlet-klass som härleds från en av två specialiserade cmdlet basklasser. Den härledda klassen måste:

- Deklarera ett attribut som identifierar den härledda klassen som en cmdlet.

- Definiera offentliga egenskaper som dekorerad med attribut som identifierar de offentliga egenskaperna som cmdlet-parametrarna.

- Åsidosätt en eller flera av indata som bearbetar metoder för att bearbeta poster.

Du kan läsa in sammansättningen som innehåller klassen direkt med hjälp av den [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet, eller skapa ett program som läser in sammansättningen med hjälp av den [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Båda metoderna ger programmässig och kommandoradssyntaxen åtkomst till funktionerna i cmdleten.

## <a name="cmdlet-terms"></a>Cmdlet-villkor

Följande villkor används ofta i dokumentationen för Windows PowerShell-cmdlet:

### <a name="cmdlet-attribute"></a>Cmdlet-attribut

Ett .NET Framework-attribut som används för att deklarera en cmdlet-klass som en cmdlet.
Även om PowerShell använder flera attribut som är valfria, är Cmdlet-attributet obligatoriskt.
Läs mer om det här attributet [Cmdlet attributet deklarationen](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Cmdlet-parameter

Offentliga egenskaper som definierar de parametrar som är tillgänglig för användaren eller för det program som kör cmdlet: en.
Cmdlet: ar kan ha krävt namngivna, namngivna, och *växla* parametrar.
Växla parametrar kan du definiera parametrar som utvärderas bara om parametrarna har angetts i anropet.
Mer information om de olika typerna av parametrar finns i [Cmdlet-parametrarna](cmdlet-parameters.md).

### <a name="parameter-set"></a>Parameteruppsättning

En grupp med parametrar som kan användas i samma kommando för att utföra en viss åtgärd.
En cmdlet kan ha flera parameteruppsättningar, men varje parameteruppsättningen måste ha minst en parameter som är unik.
Cmdlet: en bra design rekommenderar att parametern unika också vara en obligatorisk parameter.
Läs mer om parameteruppsättningar [cmdlet: en Parameter anger](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>dynamisk parameter

En parameter som läggs till i cmdleten vid körning.
Dynamiska parametrar läggs normalt till cmdlet: en när en annan parameter har angetts till ett specifikt värde.
Mer information om dynamiska parametrar finns i [dynamiska parametrar för cmdleten](cmdlet-dynamic-parameters.md).

### <a name="input-processing-method"></a>indata metoden bearbetades

En metod som en cmdlet kan använda för att bearbeta posterna som tas emot som indata.
Inkommande bearbetning sätt är att den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metoden den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden den [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metoden och [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) metod. När du implementerar en cmdlet, måste du åsidosätta minst en av de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), och [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metoder.
Normalt den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden är den metod som du åsidosätta eftersom det kallas för varje post som cmdlet bearbetar.
Däremot den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod och [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metoden anropas en gång för att utföra bearbeta data i förväg eller efter bearbetning av posterna.
Läs mer om de här metoderna [metoder för bearbetning av indata](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>ShouldProcess-funktionen

PowerShell kan du skapa cmdletar som frågar användaren om feedback innan cmdleten gör en ändring i systemet.
Om du vill använda denna funktion kan cmdlet: en måste deklarera att den stöder funktionen ShouldProcess när du deklarera Cmdlet-attributet och cmdlet: en måste anropa den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder från inom indata metoden bearbetades.
Läs mer om hur du den funktionalitet som ShouldProcess [begär bekräftelse](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transaktionen

En logisk grupp av kommandon som behandlas som en enskild uppgift.
Uppgiften misslyckas automatiskt om ett kommando i gruppen misslyckas och användaren har möjlighet att godkänna eller avvisa de åtgärder som utförs i transaktionen.
Om du vill delta i en transaktion måste cmdleten deklarera att den stöder transaktioner när Cmdlet-attributet har deklarerats.
Stöd för transaktioner introducerades i Windows PowerShell 2.0.
Mer information om transaktioner finns [så Support transaktioner](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Hur cmdletar skiljer sig från kommandon

Cmdlet: ar skiljer sig från kommandona i miljöer från andra shell för kommando på följande sätt:

- Cmdlet: ar är instanser av .NET Framework-klasser de är inte fristående körbara filer.

- Cmdlet: ar kan skapas från så lite som ett dussin rader med kod.

- Cmdlet: ar vanligtvis gör inte egna parsning fel presentation eller formatering av utdata. Parsa, fel presentation och formatering av utdata hanteras av Windows PowerShell-körningen.

- Cmdlet: ar processen indata objekt från pipelinen i stället för från strömmar av text och cmdletar ger vanligtvis objekt som utdata för pipelinen.

- Cmdlet: ar är post inriktad eftersom de bearbetar ett enskilt objekt i taget.

## <a name="cmdlet-base-classes"></a>Cmdlet: en Base-klasser

Windows PowerShell har stöd för cmdletar som härleds från följande två basklasser.

- De flesta cmdletar baseras på .NET Framework-klasserna som härleds från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) basklassen. Som härleds från den här klassen kan en cmdlet för att använda den minsta uppsättningen beroenden på en Windows PowerShell. Detta har två fördelar. Första fördelen är att cmdlet-objekt är mindre och minskar risken för att påverkas av ändringar i Windows PowerShell-runtime. Andra fördelen är att, om du behöver kan du direkt skapa en instans av objektet cmdlet och anropa det direkt i stället för att anropa den till Windows PowerShell-körning.

- Cmdlet: ar för mer komplexa baseras på .NET Framework-klasserna som härleds från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basklassen. Som härleds från den här klassen ger dig mycket större åtkomst till Windows PowerShell-körningen. Den här åtkomsten kan din cmdlet för att anropa skript, att komma åt leverantörer och komma åt det aktuella sessionstillståndet. (Om du vill komma åt det aktuella sessionstillståndet måste du skaffa och konfigurera sessionsvariabler och inställningar.) Men som härleds från den här klassen ökar storleken på objektet cmdlet och innebär det att cmdlet: mer nära kopplade till den aktuella versionen av Windows PowerShell-runtime.

I allmänhet såvida du inte behöver utökad åtkomst till Windows PowerShell-runtime, bör du härleder från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass. Windows PowerShell-körning har dock omfattande loggningsfunktioner för körningen av cmdlet: ar. Om granskning modellen är beroende av den här loggning, kan du förhindra att körningen av cmdlet: från inom en annan cmdlet genom som härleds från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klass.

## <a name="input-processing-methods"></a>Ange metoderna

Den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klassen innehåller följande virtuella metoder som används för att bearbeta poster. Klasserna för härledda cmdlet måste åsidosätta en eller flera av de första tre metoderna:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Används för att tillhandahålla valfritt enstaka, före bearbetnings-funktioner för cmdleten.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Används för att tillhandahålla post med bearbetning av funktioner för cmdleten. Den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden kan anropas många gånger eller inte alls, beroende på indata för cmdlet: ar.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Används för att ange valfria funktioner för enstaka, efterbearbetning för cmdlet: en.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Används för att stoppa bearbetningen när användaren slutar cmdleten asynkront (till exempel genom att trycka på CTRL + C).

Läs mer om de här metoderna [Cmdlet indata bearbetning av metoder](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Cmdlet-attribut

Windows PowerShell definierar flera attribut i .NET Framework som används för att hantera cmdletar och ange gemensamma funktioner som tillhandahålls av Windows PowerShell och som kan krävas av cmdlet: en. Till exempel används attribut för att ange en klass som en cmdlet genom att ange parametrarna för cmdleten, samt att begära verifiering av indata så att cmdleten utvecklare inte behöver implementera den funktionen i sina cmdlet-kod. Mer information om attribut finns i [Windows PowerShell-attribut](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Cmdlet-namnen

Windows PowerShell använder ett verb och substantiv namn-par i namn-cmdletar. Till exempel den `Get-Command` cmdlet som ingår i Windows PowerShell används för att hämta alla cmdletar som är registrerade i Kommandotolken. Verbet identifierar den åtgärd som utförs av cmdlet: en och substantivet identifierar resursen som cmdlet utför åtgärden.

Dessa namn anges när .NET Framework-klass deklareras som en cmdlet. Läs mer om hur du deklarerar en .NET Framework-klass som en cmdlet, [Cmdlet attributet deklarationen](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Skriva Cmdlet-kod

Det här dokumentet ger dig två sätt att identifiera hur cmdlet kod skrivs. Om du vill se kod utan mycket förklaring finns [exempel Cmdlet kod](./examples-of-cmdlet-code.md). Om du föredrar mer förklaring om koden, se den [GetProc självstudien](./getproc-tutorial.md), [StopProc självstudien](./stopproc-tutorial.md), eller [SelectStr självstudien](./selectstr-tutorial.md) ämnen.

Mer information om riktlinjer för att skriva cmdlets finns i [riktlinjer för utveckling av Cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Se även

[Windows PowerShell-Cmdlet-begrepp](./windows-powershell-cmdlet-concepts.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
