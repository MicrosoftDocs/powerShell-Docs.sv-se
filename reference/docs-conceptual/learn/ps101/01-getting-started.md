---
title: Komma igång med PowerShell
description: Var du hittar och hur du startar PowerShell för nya användare.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 0f72fb5baf5b829142b18ed774261e9b3b66291b
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436332"
---
# <a name="chapter-1---getting-started-with-powershell"></a>Kapitel 1 – Komma igång med PowerShell

Jag upptäcker ofta att presentatörer på konferenser och användar grupps möten redan har PowerShell igång när de startar ingångs nivå presentationer. Den här boken börjar genom att besvara frågorna som jag har hört deltagare som inte tidigare har använt PowerShell fråga i dessa sessioner.

I detta kapitel fokuserar vi på att söka efter och starta PowerShell och lösa några av de inledande problemen som nya användare upplever med PowerShell. Se till att följa med och gå igenom exemplen som visas i det här kapitlet på Windows 10 labb miljö datorn.

## <a name="what-do-i-need-to-get-started-with-powershell"></a>Vad behöver jag för att komma igång med PowerShell?

Alla moderna versioner av Windows-operativsystem levereras med PowerShell installerat. Om du kör en version som är äldre än 5,1 bör du installera den senaste versionen.

- Information om hur du uppgraderar till Windows PowerShell 5,1 finns i [uppgradera befintliga Windows PowerShell][]
- Information om hur du installerar den senaste versionen av PowerShell finns i [Installera PowerShell][]

## <a name="where-do-i-find-powershell"></a>Var hittar jag PowerShell?

Det enklaste sättet att hitta PowerShell i Windows 10 är att skriva **PowerShell** i Sök fältet som visas i bild 1-1.

![Figur 1-1](media/figure1-1.png)

Observera att fyra olika kortkommandon för PowerShell visas i bild 1-1. Datorn som används i demonstrations syfte i den här boken kör 64-bitars versionen av Windows 10, så det finns en 64-bitars version av PowerShell-konsolen och PowerShell ISE (Integrated Scripting Environment) och en 32-bitars version av var och en som anges av (x86)-suffixet i gen vägarna. Om du råkar köra en 32-bitars version av Windows 10 har du bara två genvägar. Dessa objekt har inte (x86) suffix, men är 32-bitars versioner. Om du har ett 64-bitars operativ system är min rekommendation att köra 64-bitars versionen av PowerShell, om du inte har en unik orsak för att köra 32-bitars versionen.

Information om hur du startar PowerShell i andra versioner av Windows finns i [Starta Windows PowerShell][].

## <a name="how-do-i-launch-powershell"></a>Hur gör jag för att starta PowerShell?

I produktions företags miljöer som jag stöder använder jag tre olika Active Directory-användarkonton. Jag har speglat dessa konton i labb miljön som används i den här boken. Jag loggar in på Windows 10-datorn som en domän användare som inte är en domän eller lokal administratör.

Jag har lanserat PowerShell-konsolen genom att klicka på genvägen "Windows PowerShell" som visas i bild 1-1.

![Figur 1-4](media/figure1-4.png)

Observera att PowerShell-konsolens namn List säger "Windows PowerShell" som visas i bild 1-4. Vissa kommandon fungerar bra, men PowerShell kan inte delta i användar Access Control (UAC). Det innebär att det inte går att fråga efter utökad behörighet för uppgifter som kräver godkännande av en administratör.
Följande fel meddelande genereras:

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

Lösningen på det här problemet är att köra PowerShell som en domän användare som är en lokal administratör.
Så här konfigureras mitt andra domän användar konto. Det här kontot bör inte vara en domän administratör eller ha utökade privilegier i domänen.

Stäng PowerShell. Starta om PowerShell-konsolen, förutom den här gången, högerklicka på genvägen **Windows PowerShell** och välj **Kör som administratör** enligt bilden 1-5.

![Figur 1-5](media/figure1-5.png)

Om du är inloggad på Windows som en vanlig användare uppmanas du att ange autentiseringsuppgifter. Jag anger autentiseringsuppgifterna för mitt användar konto som är domän användare och lokal administratör enligt bild 1-6.

![Figur 1-6](media/figure1-6.png)

När PowerShell startas om som administratör ska namn listen stå "administratör: Windows PowerShell" som visas i bild 1-7.

![Figur 1-7](media/figure1-7.png)

Nu när PowerShell körs upphöjt till en lokal administratör kommer UAC inte längre att vara ett problem när ett kommando körs på den lokala datorn som normalt skulle kräva en uppmaning om utökade privilegier. Tänk på att alla kommandon som körs från den här upphöjda instansen av PowerShell-konsolen också körs med förhöjd behörighet.

För att förenkla sökning av PowerShell och starta den som administratör rekommenderar vi att du fäster den i aktivitets fältet och ställer in den så att den startar automatiskt som en administratör varje gången den körs.

Sök efter PowerShell igen, förutom den här gången högerklickar du på den och väljer Fäst på aktivitets fältet som visas i bild 1-8.

![Figur 1-8](media/figure1-8.png)

Högerklicka på PowerShell-genvägen som nu har fästs i aktivitets fältet och välj egenskaper som visas i bild 1-9.

