---
description: Konfigurationsfiler för PowerShell Core, och ersätter register konfiguration.
keywords: powershell
Locale: en-US
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: 88e2f5fc5eaaf3ffffd5ceb3df0632866eee705e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271839"
---
# <a name="about-powershell-config"></a>Om PowerShell-konfiguration

## <a name="short-description"></a>KORT BESKRIVNING
Konfigurationsfiler för PowerShell Core, och ersätter register konfiguration.

## <a name="long-description"></a>LÅNG BESKRIVNING

`powershell.config.json`Filen innehåller konfigurations inställningar för PowerShell Core. PowerShell läser in den här konfigurationen vid start. Inställningarna kan också ändras vid körning. Tidigare lagrades dessa inställningar i Windows-registret för PowerShell, men ingår nu i en fil för att aktivera konfiguration på macOS och Linux.

> [!WARNING]
> Om `powershell.config.json` filen innehåller ogiltig JSON PowerShell kan inte starta en interaktiv session.
> Om detta inträffar måste du åtgärda konfigurations filen.

> [!NOTE]
> Okända nycklar eller ogiltiga värden i konfigurations filen ignoreras tyst.

### <a name="allusers-shared-configuration"></a>AllUsers (delad) konfiguration

En `powershell.config.json` fil i `$PSHOME` katalogen definierar konfigurationen för alla PowerShell-sessioner som körs från den PowerShell Core-installationen.

> [!NOTE]
> `$PSHOME`Platsen definieras som samma katalog som den System.Management.Automation.dll sammansättningen körs på. Detta gäller även för värdbaserade PowerShell SDK-instanser.

### <a name="currentuser-per-user-configurations"></a>CurrentUser-konfigurationer (per användare)

Du kan också konfigurera PowerShell per användare genom att placera filen i konfigurations katalogen för användar området. Du hittar användar konfigurations katalogen på olika plattformar med kommandot `Split-Path $PROFILE.CurrentUserCurrentHost` .

## <a name="general-configuration-settings"></a>Allmänna konfigurationsinställningar

### <a name="executionpolicy"></a>ExecutionPolicy

> [!IMPORTANT]
> Den här konfigurationen gäller endast för Windows-plattformar.

Konfigurerar körnings principen för PowerShell-sessioner och avgör vilka skript som kan köras. Som standard använder PowerShell den befintliga körnings principen.

För AllUsers-konfigurationer ställer detta in principen för **LocalMachine** -körning.
För CurrentUser-konfigurationer ställer detta in principen för **CurrentUser** -körning.

> [!NOTE]
> [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)Cmdleten ändrar den här inställningen i konfigurations filen för allusers när den anropas med `-Scope LocalMachine` , och ändrar den här inställningen i CurrentUser-konfigurationsfilen när den anropas med `-Scope CurrentUser` .

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

Där:

- `<shell-id>` refererar till ID: t för den aktuella PowerShell-värden.
  För normal PowerShell-kärna är detta `Microsoft.PowerShell` .
  I en PowerShell-session kan du identifiera den med `$ShellId` .
- `<execution-policy>` refererar till ett giltigt körnings princip namn.

I följande exempel anges körnings principen för PowerShell till `RemoteSigned` .

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

I Windows kan du hitta motsvarande register nycklar `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` under `HKEY_LOCAL_MACHINE` och i `HKEY_CURRENT_USER` .

### <a name="psmodulepath"></a>PSModulePath

Åsidosätter en PSModulePath-komponent för den här PowerShell-sessionen. Om konfigurationen gäller för den aktuella användaren anger du sökvägen till CurrentUser-modulen. Om konfigurationen är för alla användare anger sökvägen till AllUser-modulen.

> [!WARNING]
> Om du konfigurerar en sökväg för en AllUsers-eller CurrentUser-modul så ändras inte den omfångs installations platsen för PowerShellGet-moduler som [install-module](/powershell/module/powershellget/install-module).
> Dessa cmdletar använder alltid *standard* Sök vägarna.

Om inget värde anges används standardvärdet för respektive modul Sök vägs komponent. Se [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) för mer information om dessa standardvärden.

Den här inställningen gör att miljövariabler kan användas genom att bädda in dem mellan `%` tecken, t `"%HOME%\Documents\PowerShell\Modules"` . ex. på samma sätt som cmd tillåter. Den här syntaxen gäller även för Linux och macOS. Se nedan för exempel.

```Schema
"PSModulePath": "<ps-module-path>"
```

Där:

- `<ps-module-path>` är den absoluta sökvägen till en modul-katalog. För alla användarkonfigurationer är detta den AllUsers delade modul katalogen. För aktuella användarkonfigurationer är detta CurrentUser-modulens katalog.

I det här exemplet visas en PSModulePath-konfiguration för en Windows-miljö:

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

I det här exemplet visas en PSModulePath-konfiguration för en macOS-eller Linux-miljö:

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

I det här exemplet visas hur du bäddar in en miljö variabel i en PSModulePath-konfiguration. Observera att om du använder `HOME` miljövariabeln och `/` katalog avgränsaren fungerar detta på Windows, MacOS och Linux.

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

