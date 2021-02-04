---
description: Beskriver de parametrar som kan användas med vilken cmdlet som helst.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 898f0897638523291751ce75db1c6a6b4628e778
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860701"
---
# <a name="about-commonparameters"></a>Om CommonParameters

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver de parametrar som kan användas med vilken cmdlet som helst.

## <a name="long-description"></a>LÅNG BESKRIVNING

De gemensamma parametrarna är en uppsättning cmdlet-parametrar som du kan använda med valfri cmdlet. De implementeras av PowerShell, inte av cmdlet-utvecklaren, och de är automatiskt tillgängliga för alla cmdletar.

Du kan använda de gemensamma parametrarna med valfri cmdlet, men de kanske inte har någon påverkan på alla cmdletar. Om en cmdlet till exempel inte genererar några utförliga utdata, har den **utförliga** gemensamma parametern ingen effekt.

De gemensamma parametrarna är också tillgängliga för avancerade funktioner som använder attributet **CmdletBinding** eller attributet **parameter** .

Flera vanliga parametrar åsidosätter systemstandardinställningar eller inställningar som du anger med hjälp av variablerna för PowerShell-inställningar. Till skillnad från inställningarna för variabler påverkar de gemensamma parametrarna bara de kommandon som de används i.

Mer information finns i [about_Preference_Variables](./about_Preference_Variables.md).

I följande lista visas de gemensamma parametrarna. Deras alias visas inom parentes.

- **Felsöka** (dB)
- **ErrorAction** (EA)
- **ErrorVariable** (EV)
- **InformationAction** (Infa)
- **InformationVariable** (IV)
- **Avvariabel** (OV)
- **Utbuffer** (OB)
- **PipelineVariable** (PV)
- **Verbose** (VB)
- **WarningAction** (WA)
- **WarningVariable** (WV)

**Åtgärds** parametrarna är **Åtgärdsinställning** -typnamn.
**Åtgärdsinställning** är en uppräkning med följande värden:

| Name             | Värde |
|------------------|-------|
| Suspend          | 5     |
| Ignorera           | 4     |
| Inquire          | 3     |
| Fortsätt         | 2     |
| Stoppa             | 1     |
| SilentlyContinue | 0     |

Du kan använda namnet eller värdet med parametern.

Förutom de gemensamma parametrarna erbjuder många cmdlets parametrar för risk minskning. Cmdletar som innebär risk för systemet eller användar data erbjuder vanligt vis dessa parametrar.

Parametrarna för risk minskning är:

- **WhatIf** (Wi)
- **Bekräfta** (CF)

### <a name="common-parameter-descriptions"></a>VANLIGA PARAMETER BESKRIVNINGAR

#### <a name="debug"></a>Felsökning

Visar information om program nivå om den åtgärd som utförs av kommandot. Den här parametern fungerar bara när kommandot genererar ett fel söknings meddelande. Den här parametern fungerar till exempel när ett kommando innehåller `Write-Debug` cmdleten.

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

Som standard visas fel söknings meddelanden eftersom värdet för `$DebugPreference` variabeln är **SilentlyContinue**.

I interaktivt läge åsidosätter **fel söknings** parametern värdet för `$DebugPreference` variabeln för det aktuella kommandot och anger värdet för `$DebugPreference` att **fråga**.

I icke-interaktivt läge åsidosätter **fel söknings** parametern värdet för `$DebugPreference` variabeln för det aktuella kommandot och anger värdet för `$DebugPreference` att **fortsätta**.

`-Debug:$true` har samma resultat som `-Debug` . Används `-Debug:$false` för att förhindra visning av fel söknings meddelanden när `$DebugPreference` inte är **SilentlyContinue**, vilket är standardvärdet.

#### <a name="erroraction"></a>ErrorAction

Anger hur cmdleten svarar på ett icke-avslutande fel från kommandot.
Den här parametern fungerar bara när kommandot genererar ett icke-avslutande fel, till exempel från `Write-Error` cmdleten.

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