![Figur 1-9](media/figure1-9.png)

Klicka på "Avancerat" som antecknas genom att #1 i bild 1-10, markera kryss rutan Kör som administratör som betecknas genom att #2 i bild 1-10 och klicka sedan på OK två gånger för att acceptera ändringarna och avsluta från båda dialog rutorna.

![Figur 1-10](media/figure1-10.png)

Du behöver aldrig bekymra dig om att hitta PowerShell eller om den körs som administratör igen.

Att köra PowerShell som administratör för att förhindra problem med UAC påverkar bara kommandon som körs mot den lokala datorn. Den har ingen påverkan på kommandon som är riktade till fjärrdatorer.

## <a name="what-version-of-powershell-am-i-running"></a>Vilken version av PowerShell körs?

Det finns ett antal automatiska variabler i PowerShell som lagrar statusinformation. En av dessa variabler är `$PSVersionTable` , som innehåller en hash-modul som kan användas för att visa relevant information om PowerShell-version:

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Nyare versioner av Windows PowerShell distribueras som en del av Windows Management Framework (WMF). En angiven version av .NET Framework krävs beroende på WMF-versionen. Information om hur du uppgraderar till Windows PowerShell 5,1 finns i [uppgradera befintliga Windows PowerShell][].

## <a name="execution-policy"></a>Körnings princip

Till skillnad från populär tro är körnings principen i PowerShell inte en säkerhets gränser. Den är utformad för att hindra en användare från att känna sig osäker på att köra ett skript. En bestämd användare kan enkelt kringgå körnings principen i PowerShell. Tabell 1-2 visar standard körnings principen för aktuella Windows-operativsystem.

| Operativ system version för Windows | Standard körnings princip |
| -------------------------------- | ------------------------ |
| Server 2019                      | Fjärran sluten signerad            |
| Server 2016                      | Fjärran sluten signerad            |
| Windows 10                       | Begränsade               |

Oavsett inställningen för körnings principen kan alla PowerShell-kommandon köras interaktivt. Körnings principen påverkar bara kommandon som körs i ett skript. `Get-ExecutionPolicy`Cmdleten används för att avgöra vad den aktuella körnings princip inställningen är och att `Set-ExecutionPolicy` cmdleten används för att ändra körnings principen. Min rekommendation är att använda **RemoteSigned** -principen, som kräver att hämtade skript signeras av en betrodd utgivare för att kunna köras.

Kontrol lera den aktuella körnings principen:

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

PowerShell-skript kan inte köras alls när körnings principen är inställd på **begränsad**. Detta är standardinställningen på alla Windows-klientens operativ system. För att demonstrera problemet sparar du följande kod som en `.ps1` fil med namnet `Stop-TimeService.ps1` .

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

Kommandot körs interaktivt utan fel så länge PowerShell körs upphöjt till en administratör. Men så snart det sparas som en skript fil och du försöker köra skriptet, genererar det ett fel:

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

Observera att det fel som visas i den föregående uppsättningen resultat visar exakt vad problemet är (körning av skript är inaktiverat i systemet). När du kör ett kommando i PowerShell som genererar ett fel meddelande, bör du läsa fel meddelandet i stället för att bara köra kommandot och lura som körs.

Ändra PowerShell-körnings principen till fjärran sluten signerad.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

Se till att läsa varningen som visas när du ändrar körnings principen. Jag rekommenderar också att ta en titt på [about_Execution_Policies][] hjälp avsnittet och se till att du förstår säkerhets konsekvenserna av att ändra körnings principen.

Nu när körnings principen har ställts in på **RemoteSigned** `Stop-TimeService.ps1` Kör skriptet fel kostnads fritt.

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

Se till att starta tids tjänsten för Windows innan du fortsätter annars kan du stöta på oförutsedda problem.

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig hur du hittar och startar PowerShell och hur du skapar en genväg som startar PowerShell som administratör. Du har också lärt dig om standard körnings principen och hur du ändrar den.

## <a name="review"></a>Granska

1. Hur tar du reda på vilken PowerShell-version en dator kör?
1. Varför är det viktigt att starta PowerShell som administratör?
1. Hur avgör du den aktuella PowerShell-körnings principen?
1. Vad hindrar standard körnings principen för PowerShell på Windows-klientdatorer från att ske?
1. Hur ändrar du körnings principen för PowerShell?

## <a name="recommended-reading"></a>Rekommenderad läsning

För dem som vill veta mer om de ämnen som beskrivs i det här kapitlet rekommenderar vi att du läser följande PowerShell-hjälp avsnitt.

- [about_Automatic_Variables][]
- [about_Execution_Policies][]

I nästa kapitel får du lära dig mer om hur du kan hitta kommandon i PowerShell. Ett av de saker som kommer att omfattas är hur du uppdaterar PowerShell så att hjälp avsnitten kan visas direkt från PowerShell i stället för att behöva visa dem på Internet.

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Execution_Policies]: /powershell//powershell/module/microsoft.powershell.core/about/about_execution_policies
[Uppgradera befintliga Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Installera PowerShell]: /powershell/scripting/install/installing-powershell
[Starta Windows Powershell]: /powershell/scripting/windows-powershell/starting-windows-powershell
