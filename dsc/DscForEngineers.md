---
ms.date: 10/13/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Desired State Configuration-översikt för beslutsfattare
ms.openlocfilehash: 3d2d4b7e09fb699751151d7af641410bae3b38a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Desired State Configuration-översikt för tekniker

Det här dokumentet är avsett för utvecklare och åtgärder team att förstå fördelarna med PowerShell önskad tillstånd Configuration DSC ().
För en högre nivå vy av DSC-värdet innehåller finns [Desired Configuration översikt över för beslutsfattare](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Fördelarna med önskad Tillståndskonfiguration

DSC finns på:

- Minska komplexiteten över skript i Windows
- Öka hastigheten för upprepning

Begreppet ”kontinuerlig distribution” har blivit viktigare.
Kontinuerlig distribution innebär möjlighet att distribuera ofta, kan vara för många gånger per dag.
Syftet med dessa distributioner är inte att fastställa något utan att hämta något publicerade snabbt.
Genom att hämta nya funktioner via utveckling i drift så smidigt och på ett tillförlitligt sätt som möjligt, minska tid-värde för affärslogik på nytt.

Övergången cloud computing-lösningar innebär en distributionslösning för som använder en modell för ”deklarativ” mall, där en end tillstånd miljö har deklarerats som text och publiceras på en motor för distribution.
Den här distributionen tekniken ger snabb ändra, i skala, med återhämtning mot risken för fel eftersom när som helst distributionen kan konsekvent upprepas för att garantera en end-tillstånd.
Verktyg och tjänster som stöder den här typen av åtgärder med hjälp av automation skapas ett svar på dessa ändringar.

DSC är en plattform som tillhandahåller deklarativ och idempotent (repeterbara) distribution, konfiguration och överensstämmelse.
DSC-plattformen gör det möjligt för dig att se till att komponenterna i ditt datacenter har rätt konfiguration, vilket förhindrar fel och förhindrar att kostsamma distributionsfel.
Genom att behandla DSC-konfigurationer som en del av programkoden kan DSC kontinuerlig distribution.
DSC-konfigurationen ska uppdateras som en del av programmet, se till att informationen som krävs för att distribuera programmet alltid är uppdaterade och redo att användas.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>”Jag har PowerShell, varför behöver Desired State Configuration”?

DSC-konfigurationer separat avsikter och ”vad jag vill”, från körning eller ”hur jag vill göra det”.
Det innebär att logiken för körning av finns i resurserna.
Användare behöver inte känna till hur du implementerar eller distribuera en funktion när en DSC-resurs för funktionen är tillgänglig.
Detta används att fokusera på strukturen för deras distribution.

Exempelvis PowerShell-skript ska se ut så här:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Det här skriptet är enkla lättförståeliga och enkelt.
Men om du försöker att skriptet till produktion, stöter på problem med flera.
Vad händer om skriptet körs två gånger i rad?
Vad händer om Bob tidigare hade fullständig åtkomst till resursen?

För att kompensera för de här problemen, ser en ”verkliga” version av skriptet närmare något som liknar:
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

Det här skriptet är mer komplexa, med mycket logik och felhantering.
Skriptet är mer komplex eftersom du inte längre om vad du vill klart, men *gör du*.

DSC kan du önskad text klart och den underliggande logiken representeras direkt.

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
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Det här skriptet är korrekt formaterad och enkla att läsa.
Logik sökvägar och felhantering finns kvar i den [resurs](resources.md) implementeringen, men osynlig till skriptet författare.

## <a name="separating-environment-from-structure"></a>Avgränsa miljön från struktur

Ett vanligt mönster i DevOps är att ha flera miljöer för distribution.
Det kan till exempel finnas en ”utvecklingsmiljö”, används för att snabbt prototyp ny kod.
Koden från ”utvecklingsmiljö” försätts i ett ”test”-miljö där andra verifiera de nya funktionerna.
Slutligen blir koden ”prod” eller liveplatsen produktionsmiljön.

DSC-konfigurationer hantera denna dev-test-produktprenumeration pipeline med [konfigurationsdata](configData.md).
Detta ytterligare avlägsnar skillnaden mellan strukturen för konfiguration av de noder som ska hanteras.
Du kan till exempel definiera en konfiguration som kräver en SQLServer, en IIS-server och en mellannivå-server.
Oavsett vilka noder får olika delar av den här konfigurationen, är dessa tre element alltid tillgänglig.
Du kan använda konfigurationsdata för alla tre element för samma dator för en utvecklingsmiljö separat av tre element till tre olika datorer för en testmiljö och slutligen mot alla produktionsservrar för prod-miljö.
Om du vill distribuera till olika miljöer, kan du anropa **Start DscConfiguration** med rätt konfigurationsdata för den miljö du vill använda som mål.

## <a name="see-also"></a>Se även

[Konfigurationer](configurations.md)

[Konfigurationsdata](configData.md)

[Resurser](resources.md)