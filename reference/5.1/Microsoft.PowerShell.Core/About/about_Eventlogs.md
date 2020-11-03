---
description: Windows PowerShell skapar en Windows-händelseloggen med namnet "Windows PowerShell" för att registrera Windows PowerShell-händelser. Du kan visa den här loggen i Loggboken eller genom att använda cmdlets som hämtar händelser, t `Get-EventLog` . ex. cmdleten. Som standard registreras Windows PowerShell-motor och-Provider-händelser i händelse loggen, men du kan använda variablerna för händelse loggen för att anpassa händelse loggen. Du kan till exempel lägga till händelser om Windows PowerShell-kommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272156"
---
# <a name="about-eventlogs"></a>Om EventLogs

## <a name="short-description"></a>Kort beskrivning

Windows PowerShell skapar en Windows-händelseloggen med namnet "Windows PowerShell" för att registrera Windows PowerShell-händelser. Du kan visa den här loggen i Loggboken eller genom att använda cmdlets som hämtar händelser, t `Get-EventLog` . ex. cmdleten. Som standard registreras Windows PowerShell-motor och-Provider-händelser i händelse loggen, men du kan använda variablerna för händelse loggen för att anpassa händelse loggen. Du kan till exempel lägga till händelser om Windows PowerShell-kommandon.

## <a name="long-description"></a>Lång beskrivning

Händelse loggen i Windows PowerShell registrerar information om Windows PowerShell-åtgärder, till exempel starta och stoppa program motorn och starta och stoppa Windows PowerShell-providers. Du kan också logga information om Windows PowerShell-kommandon.

Händelse loggen för Windows PowerShell finns i gruppen program-och tjänst loggar. Windows PowerShell-loggen är en klassisk händelse logg som inte använder Windows Eventing-teknik. Om du vill visa loggen använder du cmdletarna som har utformats för klassiska händelse loggar, till exempel `Get-EventLog` .

## <a name="viewing-the-windows-powershell-event-log"></a>Visa händelse loggen för Windows PowerShell

Du kan visa händelse loggen för Windows PowerShell i Loggboken eller genom att `Get-EventLog` använda `Get-WmiObject` cmdletarna och. Om du vill visa innehållet i Windows PowerShell-loggen skriver du:

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

Om du vill undersöka händelserna och deras egenskaper använder du `Sort-Object` cmdleten, `Group-Object` cmdleten och cmdletarna som innehåller `Format` verbet ( `Format` cmdletarna).

Om du till exempel vill visa händelserna i loggen grupperade efter händelse-ID, skriver du:

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

Eller skriv:

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

Om du vill visa alla klassiska händelse loggar skriver du:

```powershell
Get-EventLog -List
```

Du kan också använda `Get-WmiObject` cmdleten för att använda Event-relaterade Windows Management Instrumentation (WMI)-klasser för att undersöka händelse loggen. Om du till exempel vill visa alla egenskaper för händelse logg filen skriver du:

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

Du hittar Win32 Event-relaterade WMI-klasser genom att skriva:

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

Om du vill ha mer information skriver du "Get-Help get-EventLog" och "Get-Help get-WmiObject".

## <a name="selecting-events-for-the-windows-powershell-event-log"></a>Välja händelser för händelse loggen i Windows PowerShell

Du kan använda variablerna för inställning av händelse logg för att avgöra vilka händelser som registreras i händelse loggen i Windows PowerShell.

Det finns sex variabler för händelse logg inställningar. två variabler för var och en av de tre loggnings komponenterna: motorn (Windows PowerShell-program), providers och kommandona. LifeCycleEvent-variablerna loggar normal start och stopp av händelser. Fel händelser för loggen för hälso tillstånd.

I följande tabell visas variablerna för händelse logg inställningar.

|Variabel                  |Beskrivning                                    |
|--------------------------|-----------------------------------------------|
|$LogEngineLifeCycleEvent  |Loggar start och stopp av PowerShell          |
|$LogEngineHealthEvent     |Loggar PowerShell-program fel                 |
|$LogProviderLifeCycleEvent|Loggar start och stopp för PowerShell-leverantörer|
|$LogProviderHealthEvent   |Loggar PowerShell-providerfelmeddelandet                |
|$LogCommandLifeCycleEvent |Loggar start och slut för ande av kommandon   |
|$LogCommandHealthEvent    |Loggar kommando fel                            |

