---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: Vad är PowerShell?
ms.openlocfilehash: 267b2938a0892c99c3a961bc7107f573df40a683
ms.sourcegitcommit: 38215ad49e237b219e62bb5a5f0eb3b6b048df1e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/27/2020
ms.locfileid: "83868487"
---
# <a name="what-is-powershell"></a>Vad är PowerShell?

PowerShell är en plattforms oberoende uppgift för automatisering och konfigurations hanterings ramverk, som består av ett kommando rads gränssnitt och skript språk. Till skillnad från de flesta Shell, som godkänner och returnerar text, bygger PowerShell på CLR (Common Language Runtime) för .NET och godkänner och returnerar .NET-objekt. Den här grundläggande ändringen ger helt nya verktyg och metoder för automatisering.

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a>Utdata är Object-baserad

Till skillnad från traditionella kommando rads gränssnitt är PowerShell-cmdletar utformade för att hantera objekt.
Ett objekt är strukturerad information som är mer än bara den sträng med tecken som visas på skärmen. Kommandoutdata innehåller alltid ytterligare information som du kan använda om du behöver den.

Om du har använt text bearbetnings verktyg för att bearbeta data tidigare kommer du att se att de fungerar annorlunda när de används i PowerShell. I de flesta fall behöver du inte text bearbetnings verktyg för att extrahera speciell information. Du får direkt åtkomst till delar av data med hjälp av standardsyntaxen för PowerShell-objekt.

## <a name="the-command-family-is-extensible"></a>Kommando serien är utöknings bar

Gränssnitt som `cmd.exe` inte ger dig möjlighet att direkt utöka den inbyggda kommando uppsättningen. Du kan skapa externa kommando rads verktyg som körs i `cmd.exe` . Men dessa externa verktyg saknar tjänster, till exempel hjälp integrering. `cmd.exe`känner inte automatiskt till att dessa externa verktyg är giltiga kommandon.

Kommandona i PowerShell kallas _cmdlets_. Du kan använda varje cmdlet separat, men deras effekt realiseras när du kombinerar dem för att utföra komplexa uppgifter. Precis som många gränssnitt ger PowerShell åtkomst till fil systemet på datorn. Med PowerShell- _providers_ kan du komma åt andra data lager, till exempel registret och certifikat Arkiv, så enkelt som du har åtkomst till fil systemet.

Du kan skapa egna cmdlet-och Function-moduler med hjälp av kompilerade kod eller skript. Moduler kan lägga till cmdlets och providers i gränssnittet. PowerShell stöder även skript som är likvärdiga med UNIX-Shell-skript och `cmd.exe` kommandofiler.

## <a name="support-for-command-aliases"></a>Stöd för kommando-alias

PowerShell stöder alias för att referera till kommandon med alternativa namn. Med aliasering kan användare i andra gränssnitt använda vanliga kommando namn som de redan känner till för liknande åtgärder i PowerShell.

Alias associerar ett nytt namn med ett annat kommando. PowerShell har till exempel en intern funktion med namnet `Clear-Host` som rensar utdatafönstret. Du kan ange antingen `cls` eller `clear` aliaset i en kommando tolk. PowerShell tolkar dessa alias och kör `Clear-Host` funktionen.

Den här funktionen hjälper användare att lära sig PowerShell. De flesta- `cmd.exe` och UNIX-användare har ett stort repertoaren kommandon som användare redan känner till med namn. PowerShell-motsvarigheterna kanske inte genererar identiska resultat. Resultaten är dock tillräckligt nära att användarna kan arbeta utan att känna till PowerShell-kommando namnet. "Muskel minne" är en annan stor källa för att lära sig ett nytt kommando gränssnitt. Om du har använt `cmd.exe` i år kan du ange `cls` kommandot för att rensa skärmen. Utan alias för `Clear-Host` får du ett fel meddelande och vet inte vad du ska göra för att rensa utdata.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell hanterar inmatade konsoler och visar

