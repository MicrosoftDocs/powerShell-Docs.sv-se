---
ms.date: 10/13/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Desired State Configuration-översikt för tekniker
description: Det här dokumentet är avsett för utvecklare och drifts team för att förstå fördelarna med PowerShell-tjänsten för önskad tillstånds konfiguration (DSC).
ms.openlocfilehash: c98295d0e78f4dc89e5df429e3c1de9a0c024054
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646940"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Desired State Configuration-översikt för tekniker

Det här dokumentet är avsett för utvecklare och drifts team för att förstå fördelarna med PowerShell-tjänsten för önskad tillstånds konfiguration (DSC). Om du vill visa en högre nivå av värdet DSC kan du läsa [Översikt över önskad tillstånds konfiguration för besluts fattare](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Fördelar med önskad tillstånds konfiguration

DSC finns för att:

- Minska komplexiteten i skript i Windows
- Öka upprepnings hastigheten

Begreppet "kontinuerlig distribution" blir viktigare. Kontinuerlig distribution innebär att du kan distribuera oftare, potentiellt många gånger per dag. Syftet med dessa distributioner är inte att åtgärda något men för att få något publicerat snabbt. Genom att få nya funktioner genom utveckling i drift så smidigt och tillförlitligt som möjligt minskar du tiden till värde för nya affärs logik.

Flytten till molnbaserad data behandling innebär en distributions lösning som använder en "deklarativ" mall modell, där en slut tillstånds miljö deklareras som text och publiceras till en distributions motor. Med den här distributions tekniken kan du snabbt ändra i skala, med återhämtning mot hot om felet, eftersom distributionen kan upprepas kontinuerligt för att garantera ett slut tillstånd. Att skapa verktyg och tjänster som har stöd för den här typen av åtgärder via automatisering är ett svar på dessa ändringar.

DSC är en plattform som tillhandahåller deklarativ och idempotenta (repeterbart) distribution, konfiguration och överensstämmelse. DSC-plattformen gör det möjligt för dig att se till att komponenterna i data centret har rätt konfiguration, vilket undviker fel och förhindrar kostsamma distributions fel. Genom att behandla DSC-konfigurationer som en del av program koden, aktiverar DSC kontinuerlig distribution. DSC-konfigurationen bör uppdateras som en del av programmet, vilket säkerställer att den kunskap som krävs för att distribuera programmet alltid är uppdaterad och redo att användas.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Jag har PowerShell, varför behöver jag önskad tillstånds konfiguration?"

DSC-konfigurationer, separata avsikter, eller "vad jag vill göra", från körning eller "hur jag vill göra det". Det innebär att logiken för körningen ingår i resurserna. Användarna behöver inte veta hur de ska implementera eller distribuera en funktion när en DSC-resurs för den funktionen är tillgänglig. Detta gör att användaren kan fokusera på strukturen i distributionen.

Som exempel bör PowerShell-skript se ut så här:

```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```

Det här skriptet är enkelt, begripligt och enkelt. Men om du försöker sätta skriptet i produktion, kan du köra på flera problem. Vad händer om skriptet körs två gånger i rad? Vad händer om Bob tidigare hade fullständig åtkomst till resursen?

För att kompensera för de här problemen ser en "verklig" version av skriptet att se ut ungefär så här:

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
    New-SmbShare @PSBoundParameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($PSBoundParameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Det här skriptet är mer komplicerat, med massor av logik-och fel hantering. Skriptet är mer komplicerat eftersom du inte längre anger vad du vill göra, men _hur du gör det_ .

DSC låter dig säga vad du vill göra och den underliggande logiken är indelad.

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

Det här skriptet är rent formaterat och enkelt att läsa.
Logik Sök vägar och fel hantering finns kvar i [resurs](../resources/resources.md) implementeringen, men är osynliga för skript författaren.

## <a name="separating-environment-from-structure"></a>Separera miljö från struktur

Ett vanligt mönster i DevOps är att ha flera miljöer för distribution. Det kan till exempel finnas en "dev"-miljö som används för att snabbt kunna prototypa ny kod. Koden från "dev"-miljön hamnar i en test miljö där andra personer verifierar de nya funktionerna. Slutligen hamnar koden i "Prod" eller The Live site Production Environment.

DSC-konfigurationer hanterar den här dev-test-Prod-pipeline genom att använda [konfigurations data](../configurations/configData.md).
Detta sammanfattar skillnaden mellan konfigurationens struktur och de noder som hanteras. Du kan till exempel definiera en konfiguration som kräver en SQL-Server, en IIS-server och en server på mellan nivå. Oavsett vilka noder som tar emot olika delar av den här konfigurationen, kommer dessa tre element alltid att finnas. Du kan använda konfigurations data för att peka alla tre element mot samma dator för en utvecklings miljö, separera de tre elementen till tre olika datorer för en test miljö och slutligen till alla produktions servrar för produktions miljön. Om du vill distribuera till olika miljöer kan du anropa `Start-DscConfiguration` med rätt konfigurations data för den miljö som du vill använda som mål.

## <a name="see-also"></a>Se även

[Konfigurationer](../configurations/configurations.md)

[Konfigurationsdata](../configurations/configData.md)

[Resurser](../resources/resources.md)