Parametern **ErrorAction** åsidosätter värdet för `$ErrorActionPreference` variabeln för det aktuella kommandot. Eftersom standardvärdet för `$ErrorActionPreference` variabeln **fortsätter** visas fel meddelanden och körningen fortsätter om du inte använder parametern **ErrorAction** .

Parametern **ErrorAction** har ingen påverkan på att avsluta fel (till exempel saknade data, parametrar som inte är giltiga eller otillräckliga behörigheter) som hindrar ett kommando från att slutföras.

`-ErrorAction:Continue` Visa fel meddelandet och fortsätt att köra kommandot. `Continue` används som standard.

`-ErrorAction:Ignore` ignorerar fel meddelandet och fortsätter att köra kommandot. Till skillnad från **SilentlyContinue** lägger **Ignorera** inte till fel meddelandet i den `$Error` automatiska variabeln. **Ignorera** -värdet introduceras i PowerShell 3,0.

`-ErrorAction:Inquire` visar fel meddelandet och du uppmanas att bekräfta innan du fortsätter körningen. Det här värdet används sällan.

`-ErrorAction:SilentlyContinue` ignorerar fel meddelandet och fortsätter att köra kommandot.

`-ErrorAction:Stop` visar fel meddelandet och slutar att köra kommandot.

`-ErrorAction:Suspend` är bara tillgängligt för arbets flöden som inte stöds i PowerShell 6 och senare.

> [!NOTE]
> Parametern **ErrorAction** åsidosätter, men ersätter inte värdet för `$ErrorAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.

#### <a name="errorvariable"></a>ErrorVariable

**ErrorVariable** lagrar fel meddelanden om kommandot i den angivna variabeln och i den `$Error` automatiska variabeln. Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md)

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Som standard skriver nya fel meddelanden över fel meddelanden som redan är lagrade i variabeln. Om du vill lägga till fel meddelandet i variabel innehållet skriver du ett plus tecken ( `+` ) före variabel namnet.

Till exempel skapar följande kommando `$a` variabeln och lagrar sedan eventuella fel i den:

```powershell
Get-Process -Id 6 -ErrorVariable a
```

Följande kommando lägger till eventuella fel meddelanden i `$a` variabeln:

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

Följande kommando visar innehållet i `$a` :

```powershell
$a
```

Du kan använda den här parametern för att skapa en variabel som bara innehåller fel meddelanden från vissa kommandon och som inte påverkar beteendet för den `$Error` automatiska variabeln. Den `$Error` automatiska variabeln innehåller fel meddelanden från alla kommandon i sessionen. Du kan använda mat ris notation, till exempel `$a[0]` eller `$error[1,2]` för att referera till vissa fel som lagras i variablerna.

> [!NOTE]
> Den anpassade fel variabeln innehåller alla fel som genereras av kommandot, inklusive fel från anrop till kapslade funktioner eller skript.

#### <a name="informationaction"></a>InformationAction

Introducerades i PowerShell 5,0. I det kommando eller skript där det används åsidosätter den gemensamma parametern **InformationAction** värdet för `$InformationPreference` variabeln Preference, vilket som standard är inställt på **SilentlyContinue**. När du använder `Write-Information` i ett skript med **InformationAction**, `Write-Information` visas värdena beroende på värdet för parametern **InformationAction** . Mer information om `$InformationPreference` finns i [about_Preference_Variables](./about_Preference_Variables.md).

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

`-InformationAction:Stop` stoppar ett kommando eller skript vid en förekomst av `Write-Information` kommandot.

`-InformationAction:Ignore` undertrycker informations meddelandet och fortsätter att köra kommandot. Till skillnad från **SilentlyContinue** glömmer ignorera det informations meddelandet att **ignoreras** . informations meddelandet läggs inte till i informations data strömmen.

`-InformationAction:Inquire` visar det informations meddelande som du anger i ett `Write-Information` kommando och frågar om du vill fortsätta.

`-InformationAction:Continue` visar informations meddelandet och fortsätter att köra.

`-InformationAction:Suspend` stöds inte i PowerShell Core eftersom det endast är tillgängligt för arbets flöden.

`-InformationAction:SilentlyContinue` ingen påverkan eftersom informations meddelandet inte är (standard) visas och skriptet fortsätter utan avbrott.

> [!NOTE]
> Parametern **InformationAction** åsidosätter, men ersätter inte värdet för `$InformationAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.