När du skriver ett kommando bearbetar PowerShell alltid kommando rads indatamängden direkt. PowerShell formaterar också utdata som visas på skärmen. Den här skillnaden är viktig eftersom den minskar det arbete som krävs för varje cmdlet. Det garanterar att du alltid kan göra saker på samma sätt med alla cmdletar. Cmdlet-utvecklare behöver inte skriva kod för att parsa kommando rads argumenten eller formatera utdata.

Traditionella kommando rads verktyg har egna scheman för att begära och Visa hjälp. Vissa kommando rads verktyg används `/?` för att utlösa hjälp visningen, andra använder `-?` , `/H` eller till och med `//` . Vissa visar hjälpen i ett GUI-fönster, i stället för i konsolens visning. Om du använder fel parameter kan verktyget ignorera det du skrev och börja köra en uppgift automatiskt.
Eftersom PowerShell automatiskt tolkar och bearbetar kommando raden `-?` betyder parametern alltid att visa mig hjälp för det här kommandot.

> [!NOTE]
> Om du kör ett grafiskt program i PowerShell öppnas fönstret för programmet.
> PowerShell inverkar bara vid bearbetning av kommando rads indata som du anger eller programutdata som returneras till konsol fönstret. Det påverkar inte hur programmet fungerar internt.

## <a name="powershell-has-a-pipeline"></a>PowerShell har en pipeline

Pipelines är utan tvekan det mest värdefulla konceptet som används i kommando rads gränssnitt. När den används korrekt minskar pipelinen arbetet med att använda komplexa kommandon och gör det lättare att se arbets flödet. Varje kommando i en pipeline skickar utdata, objekt efter objekt, till nästa kommando. Kommandon behöver inte hantera mer än ett objekt i taget. Resultatet är minskad resursförbrukning och möjligheten att få utdata direkt.

Den notation som används för pipelines liknar den notation som används i andra gränssnitt. I första hand kan det vara inte uppenbart hur pipelines skiljer sig i PowerShell. Även om du ser text på skärmen, PowerShell pipe-objekt, inte text, mellan kommandon.

Om du till exempel använder `Out-Host` cmdleten för att tvinga fram visning av utdata från ett annat kommando, ser utdata ut precis som den normala texten som visas på skärmen, och delas upp i sidor:

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

Växlingen minskar också processor användningen eftersom bearbetningen överförs till `Out-Host` cmdleten när en hel sida är klar att visas. Cmdletarna som föregår den i pipelinen pausar körningen tills nästa sida med utdata är tillgänglig.

### <a name="objects-in-the-pipeline"></a>Objekt i pipelinen

När du kör en cmdlet i PowerShell visas text utdata eftersom det är nödvändigt att representera objekt som text i ett konsol fönster. Text utmatningen kanske inte visar alla egenskaper för objektet som ska skrivas ut.

Överväg till exempel `Get-Location` cmdleten. Text utmatningen är en sammanfattning av informationen, inte en fullständig representation av det objekt som returnerades av `Get-Location` . Rubriken i utdata läggs till av processen som formaterar data för skärm visning.

```powershell
Get-Location
```

```Output
Path
----
C:\
```

Genom att skicka utdata till `Get-Member` cmdleten visas information om objektet som returnerades av `Get-Location` .

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location`Returnerar ett **PathInfo** -objekt som innehåller den aktuella sökvägen och annan information.

## <a name="built-in-help-system"></a>Inbyggt hjälpsystem

På samma sätt som UNIX `man` -sidor innehåller PowerShell detaljerade hjälp artiklar som förklarar PowerShell-begrepp och kommandosyntax. Använd cmdleten [Get-Help][] för att visa dessa artiklar i kommando tolken eller Visa de senaste uppdaterade versionerna av de här artiklarna i PowerShell-dokumentationen online.

## <a name="next-steps"></a>Nästa steg

Mer information om PowerShell finns i avsnittet **Learning PowerShell** på den här webbplatsen.

<!-- link references -->

[Get – hjälp]: /powershell/module/microsoft.powershell.core/Get-Help
