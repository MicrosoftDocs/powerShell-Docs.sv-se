---
ms.date: 10/13/2017
keywords: DSC, powershell, konfiguration, installation
title: Desired State Configuration-översikt för tekniker
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405368"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Desired State Configuration-översikt för tekniker

Det här dokumentet är avsett för utvecklare och åtgärder team att förstå fördelarna med PowerShell Desired State Configuration (DSC).
För en högre nivå vy av DSC-värdet erbjuder finns [Desired State Configuration-översikt för beslutsfattare](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Fördelarna med Desired State Configuration

DSC finns för att:

- Minska komplexiteten i skript i Windows
- Öka hastigheten på iteration

Begreppet ”kontinuerlig distribution” blir viktigare.
Kontinuerlig distribution innebär möjlighet att distribuera oftare och potentiellt många gånger per dag.
Syftet med dessa distributioner är inte att korrigera något, men att få något publicerade snabbt.
Genom att hämta nya funktioner via utveckling i drift som smidigt och på ett tillförlitligt sätt som möjligt, minska tiden till värde av nya affärslogik.

Övergången molnbaserad databehandling innebär en distributionslösning som använder en ”mall”-modell, där en end tillstånd miljö deklarerats som text och publiceras på en motor för distribution.
Den här distributionen tekniken kan snabba förändringar i skala, med flexibilitet mot risken för fel eftersom när som helst distributionen kan upprepas konsekvent för att garantera ett sluttillstånd.
Skapandet av verktyg och tjänster som stöder den här typen av åtgärder via automation är ett svar på dessa ändringar.

DSC är en plattform som ger deklarativ och idempotenta (upprepningsbara) distribution-, konfigurations- och efterlevnadsstatus.
DSC-plattformen gör det möjligt för dig att se till att komponenterna i ditt datacenter har rätt konfiguration, som undviker fel och förhindrar kostsamma distributionsfel.
DSC möjliggör kontinuerlig distribution genom att behandla DSC-konfigurationer som en del av programkoden.
DSC-konfigurationen ska uppdateras som en del av programmet, se till att den kunskap som krävs för att distribuera programmet alltid är uppdaterade och redo att användas.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>”Jag har PowerShell, varför behöver jag Desired State Configuration”?

DSC-konfigurationer separat avsikter och ”vad jag vill göra”, från körning eller ”hur jag vill göra det”.
Det innebär att logik körs finns i resurserna.
Användarna behöver inte vet hur du implementerar eller distribuera en funktion när en DSC-resurs för den funktionen är tillgänglig.
Detta gör att användaren kan fokusera på strukturen för deras distribution.

Till exempel PowerShell-skript ska se ut så här:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Det här skriptet är enkel, begripligt och enkelt.
Men om du placera skriptet i produktion, kör flera problem.
Vad händer om som skriptet körs två gånger i rad?
Vad händer om Bob tidigare hade fullständig åtkomst till resursen?

För att kompensera för de här problemen, ut en ”verklig” version av skriptet närmare till något som liknar:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Det här skriptet är mer komplex, med mycket logik och felhantering.
Skriptet är mer komplexa eftersom du inte längre om vad som du vill ha klar, men *gör så*.

DSC kan du till önskad text klar och den underliggande logiken har abstraherats direkt.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Det här skriptet är korrekt formaterad och enkelt att läsa.
Logik sökvägar och felhantering finns kvar i den [resource](../resources/resources.md) implementering, men osynlig till skriptförfattaren.

## <a name="separating-environment-from-structure"></a>Separera miljö från struktur

Ett vanligt mönster i DevOps är att ha flera miljöer för distribution.
Det kan till exempel finnas en ”” utvecklingsmiljö som används för att snabbt skapa prototyper ny kod.
Koden från ”utvecklingsmiljö” hamnar i en miljö med ”test”, där andra verifiera de nya funktionerna.
Slutligen hamnar koden i ”prod”- eller produktionsmiljön live-webbplatsen.

DSC-konfigurationer hantera denna dev-test-prod pipeline med [konfigurationsdata](../configurations/configData.md).
Detta ytterligare avlägsnar skillnaden mellan struktur för konfigurationen från de noder som ska hanteras.
Du kan till exempel definiera en konfiguration som kräver en SQLServer, en IIS-server och en mellannivå-server.
Oavsett vilka noder får de olika delarna av den här konfigurationen kan kommer dessa tre element alltid att finnas.
Du kan använda konfigurationsdata för alla tre element för samma dator för en utvecklingsmiljö, separat tre element på tre olika datorer för en testmiljö och slutligen på alla produktionsservrar prod-miljön.
Om du vill distribuera till olika miljöer, kan du anropa **Start-DscConfiguration** med rätt konfigurationsdata för den miljö som du vill använda.

## <a name="see-also"></a>Se även

[Konfigurationer](../configurations/configurations.md)

[Konfigurationsdata](../configurations/configData.md)

[Resurser](../resources/resources.md)