#### <a name="informationvariable"></a>InformationVariable

Introducerades i PowerShell 5,0. I det kommando eller skript där det används lagras den gemensamma **InformationVariable** -parametern i en variabel en sträng som du anger genom att lägga till `Write-Information` kommandot. `Write-Information`värdena visas beroende på värdet för den gemensamma parametern **InformationAction** . Om du inte lägger till  den gemensamma parametern InformationAction `Write-Information` visas strängarna beroende på värdet för `$InformationPreference` variabeln Preference. Mer information om `$InformationPreference` finns i [about_Preference_Variables](./about_Preference_Variables.md).

> [!NOTE]
> Variabeln information innehåller alla informations meddelanden som genereras av kommandot, inklusive informations meddelanden från anrop till kapslade funktioner eller skript.

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a>OutBuffer

Fastställer antalet objekt som ska samlas i en buffert innan objekt skickas via pipelinen. Om du utelämnar den här parametern skickas objekten när de genereras.

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Den här resurs hanterings parametern är avsedd för avancerade användare. När du använder den här parametern skickar PowerShell data till nästa cmdlet i batchar för `OutBuffer + 1` .

I följande exempel visas mellan för att `ForEach-Object` bearbeta block som använder `Write-Host` cmdleten. Alternativen visas i batchar med 2 eller `OutBuffer + 1` .

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a>OutVariable

Lagrar utdata-objekt från kommandot i den angivna variabeln, förutom att skicka utdata längs pipelinen.

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Om du vill lägga till utdata i variabeln, i stället för att ersätta eventuella utdata som redan är lagrade där, skriver du ett plus tecken ( `+` ) före variabel namnet.

Följande kommando skapar till exempel `$out` variabeln och lagrar processobjektet i den:

```powershell
Get-Process PowerShell -OutVariable out
```

Följande kommando lägger till objektet bearbeta i `$out` variabeln:

```powershell
Get-Process iexplore -OutVariable +out
```

Följande kommando visar innehållet i `$out` variabeln:

```powershell
$out
```

> [!NOTE]
> Variabeln som skapas av parametern **devariable** är en `[System.Collections.ArrayList]` .

#### <a name="pipelinevariable"></a>PipelineVariable

**PipelineVariable** lagrar värdet för det aktuella pipeline-elementet som en variabel, för alla namngivna kommandon som det flödar genom pipelinen.

>[!NOTE]
> Avancerade funktioner kan ha upp till tre skript block: `begin` , `process` och `end` . När du använder parametern **PipelineVariable** med avancerade funktioner, tilldelas endast värden från det första definierade skript blocket som funktionen kör. Mer information finns i [avancerade funktioner](./about_functions_advanced.md).
> PowerShell 7,2 korrigerar det här beteendet.

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Giltiga värden är strängar, samma som för alla variabel namn.

Följande är ett exempel på hur **PipelineVariable** fungerar. I det här exemplet läggs parametern **PipelineVariable** till i ett `Foreach-Object` kommando för att lagra resultatet av kommandot i variabler. Ett intervall med tal, 1 till 10, är skickas i det första `Foreach-Object` kommandot, vars resultat lagras i en variabel med namnet **Left**.

