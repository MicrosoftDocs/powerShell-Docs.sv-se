---
title: Cmdlet-översikt | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356548"
---
# <a name="cmdlet-overview"></a>Översikt över cmdlets

En cmdlet är ett lättviktigt kommando som används i Windows PowerShell-miljön. Windows PowerShell-körningen anropar dessa cmdlets inom kontexten för Automation-skript som anges på kommando raden. Windows PowerShell-körningen anropar också dem program mässigt via API: er för Windows PowerShell.

## <a name="cmdlets"></a>Cmdletar

Cmdlet: ar utför en åtgärd och returnerar vanligt vis ett Microsoft .NET Framework-objekt till nästa-kommando i pipelinen. Om du vill skriva en cmdlet måste du implementera en cmdlet-klass som härleds från en av två specialiserade cmdlets bas klasser. Den härledda klassen måste:

- Deklarera ett attribut som identifierar den härledda klassen som en cmdlet.

- Definiera offentliga egenskaper som dekoreras med attribut som identifierar de offentliga egenskaperna som cmdlet-parametrar.

- Åsidosätt en eller flera av metoderna för bearbetning av indata för att bearbeta poster.

Du kan läsa in sammansättningen som innehåller klassen direkt med hjälp av cmdleten [import-module](/powershell/module/microsoft.powershell.core/import-module) , eller så kan du skapa ett värd program som läser in sammansättningen med hjälp av API: t [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) . Båda metoderna ger program mässig och kommando rads åtkomst till funktionerna i cmdleten.

## <a name="cmdlet-terms"></a>Cmdlet-villkor

Följande villkor används ofta i Windows PowerShell-cmdlet-dokumentationen:

### <a name="cmdlet-attribute"></a>Cmdlet-attribut

