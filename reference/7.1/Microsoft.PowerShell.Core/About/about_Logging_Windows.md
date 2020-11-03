---
description: PowerShell loggar interna åtgärder från motorn, providers och cmdlets.
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: dbc11e15642673d3159d4f02a40147e68fbf1d7d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269865"
---
# <a name="about-logging-windows"></a>Om loggning av Windows

## <a name="short-description"></a>Kort beskrivning

PowerShell loggar interna åtgärder från motorn, providers och cmdlets.

## <a name="long-description"></a>Lång beskrivning

PowerShell loggar information om PowerShell-åtgärder, till exempel starta och stoppa motorn och providers och köra PowerShell-kommandon.

> [!NOTE]
> Windows PowerShell-versionerna 3,0, 4,0, 5,0 och 5,1 innehåller **EventLog** -cmdletar för Windows-händelseloggarna. I dessa versioner för att visa listan över cmdletar för **händelse loggen** skriver du: `Get-Command -Noun EventLog` . Mer information finns i cmdlet-dokumentationen och about_EventLogs för din version av Windows PowerShell.

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a>Visa poster i PowerShell-händelseloggen i Windows

PowerShell-loggar kan visas med hjälp av Windows Loggboken. Händelse loggen finns i gruppen program-och tjänst loggar och har namnet `PowerShellCore` . Den tillhör ande ETW-providern `GUID` är `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` .

När skript block loggning är aktiverat loggar PowerShell följande händelser i `PowerShellCore/Operational` loggen:

|Fält| Värde|
|-|-|
|EventId|`4104` / `0x1008`|
|Kanal|`Operational`|
|Nivå|`Verbose`|
|Opcode|`Create`|
|Uppgift|`CommandStart`|
|Följt|`Runspace`|

### <a name="registering-the-powershell-event-provider-on-windows"></a>Registrera PowerShell-Händelseprovidern i Windows

Till skillnad från Linux eller macOS kräver Windows att Händelseprovidern registreras innan händelser kan skrivas till händelse loggen. Aktivera PowerShell-Händelseprovidern genom att köra följande kommando från en upphöjd PowerShell-kommandotolk.

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a>Avregistrerar PowerShell-Händelseprovidern i Windows

När du registrerar händelse leverantören placeras ett lås i det binära biblioteket som används för att avkoda händelser. För att kunna uppdatera det här biblioteket måste providern avregistreras för att låsa upp det här låset.

Om du vill avregistrera PowerShell-providern kör du följande kommando från en upphöjd PowerShell-kommandotolk.

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

När du har uppdaterat PowerShell kör `$PSHOME\RegisterManifest.ps1` du för att registrera den uppdaterade Händelseprovidern.

## <a name="enabling-script-block-logging"></a>Aktivera skript Blocks loggning

När du aktiverar skript Blocks loggning registrerar PowerShell innehållet i alla skript block som den bearbetar. När en ny PowerShell-session har Aktiver ATS loggar den här informationen.

> [!NOTE]
> Vi rekommenderar att du aktiverar skyddad händelse loggning, enligt beskrivningen nedan, när du använder skript Blocks loggning för något annat än diagnostiskt syfte.

Loggning av skript block kan aktive ras via grupprincip eller en register inställning.

### <a name="using-group-policy"></a>Använda grupprincip

Aktivera automatisk avskrift genom att aktivera `Turn on PowerShell Script Block
Logging` funktionen i Grupprincip via `Administrative Templates -> Windows
Components -> Windows PowerShell` .

### <a name="using-the-registry"></a>Använda registret

Kör följande funktion:

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a>Skyddad händelse loggning

Att öka loggnings nivån på ett system ökar risken för att loggat innehåll kan innehålla känsliga data. Med skript loggning aktive rad kan exempelvis autentiseringsuppgifter eller andra känsliga data som används av ett skript skrivas till händelse loggen. När en dator som har loggat känsliga data komprometteras, kan loggarna tillhandahålla en angripare med information som behövs för att utöka sin räckvidd.

För att skydda den här informationen introducerar Windows 10 skyddad händelse loggning.
Med skyddad händelse loggning kan deltagande program Kryptera känsliga data som skrivs till händelse loggen. Senare kan du dekryptera och bearbeta dessa loggar på en säkrare och centraliserad logg insamlare.

Innehållet i händelse loggen skyddas med hjälp av standard-CMS (Cryptographic Message Syntax) i IETF. CMS använder kryptering med offentlig nyckel. Nycklar som används för att kryptera innehåll och dekryptera innehåll hålls åtskilda.

Den offentliga nyckeln kan delas mycket och är inte känslig för data. Allt innehåll som krypteras med den här offentliga nyckeln kan bara dekrypteras av den privata nyckeln. Mer information om kryptering med offentliga nycklar finns i [Wikipedia-offentlig nyckel kryptering](https://en.wikipedia.org/wiki/Public-key_cryptography).

Om du vill aktivera en princip för en skyddad händelse loggning distribuerar du en offentlig nyckel till alla datorer som har händelse logg data som ska skyddas. Motsvarande privata nyckel används för att efter bearbetning av händelse loggarna på en säkrare plats, till exempel en central händelse logg insamlare eller [Siem][] Aggregator. Du kan konfigurera SIEM i Azure. Mer information finns i [allmän Siem-integrering](/cloud-app-security/siem).

### <a name="enabling-protected-event-logging-via-group-policy"></a>Aktivera skyddad händelse loggning via grupprincip

Aktivera skyddad händelse loggning genom att aktivera `Enable Protected Event Logging` funktionen i Grupprincip via `Administrative Templates -> Windows Components
-> Event Logging` . Den här inställningen kräver ett krypterings certifikat, som du kan ange i ett av flera formulär:

- Innehållet i ett Base-64-kodat X. 509-certifikat (till exempel som erbjuds av `Export` alternativet i certifikat hanteraren).
- Tumavtrycket för ett certifikat som finns i den lokala datorns certifikat arkiv (kan distribueras av PKI-infrastrukturen).
- Den fullständiga sökvägen till ett certifikat (kan vara lokal eller en fjär resurs).
- Sökvägen till en katalog som innehåller ett certifikat eller certifikat (kan vara lokalt eller en fjär resurs).
- Ämnes namnet för ett certifikat som kan hittas i den lokala datorns certifikat arkiv (kan distribueras av PKI-infrastrukturen).

Det resulterande certifikatet måste ha `Document Encryption` som en förbättrad nyckel användning ( `1.3.6.1.4.1.311.80.1` ) och antingen `Data Encipherment` eller `Key
Encipherment` nyckel användningen aktiverade.

> [!WARNING]
> Den privata nyckeln bör inte distribueras till datorns loggnings händelser. Den bör behållas på en säker plats där du dekrypterar meddelandena.

### <a name="decrypting-protected-event-logging-messages"></a>Dekryptera meddelanden om skyddade händelser

Följande skript kommer att hämta och dekryptera, förutsatt att du har den privata nyckeln:

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a>Se även

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[PowerShell det blå teamet](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[Allmän SIEM-integration](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management