Resultatet från det första `Foreach-Object` kommandot är skickas i ett andra `Foreach-Object` kommando, som filtrerar objekten som returneras av det första `Foreach-Object` kommandot. Resultatet av det andra kommandot lagras i en variabel med namnet **Right**.

I det tredje `Foreach-Object` kommandot bearbetas resultaten av de första två `Foreach-Object` skickas-kommandona som representeras av variablerna **Left** och **Right**, med hjälp av en multiplikation-operator. Kommandot instruerar objekt som lagras i de **vänstra** och **högra** variablerna att multipliceras och anger att resultaten ska visas som "medlemmar i vänster intervall * höger intervall medlem = produkt".

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a>Verbose

Visar detaljerad information om den åtgärd som utförs av kommandot. Den här informationen liknar informationen i en spårning eller i en transaktions logg. Den här parametern fungerar bara när kommandot genererar ett utförligt meddelande. Den här parametern fungerar till exempel när ett kommando innehåller `Write-Verbose` cmdleten.

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

Den **utförliga** parametern åsidosätter värdet för `$VerbosePreference` variabeln för det aktuella kommandot. Eftersom standardvärdet för `$VerbosePreference` variabeln är **SilentlyContinue** visas inte utförliga meddelanden som standard.

`-Verbose:$true` har samma resultat som `-Verbose`

`-Verbose:$false` förhindrar visning av utförliga meddelanden. Använd den här parametern när värdet för `$VerbosePreference` inte är **SilentlyContinue** (standard).

#### <a name="warningaction"></a>WarningAction

Anger hur cmdleten svarar på en varning från kommandot. **Fortsätt** är standardvärdet. Den här parametern fungerar bara när kommandot genererar ett varnings meddelande. Den här parametern fungerar till exempel när ett kommando innehåller `Write-Warning` cmdleten.

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

Parametern **WarningAction** åsidosätter värdet för `$WarningPreference` variabeln för det aktuella kommandot. Eftersom standardvärdet för `$WarningPreference` variabeln **fortsätter** visas varningar och körningen fortsätter om du inte använder parametern **WarningAction** .

`-WarningAction:Continue` visar varnings meddelandena och fortsätter att köra kommandot. `Continue` används som standard.

`-WarningAction:Inquire` visar varnings meddelandet och du uppmanas att bekräfta innan du fortsätter körningen. Det här värdet används sällan.

`-WarningAction:SilentlyContinue` undertrycker varnings meddelandet och fortsätter att köra kommandot.

`-WarningAction:Stop` visar varnings meddelandet och stoppar körningen av kommandot.