Ett .NET Framework-attribut som används för att deklarera en cmdlet-klass som en cmdlet.
Även om PowerShell använder flera andra attribut som är valfria, krävs cmdlet-attributet.
Mer information om det här attributet finns i [deklaration av cmdlet-attribut](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Cmdlet-parameter

De offentliga egenskaperna som definierar de parametrar som är tillgängliga för användaren eller till det program som kör cmdleten.
Cmdlets kan ha obligatoriska, namngivna parametrar, positions parametrar och *växlings* parametrar.
Med växlings parametrar kan du definiera parametrar som bara utvärderas om parametrarna anges i anropet.
Mer information om olika typer av parametrar finns i cmdlet- [parametrar](cmdlet-parameters.md).

### <a name="parameter-set"></a>Parameter uppsättning

En grupp parametrar som kan användas i samma kommando för att utföra en speciell åtgärd.
En cmdlet kan ha flera parameter uppsättningar, men varje parameter uppsättning måste ha minst en parameter som är unik.
En utmärkt cmdlet-design innebär starkt att den unika parametern även är en obligatorisk parameter.
Mer information om parameter uppsättningar finns i [cmdlet parameter Sets](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>Dynamisk parameter

En parameter som läggs till i cmdleten vid körning.
Normalt läggs de dynamiska parametrarna till i cmdleten när en annan parameter har angetts till ett speciellt värde.
Mer information om dynamiska parametrar finns i [cmdlet Dynamic Parameters](cmdlet-dynamic-parameters.md).

### <a name="input-processing-method"></a>Metod för bearbetning av indata

En metod som en cmdlet kan använda för att bearbeta de poster som tas emot som inmatade.
I metoderna för indata bearbetning ingår metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) och metoden [system. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) . När du implementerar en cmdlet måste du åsidosätta minst en av metoderna [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)och [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .
Normalt är metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden som du åsidosätter eftersom den anropas för varje post som cmdleten bearbetar.
Däremot kallas metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) och [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -metoden en tid för att utföra för bearbetning eller efter bearbetning av posterna.
Mer information om dessa metoder finns i [metoder för indata bearbetning](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>ShouldProcess-funktion

Med PowerShell kan du skapa cmdlets som frågar användaren om feedback innan cmdleten gör en ändring i systemet.
För att använda den här funktionen måste cmdleten deklarera att den stöder funktionen ShouldProcess när du deklarerar cmdlet-attributet, och cmdleten måste anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder inifrån en bearbetnings metod för indata.
Mer information om hur du stöder ShouldProcess-funktionen finns i [begära bekräftelse](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transaktionen

En logisk grupp kommandon som behandlas som en enskild uppgift.
Aktiviteten Miss lyckas automatiskt om något kommando i gruppen Miss lyckas och användaren har möjlighet att acceptera eller avvisa de åtgärder som utförs i transaktionen.
För att delta i en transaktion måste cmdleten deklarera att den stöder transaktioner när cmdlet-attributet deklareras.
Stöd för transaktioner infördes i Windows PowerShell 2,0.
Mer information om transaktioner finns i [så här stöder du transaktioner](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Hur cmdletar skiljer sig från kommandon

Cmdlets skiljer sig från kommandon i andra kommando-Shell-miljöer på följande sätt:

- Cmdlet: ar är instanser av .NET Framework klasser. de är inte fristående körbara filer.

- Cmdletar kan skapas från så få som dussin rader kod.

- -Cmdlet: ar utför vanligt vis inte egna tolkningar, fel presentationer eller formatering av utdata. Parsning, fel presentation och formatering av utdata hanteras av Windows PowerShell-körningsmiljön.

- Cmdlets bearbetar indata-objekt från pipelinen i stället för från strömmar av text, och cmdletar skickar vanligt vis objekt som utdata till pipelinen.

- Cmdletar är postorienterade eftersom de bearbetar ett enskilt objekt i taget.

## <a name="cmdlet-base-classes"></a>Cmdlet-basadress

Windows PowerShell stöder cmdlets som härleds från följande två bas klasser.

- De flesta cmdlets baseras på .NET Framework klasser som härleds från Bask Lassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . Genom att härleda från den här klassen kan en cmdlet använda den minsta uppsättningen beroenden i Windows PowerShell-körningsmiljön. Detta har två fördelar. Den första förmånen är att cmdlet-objekten är mindre, och du är mindre sannolika att påverkas av ändringar i Windows PowerShell-körningsmiljön. Den andra fördelen är att om du behöver kan du direkt skapa en instans av cmdlet-objektet och sedan anropa det direkt i stället för att anropa det via Windows PowerShell-körningsmiljön.

- De mer komplexa cmdletarna baseras på .NET Framework klasser som härleds från Bask Lassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Genom att härleda från den här klassen får du mycket mer åtkomst till Windows PowerShell-körningsmiljön. Med den här åtkomsten kan din cmdlet anropa skript, för att få åtkomst till providrar och för att komma åt det aktuella sessionstillståndet. (För att få åtkomst till det aktuella sessionstillståndet får du och ställer in sessionsvariabler och inställningar.) Att härleda från den här klassen ökar dock storleken på cmdlet-objektet och innebär att cmdleten är mer tätt kopplad till den aktuella versionen av Windows PowerShell-körningsmiljön.

I allmänhet bör du, om du inte behöver utökad åtkomst till Windows PowerShell-körningsmiljön, härledas från klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . Windows PowerShell-körningsmiljön har dock omfattande loggnings funktioner för körning av cmdletar. Om din gransknings modell är beroende av den här loggningen kan du förhindra körning av cmdleten från en annan cmdlet genom att härleda från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="input-processing-methods"></a>Metoder för bearbetning av indata

Klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) innehåller följande virtuella metoder som används för att bearbeta poster. Alla härledda cmdlet-klasser måste åsidosätta en eller flera av de första tre metoderna:

- [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): används för att tillhandahålla valfria för bearbetnings funktioner för cmdlet: en.

- [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): används för att tillhandahålla funktioner för post-för-post-bearbetning för cmdlet: en. Metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) kan anropas valfritt antal gånger eller inte alls, beroende på inmatad cmdlet.

- [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): används för att tillhandahålla valfria funktioner för efter bearbetning för cmdlet: en.

- [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): används för att stoppa bearbetningen när användaren stoppar cmdlet asynkront (till exempel genom att trycka på CTRL + C).

Mer information om dessa metoder finns i [cmdlet-metoder för bearbetning av indata](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Cmdlet-attribut

Windows PowerShell definierar flera .NET Framework attribut som används för att hantera cmdlets och för att ange vanliga funktioner som tillhandahålls av Windows PowerShell och som kan krävas av cmdleten. Attribut används till exempel för att ange en klass som en cmdlet för att ange parametrarna för cmdleten och för att begära verifiering av Indatatyp så att cmdlet-utvecklare inte behöver implementera funktionen i sin cmdlet-kod. Mer information om attribut finns i [Windows PowerShell-attribut](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Cmdlet-namn

Windows PowerShell använder ett verb-och-Substantiv-filnamn för namn-cmdletar. Till exempel används den `Get-Command`-cmdleten som ingår i Windows PowerShell för att hämta alla cmdletar som är registrerade i kommando gränssnittet. Verbet identifierar åtgärden som cmdleten utför, och Substantiv identifierar resursen som cmdleten utför åtgärden på.

Dessa namn anges när klassen .NET Framework deklareras som en cmdlet. Mer information om hur du deklarerar en .NET Framework klass som en cmdlet finns i [deklaration av cmdlet-attribut](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Skriver cmdlet-kod

Det här dokumentet innehåller två sätt att identifiera hur cmdlet-kod skrivs. Om du föredrar att se koden utan mycket förklaring, se [exempel på cmdlet-kod](./examples-of-cmdlet-code.md). Om du vill ha mer information om koden kan du läsa avsnittet [GetProc självstudie](./getproc-tutorial.md), [StopProc självstudie](./stopproc-tutorial.md)eller [SelectStr](./selectstr-tutorial.md) .

Mer information om rikt linjerna för att skriva cmdlets finns i [rikt linjer för utveckling av cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Se även

[Windows PowerShell-cmdlet-koncept](./windows-powershell-cmdlet-concepts.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