(Information om Windows PowerShell-providers finns i [about_Providers](about_Providers.md).)

Som standard är endast följande händelse typer aktiverade:

* $LogEngineLifeCycleEvent
* $LogEngineHealthEvent
* $LogProviderLifeCycleEvent
* $LogProviderHealthEvent

Om du vill aktivera en händelse typ anger du variabeln Preference för den händelse typen till $true. Om du till exempel vill aktivera kommando livs cykel händelser skriver du:

```powershell
$LogCommandLifeCycleEvent
```

Eller skriv:

```powershell
$LogCommandLifeCycleEvent = $true
```

Om du vill inaktivera en händelse typ anger du variabeln Preference för den händelse typen till $false. Om du till exempel vill inaktivera kommando livs cykel händelser skriver du:

```powershell
$LogProviderLifeCycleEvent = $false
```

Du kan inaktivera vilken händelse som helst, förutom de händelser som indikerar att Windows PowerShell-motorn och Core-providern har startats. Dessa händelser genereras innan Windows PowerShell-profilerna körs och innan värd programmet kan ta emot kommandon.

Variabel inställningarna gäller endast för den aktuella Windows PowerShell-sessionen.
Om du vill tillämpa dem på alla Windows PowerShell-sessioner lägger du till dem i Windows PowerShell-profilen.

## <a name="logging-module-events"></a>Loggning av module-händelser

Från och med Windows PowerShell 3,0 kan du registrera körnings händelser för cmdlets och Functions i Windows PowerShell-moduler och snapin-moduler genom att ange egenskapen LogPipelineExecutionDetails för moduler och snapin-moduler till sant. Den här funktionen är endast tillgänglig för snapin-moduler i Windows PowerShell 2,0.

När värdet för egenskapen LogPipelineExecutionDetails är TRUE ( `$true` ), skriver Windows PowerShell cmdlet-och Function-körningarna i sessionen till Windows PowerShell-loggen i Loggboken. Inställningen är endast effektiv i den aktuella sessionen.

Om du vill aktivera loggning av körnings händelser av cmdletar och funktioner i en modul använder du följande kommandosekvens.

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

Om du vill aktivera loggning av körnings händelser av cmdletar i en snapin-modul använder du följande kommandosekvens.

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

Om du vill inaktivera loggning använder du samma kommando sekvens för att ange värdet FALSKT () för egenskap svärdet `$false` .

Du kan också använda grupprincip inställningen "Aktivera loggning av modul" för att aktivera och inaktivera modul-och snapin-loggning. Princip svärdet innehåller en lista över modul-och snapin-namn. Jokertecken stöds.

När "Aktivera loggning av modul" har angetts för en modul är värdet för LogPipelineExecutionDetails-egenskapen i modulen sann i alla sessioner och kan inte ändras.

Grup princip inställningen Aktivera modul loggning finns i följande grupprincip sökvägar:

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

Användar konfigurations principen har företräde framför princip för dator konfiguration och båda principerna har företräde framför värdet för egenskapen LogPipelineExecutionDetails för moduler och snapin-moduler.

Mer information om den här grupprincip inställningen finns i [about_Group_Policy_Settings](about_Group_Policy_Settings.md).

## <a name="security-and-auditing"></a>Säkerhet och granskning

Händelse loggen i Windows PowerShell är utformad för att indikera aktivitet och för att ge drifts information för fel sökning.

Men precis som de flesta Windows-baserade program händelse loggar är Windows PowerShell-händelseloggen inte utformad för att vara säker. Den bör inte användas för att granska säkerheten eller registrera konfidentiell eller patentskyddad information.

Händelse loggar är utformade för att läsas och förstås av användare. Användare kan läsa från och skriva till loggen. En obehörig användare kan läsa en händelse logg på en lokal dator eller fjärrdator, registrera falska data och sedan förhindra att deras aktiviteter loggas.

## <a name="notes"></a>Kommentarer

Författare av modulens författare kan lägga till loggnings funktioner i sina moduler. Mer information finns i [skriva en Windows PowerShell-modul](/powershell/scripting/developer/module/writing-a-windows-powershell-module).

## <a name="see-also"></a>Se även

[Get-EventLog](xref:Microsoft.PowerShell.Management.Get-EventLog)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Preference_Variables](about_Preference_Variables.md)