> [!NOTE]
> Parametern **WarningAction** åsidosätter, men ersätter inte värdet för `$WarningAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.

#### <a name="warningvariable"></a>WarningVariable

Lagrar varningar om kommandot i den angivna variabeln.

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Alla genererade varningar sparas i variabeln även om varningarna inte visas för användaren.

Om du vill lägga till varningar i variabel innehållet, i stället för att ersätta eventuella varningar som redan är lagrade där, skriver du ett plus tecken ( `+` ) före variabel namnet.

Till exempel skapar följande kommando `$a` variabeln och lagrar sedan alla varningar:

```powershell
Get-Process -Id 6 -WarningVariable a
```

Följande kommando lägger till eventuella varningar till `$a` variabeln:

```powershell
Get-Process -Id 2 -WarningVariable +a
```

Följande kommando visar innehållet i `$a` :

```powershell
$a
```

Du kan använda den här parametern för att skapa en variabel som bara innehåller varningar från vissa kommandon. Du kan använda mat ris notation, till exempel `$a[0]` eller `$warning[1,2]` för att referera till vissa varningar som lagras i variabeln.

> [!NOTE]
> Varnings variabeln innehåller alla varningar som genererats av kommandot, inklusive varningar från anrop till kapslade funktioner eller skript.
### <a name="risk-management-parameter-descriptions"></a>Parameter beskrivningar för risk hantering

#### <a name="whatif"></a>WhatIf

Visar ett meddelande som beskriver kommandots effekter i stället för att köra kommandot.

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

Parametern **whatIf** åsidosätter värdet för `$WhatIfPreference` variabeln för det aktuella kommandot. Eftersom standardvärdet för `$WhatIfPreference` variabeln är 0 (inaktiverat), utförs inte **whatIf** -beteendet utan parametern **whatIf** . Mer information finns i [about_Preference_Variables](about_Preference_Variables.md)

`-WhatIf:$true` har samma resultat som `-WhatIf` .

`-WhatIf:$false` ignorerar det automatiska beteendet i WhatIf som resulterar i när värdet för `$WhatIfPreference` variabeln är 1.

Följande kommando använder till exempel `-WhatIf` parametern i ett `Remove-Item` kommando:

```powershell
Remove-Item Date.csv -WhatIf
```

I stället för att ta bort objektet, visar PowerShell de åtgärder som ska utföras och de objekt som skulle påverkas. Det här kommandot ger följande utdata:

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a>Bekräfta

Du uppmanas att bekräfta innan du kör kommandot.

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

Parametern **Confirm** åsidosätter värdet för `$ConfirmPreference` variabeln för det aktuella kommandot. Standardvärdet är True. Mer information finns i [about_Preference_Variables](about_Preference_Variables.md)

`-Confirm:$true` har samma resultat som `-Confirm` .

`-Confirm:$false` förhindrar automatisk bekräftelse, som inträffar när värdet för `$ConfirmPreference` är mindre än eller lika med den beräknade risken för cmdleten.

Följande kommando använder till exempel parametern **Confirm** med ett `Remove-Item` kommando. Innan objektet tas bort, visar PowerShell de åtgärder som skulle utföras och de objekt som skulle påverkas, och ber om godkännande.

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

Alternativen för att bekräfta svar är följande:

|Svarsåtgärder       |Resultat                                                     |
|---------------|-----------------------------------------------------------|
|Ja (Y)        |Utför åtgärden.                                        |
|Ja till alla (A) |Utföra alla åtgärder och utelämna efterföljande bekräfta-frågor|
|               |för det här kommandot.                                          |
|Nej (N):        |Utför inte åtgärden.                                 |
|Nej till alla (L): |Utför inga åtgärder och ignorera sedan efterföljande bekräftelse |
|               |frågor för det här kommandot.                                  |
|Pausa (S):   |Pausa kommandot och skapa en tillfällig session.          |
|Hjälp (?)       |Visa hjälp för de här alternativen.                            |

Alternativet **PAUSE** placerar kommandot stoppad och skapar en tillfällig kapslad session där du kan arbeta tills du är redo att välja ett **Bekräfta** -alternativ. Kommando tolken för den kapslade sessionen har två extra försiktighets åtgärder (>>) för att indikera att det är en underordnad åtgärd för det ursprungliga överordnade kommandot. Du kan köra kommandon och skript i den kapslade sessionen. Om du vill avsluta den kapslade sessionen och återgå till bekräfta-alternativen för det ursprungliga kommandot skriver du "Exit".

I följande exempel används **paus** alternativen för att stoppa ett kommando tillfälligt medan användaren kontrollerar hjälpen för en kommando parameter. När du har hämtat den information som behövs avslutar du den kapslade prompten och väljer Ja (y) som svar på bekräfta fråga.

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a>RESERVERADE

about_Common_Parameters

## <a name="see-also"></a>SE ÄVEN

[about_Preference_Variables](about_Preference_Variables.md)

[Skriv-debug](xref:Microsoft.PowerShell.Utility.Write-Debug)

[Skriv varning](xref:Microsoft.PowerShell.Utility.Write-Warning)

[Skriv-fel](xref:Microsoft.PowerShell.Utility.Write-Error)

[Skriv-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
