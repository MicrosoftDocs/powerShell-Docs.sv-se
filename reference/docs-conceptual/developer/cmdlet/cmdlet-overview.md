---
title: Översikt över cmdlets
ms.date: 06/11/2020
ms.openlocfilehash: 576df03f35dff80479d1fce18cf4306c9219d42f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784409"
---
# <a name="cmdlet-overview"></a>Översikt över cmdlets

En cmdlet är ett lättviktigt kommando som används i PowerShell-miljön. PowerShell-körningen anropar dessa cmdlets inom kontexten för Automation-skript som anges på kommando raden. PowerShell-körningen anropar också dem via programmering via PowerShell-API: er.

## <a name="cmdlets"></a>Cmdletar

Cmdletar utför en åtgärd och returnerar vanligt vis ett Microsoft .NET-objekt till nästa-kommando i pipelinen. En cmdlet är ett enda kommando som ingår i pipeline-semantiken för PowerShell.
Detta inkluderar binära (C#) cmdlets, avancerade skript funktioner, CDXLM och arbets flöden.

Den här SDK-dokumentationen beskriver hur du skapar binära cmdlets som skrivits i C#. Information om skriptbaserade cmdlets finns i:

- [about_Functions_Advanced](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [about_Functions_CmdletBindingAttribute](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [about_Functions_Advanced_Methods](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

Om du vill skapa en binär cmdlet måste du implementera en cmdlet-klass som härleds från en av två specialiserade cmdlets bas klasser. Den härledda klassen måste:

- Deklarera ett attribut som identifierar den härledda klassen som en cmdlet.
- Definiera offentliga egenskaper som dekoreras med attribut som identifierar de offentliga egenskaperna som cmdlet-parametrar.
- Åsidosätt en eller flera av metoderna för bearbetning av indata för att bearbeta poster.

Du kan läsa in sammansättningen som innehåller klassen direkt med hjälp av cmdleten [import-module](/powershell/module/microsoft.powershell.core/import-module) , eller så kan du skapa ett värd program som läser in sammansättningen med hjälp av [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -API: et. Båda metoderna ger program mässig och kommando rads åtkomst till funktionerna i cmdleten.

## <a name="cmdlet-terms"></a>Cmdlet-villkor

Följande villkor används ofta i PowerShell-cmdlet-dokumentationen:

### <a name="cmdlet-attribute"></a>Cmdlet-attribut

Ett .NET-attribut som används för att deklarera en cmdlet-klass som en cmdlet. Även om PowerShell använder flera andra attribut som är valfria, krävs cmdlet-attributet. Mer information om det här attributet finns i [deklaration av cmdlet-attribut](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Cmdlet-parameter

De offentliga egenskaperna som definierar de parametrar som är tillgängliga för användaren eller till det program som kör cmdleten. Cmdlets kan ha obligatoriska, namngivna parametrar, positions parametrar och *växlings* parametrar. Med växlings parametrar kan du definiera parametrar som bara utvärderas om parametrarna anges i anropet. Mer information om olika typer av parametrar finns i cmdlet- [parametrar](cmdlet-parameters.md).

### <a name="parameter-set"></a>Parameter uppsättning

En grupp parametrar som kan användas i samma kommando för att utföra en speciell åtgärd. En cmdlet kan ha flera parameter uppsättningar, men varje parameter uppsättning måste ha minst en parameter som är unik. En utmärkt cmdlet-design innebär starkt att den unika parametern även är en obligatorisk parameter.
Mer information om parameter uppsättningar finns i [cmdlet parameter Sets](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>Dynamisk parameter

En parameter som läggs till i cmdleten vid körning. Normalt läggs de dynamiska parametrarna till i cmdleten när en annan parameter har angetts till ett speciellt värde. Mer information om dynamiska parametrar finns i [cmdlet Dynamic Parameters](cmdlet-dynamic-parameters.md).

### <a name="input-processing-methods"></a>Metoder för bearbetning av indata

Klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) innehåller följande virtuella metoder som används för att bearbeta poster. Alla härledda cmdlet-klasser måste åsidosätta en eller flera av de första tre metoderna:

- [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): används för att tillhandahålla valfria för bearbetnings funktioner för cmdlet: en.
- [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): används för att tillhandahålla funktioner för post-för-post-bearbetning för cmdlet: en. Metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) kan anropas valfritt antal gånger eller inte alls, beroende på inmatad cmdlet.
- [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): används för att tillhandahålla valfria funktioner för efter bearbetning för cmdlet: en.
- [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): används för att stoppa bearbetningen när användaren stoppar cmdlet asynkront (till exempel genom att trycka på <kbd>CTRL</kbd> + <kbd>C</kbd>).

Mer information om dessa metoder finns i [cmdlet-metoder för bearbetning av indata](./cmdlet-input-processing-methods.md).

När du implementerar en cmdlet måste du åsidosätta minst en av dessa metoder för bearbetning av indata.
Normalt är **ProcessRecord ()** metoden som du åsidosätter eftersom den anropas för varje post som cmdleten bearbetar. Däremot anropas metoden **BeginProcessing ()** och **EndProcessing ()** för att utföra för bearbetning eller efter bearbetning av posterna. Mer information om dessa metoder finns i [metoder för indata bearbetning](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>ShouldProcess-funktion

Med PowerShell kan du skapa cmdlets som frågar användaren om feedback innan cmdleten gör en ändring i systemet. Om du vill använda den här funktionen måste cmdleten deklarera att den stöder `ShouldProcess` funktionen när du deklarerar cmdlet-attributet och cmdleten måste anropa metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) i en metod för bearbetning av indata. Mer information om hur du stöder `ShouldProcess` funktionen finns i [begära bekräftelse](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transaktion

En logisk grupp kommandon som behandlas som en enskild uppgift. Aktiviteten Miss lyckas automatiskt om något kommando i gruppen Miss lyckas och användaren har möjlighet att acceptera eller avvisa de åtgärder som utförs i transaktionen. För att delta i en transaktion måste cmdleten deklarera att den stöder transaktioner när cmdlet-attributet deklareras. Stöd för transaktioner infördes i Windows PowerShell 2,0. Mer information om transaktioner finns i [så här stöder du transaktioner](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Hur cmdletar skiljer sig från kommandon

Cmdlets skiljer sig från kommandon i andra kommando-Shell-miljöer på följande sätt:

- Cmdlet: ar är instanser av .NET-klasser. de är inte fristående körbara filer.
- Cmdletar kan skapas från så få som dussin rader kod.
- -Cmdlet: ar utför vanligt vis inte egna tolkningar, fel presentationer eller formatering av utdata. Parsning, fel presentation och formatering av utdata hanteras av PowerShell-körningsmiljön.
- Cmdlets bearbetar indata-objekt från pipelinen i stället för från strömmar av text, och cmdletar skickar vanligt vis objekt som utdata till pipelinen.
- Cmdletar är postorienterade eftersom de bearbetar ett enskilt objekt i taget.

## <a name="cmdlet-base-classes"></a>Cmdlet-basadress

Windows PowerShell stöder cmdlets som härleds från följande två bas klasser.

- De flesta cmdlets baseras på .NET-klasser som härleds från Bask Lassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .
  Genom att härleda från den här klassen kan en cmdlet använda den minsta uppsättningen beroenden i Windows PowerShell-körningsmiljön. Detta har två fördelar. Den första förmånen är att cmdlet-objekten är mindre, och du är mindre sannolika att påverkas av ändringar i PowerShell-körningsmiljön. Den andra fördelen är att om du behöver kan du direkt skapa en instans av cmdlet-objektet och sedan anropa det direkt i stället för att anropa det via PowerShell-körningen.

- De mer komplexa cmdletarna baseras på .NET-klasser som härleds från Bask Lassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Genom att härleda från den här klassen får du mycket mer åtkomst till PowerShell-körningsmiljön. Med den här åtkomsten kan din cmdlet anropa skript, för att få åtkomst till providrar och för att komma åt det aktuella sessionstillståndet.
  (För att få åtkomst till det aktuella sessionstillståndet får du och ställer in sessionsvariabler och inställningar.) Att härleda från den här klassen ökar dock storleken på cmdlet-objektet och innebär att cmdleten är mer tätt kopplad till den aktuella versionen av PowerShell-körningsmiljön.

I allmänhet bör du, om du inte behöver utökad åtkomst till PowerShell-körningsmiljön, härledas från klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .
PowerShell-körningsmiljön har dock omfattande loggnings funktioner för körning av cmdletar. Om din gransknings modell är beroende av den här loggningen kan du förhindra körning av cmdleten från en annan cmdlet genom att härleda från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="cmdlet-attributes"></a>Cmdlet-attribut

PowerShell definierar flera .NET-attribut som används för att hantera cmdlets och för att ange vanliga funktioner som tillhandahålls av PowerShell och som kan krävas av cmdleten. Attribut används till exempel för att ange en klass som en cmdlet för att ange parametrarna för cmdleten och för att begära verifiering av Indatatyp så att cmdlet-utvecklare inte behöver implementera funktionen i sin cmdlet-kod. Mer information om attribut finns i [PowerShell-attribut](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Cmdlet-namn

PowerShell använder ett verb-och-Substantiv-nyckelpar för namn-cmdletar. Den `Get-Command` cmdlet som ingår i PowerShell används till exempel för att hämta alla cmdletar som är registrerade i kommando gränssnittet. Verbet identifierar åtgärden som cmdleten utför, och Substantiv identifierar resursen som cmdleten utför åtgärden på.

Dessa namn anges när .NET-klassen deklareras som en cmdlet. Mer information om hur du deklarerar en .NET-klass som en-cmdlet finns i [deklaration av cmdlet-attribut](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Skriver cmdlet-kod

Det här dokumentet innehåller två sätt att identifiera hur cmdlet-kod skrivs. Om du föredrar att se koden utan mycket förklaring, se [exempel på cmdlet-kod](./examples-of-cmdlet-code.md). Om du vill ha mer information om koden kan du läsa avsnittet [GetProc självstudie](./getproc-tutorial.md), [StopProc självstudie](./stopproc-tutorial.md)eller [SelectStr](./selectstr-tutorial.md) .

Mer information om rikt linjerna för att skriva cmdlets finns i [rikt linjer för utveckling av cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Se även

[PowerShell-cmdlet-koncept](./windows-powershell-cmdlet-concepts.md)

[Skriva en PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[PowerShell SDK](../windows-powershell-reference.md)