I det här exemplet visas hur du bäddar in en miljö variabel i en PSModulePath-konfiguration som bara fungerar på macOS och Linux:

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> PowerShell-variabler kan inte bäddas in i PSModulePath-konfigurationer.
> PSModulePath-konfigurationer på Linux och macOS är Skift läges känsliga. En PSModulePath-konfiguration måste använda giltiga katalog avgränsare för plattformen. På macOS och Linux innebär det här `/` . I Windows fungerar både `/` och `\` .

### <a name="experimentalfeatures"></a>ExperimentalFeatures

Namnen på de experimentella funktioner som ska aktive ras i PowerShell.
Som standard är inga experimentella funktioner aktiverade.
Standardvärdet är en tom matris.

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

Där:

- `<experimental-feature-name>` är namnet på en experimentell funktion som ska aktive ras.

I följande exempel aktive ras **PSImplicitRemoting** -och **PSUseAbbreviationExpansion** -experimentella funktioner när PowerShell startas.

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

Mer information om experimentella funktioner finns i [POWERSHELL RFC 29][RFC0029].

## <a name="non-windows-logging-configuration"></a>Konfiguration för icke-Windows-loggning

> [!IMPORTANT]
> Konfigurations alternativen i det här avsnittet gäller endast macOS och Linux.
> Loggning för Windows hanteras av Windows-Loggboken.

PowerShell-loggning på macOS och Linux kan konfigureras i PowerShell-konfigurationsfilen. En fullständig beskrivning av PowerShell-loggning för icke-Windows-system finns i [om loggning](./about_Logging_Non-Windows.md).

### <a name="logidentity"></a>LogIdentity

> [!IMPORTANT]
> Den här inställningen kan endast användas i macOS och Linux.

Anger det identitets namn som används för att skriva till system loggen. Standardvärdet är "PowerShell".

```Schema
"LogIdentity": "<log-identity>"
```

Där:

- `<log-identity>` är sträng identiteten som PowerShell ska använda för att skriva till syslog.

> [!NOTE]
> Du kanske vill ha olika **LogIdentity** -värden för varje instans av PowerShell som du har installerat.

I det här exemplet konfigurerar vi **LogIdentity** för en för hands version av PowerShell.

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a>Loggnivå

> [!IMPORTANT]
> Den här inställningen kan endast användas i macOS och Linux.

Anger den lägsta allvarlighets grad som PowerShell ska logga.

```Schema
"LogLevel": "<log-level>|default"
```

Där:

- `<log-level>` är en av:
  - Always
  - Kritiskt
  - Fel
  - Varning
  - Information
  - Verbose
  - Felsökning

> [!NOTE]
> Om du anger en loggnings nivå aktive ras alla logg nivåer ovanför.

Om du ställer in den här inställningen som **standard** tolkas det som standardvärdet.
Standardvärdet är **information**.

I följande exempel anges värdet till **verbose**.

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a>LogChannels

> [!IMPORTANT]
> Den här inställningen kan endast användas i macOS och Linux.

Bestämmer vilka loggnings kanaler som är aktiverade.

```Schema
"LogChannels": "<log-channel>,..."
```

Där:

- `<log-channel>` är en av:
  - Drift – loggar grundläggande information om PowerShell-aktiviteter
  - Analytiskt loggar mer detaljerad diagnostikinformation

Standardvärdet är **drift**. Om du vill aktivera båda kanalerna inkluderar du båda värdena som en kommaavgränsad sträng. Ett exempel:

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a>LogKeywords

> [!IMPORTANT]
> Den här inställningen kan endast användas i macOS och Linux.

Anger vilka delar av PowerShell som loggas. Som standard är alla logg nyckelord aktiverade. Om du vill aktivera flera nyckelord anger du värdena i en enda kommaavgränsad sträng.

```Schema
"LogKeywords": "<log-keyword>,..."
```

Där:

- `<log-keyword>` är en av:
  - Hantering av körnings utrymme-körnings utrymme
  - Pipeline – pipeline-åtgärder
  - Protokoll hantering av protokoll, till exempel PSRP
  - Stöd för transport transport skikt, till exempel SSH
  - Värd-PowerShell-värd funktioner, till exempel konsol interaktion
  - Cmdlets – PowerShell Built-cmdlet: ar
  - Serialiserare – serialiserings logik
  - Session – PowerShell-sessionstillstånd
  - ManagedPlugin – WSMan-plugin

> [!NOTE]
> Det rekommenderas vanligt vis att lämna det här värdet unset om du inte försöker diagnostisera ett visst beteende i en känd del av PowerShell.
> Om du ändrar det här värdet minskar bara mängden information som loggas.

Det här exemplet begränsar loggningen till körnings utrymme-åtgärder, pipeline-logik och cmdlet-användning. All annan loggning kommer att utelämnas.

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a>Fler exempel konfigurationer

### <a name="example-windows-configuration"></a>Exempel på Windows-konfiguration

Den här konfigurationen har flera inställningar som uttryckligen anges:

- Körnings principen för den här PowerShell-installationen är `AllSigned`
- Sökvägen till CurrentUser-modulen har angetts till en modul-katalog på en delad enhet
- `PSImplicitRemotingBatching`Experimentell funktion är aktive rad

> [!NOTE]
> `ExecutionPolicy`Inställningarna och `PSModulePath` fungerar bara på en Windows-plattform eftersom modulens sökväg använder `\` och `;` avgränsnings tecken och körnings principen inte `Unrestricted` (den enda principen som tillåts på UNIX-liknande plattformar).

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a>Exempel på konfiguration som inte är Windows

Den här konfigurationen anger ett antal alternativ som bara fungerar i macOS eller Linux:

- Sökvägen till CurrentUser-modulen har angetts till en anpassad modul-katalog i `$HOME`
- Funktionen **PSImplicitRemotingBatching** experimentell är aktive rad
- Loggnings nivån för PowerShell är inställd på **verbose** , för mer loggning
- Den här PowerShell-installationen skriver till loggarna med hjälp av **Home-PowerShell-** identiteten.

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a>Se även

[Om körnings principer](./about_Execution_Policies.md)

[Om automatiska variabler](./about_Automatic_Variables.md)

[RFC0029]: https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md
