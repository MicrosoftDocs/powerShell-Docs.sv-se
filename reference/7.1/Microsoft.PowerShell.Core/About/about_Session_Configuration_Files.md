---
description: Beskriver konfigurationsfiler för sessioner, som används i en sessionsnyckel (kallas även "slut punkt") för att definiera miljön för sessioner som använder sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 45c8a6e0ba8478e0a49cb287cd4311d7556a42ea
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270153"
---
# <a name="about-session-configuration-files"></a>Om konfigurationsfiler för sessioner

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver konfigurationsfiler för sessioner, som används i en sessionsnyckel (kallas även "slut punkt") för att definiera miljön för sessioner som använder sessionen.

## <a name="long-description"></a>LÅNG BESKRIVNING

En "sessions konfigurations fil" är en textfil med fil namns tillägget. PSSC som innehåller en hash-tabell med konfigurations egenskaper och värden för sessioner. Du kan använda en konfigurations fil för sessionen för att ange egenskaperna för en sessions konfiguration. Detta definierar miljön för alla PowerShell-sessioner som använder den konfigurationen av sessionen.

Konfigurationsfiler för sessioner gör det enkelt att skapa anpassade sessioner utan att använda komplexa C#-sammansättningar eller skript.

En "sessionsinformation" eller "slut punkt" är en samling inställningar för lokala datorer som avgör vilka användare som kan skapa sessioner på datorn. vilka kommandon användare kan köra i dessa sessioner. och om sessionen ska köras som ett privilegierat virtuellt konto. För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](about_Session_Configurations.md).

Nodkonfigurationer introducerades i Windows PowerShell 2,0 och konfigurationsfiler för sessionen introducerades i Windows PowerShell 3,0. Du måste använda Windows PowerShell 3,0 för att inkludera en sessions konfigurations fil i en sessions konfiguration. Användare av Windows PowerShell 2,0 (och senare) påverkas dock av inställningarna i konfigurationen av sessionen.

## <a name="creating-custom-sessions"></a>Skapa anpassade sessioner

Du kan anpassa många funktioner i en PowerShell-session genom att ange sessionsinställningar i en sessions konfiguration. Du kan anpassa en session genom att skriva ett C#-program som definierar en anpassad körnings utrymme, eller så kan du använda en konfigurations fil för sessionen för att definiera egenskaperna för sessioner som skapats med hjälp av konfigurationen av sessionen. Som en allmän regel är det enklare att använda konfigurations filen för sessionen än att skriva ett C#-program.

Du kan använda en konfigurations fil för sessionen för att skapa objekt som till exempel fullt fungerande sessioner för mycket betrodda användare. låsta sessioner som tillåter minimal åtkomst; sessioner som har utformats för vissa och som endast innehåller de moduler som krävs för dessa uppgifter. sessioner där användare utan privilegier kan bara köra vissa kommandon som ett privilegierat konto.

Förutom det kan du hantera om användare av-sessionen kan använda PowerShell-språkelement som skript block, eller om de bara kan köra kommandon. Du kan hantera versionen av PowerShell-användare som kan köras i sessionen. hantera vilka moduler som importeras till sessionen. och hantera vilka cmdlets, Functions och alias som session användare kan köra. När du använder fältet RoleDefinitions kan du ge användarna olika funktioner i sessionen baserat på grupp medlemskap.

Mer information om RoleDefinitions och hur du definierar det här värdet finns i hjälp avsnittet för cmdleten New-PSRoleCapabilityFile.

## <a name="creating-a-session-configuration-file"></a>Skapa en konfigurations fil för sessionen

Det enklaste sättet att skapa en konfigurations fil för en session är genom att använda New-PSSessionConfigurationFile-cmdleten. Denna cmdlet skapar en fil som använder rätt syntax och format, och som automatiskt verifierar många av konfigurations filens egenskaps värden.

Detaljerad beskrivning av de egenskaper som du kan ange i en sessions konfigurations fil finns i hjälp avsnittet för New-PSSessionConfigurationFile-cmdleten.

Följande kommando skapar en konfigurations fil för sessionen som använder standardvärdena. Den resulterande konfigurations filen använder bara standardvärdena eftersom inga andra parametrar än Sök vägs parametern (som anger fil Sök vägen) ingår:

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

Om du vill visa den nya konfigurations filen i standard text redigeraren använder du följande kommando:

```powershell
Invoke-Item -Path .\Defaults.pssc
```

Om du vill skapa en sessions konfiguration för sessioner där användaren kan köra kommandon, men inte använda andra element för PowerShell-språket, skriver du:

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

I föregående kommando ställer du in parametern LanguageMode till nolanguage förhindrar användare att göra sådana saker som att skriva eller köra skript eller använda variabler.

Om du vill skapa en sessionsnyckel för sessioner där användare bara kan använda Get-cmdletar skriver du:

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

I föregående exempel ställer du in parametern VisibleCmdlets på Get-* begränsar användare till cmdletar som har namn som börjar med strängvärdet "Get-".

Om du vill skapa en sessionsnyckel för sessioner som körs under ett privilegierat virtuellt konto i stället för användarens autentiseringsuppgifter, skriver du:

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

Om du vill skapa en sessionsnyckel för sessioner där de kommandon som är synliga för användaren anges i en roll funktions fil, skriver du:

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a>Använda en konfigurations fil för sessionen

Du kan inkludera en konfigurations fil för sessionen när du skapar en konfiguration av sessionen eller lägga till en fil i konfigurationen vid ett senare tillfälle.

Om du vill lägga till en sessions konfigurations fil när du skapar en-sessionsnyckel använder du parametern Path i Register-PSSessionConfiguration-cmdleten.

Följande kommando använder till exempel filen nolanguage. PSSC när den skapar en konfiguration för nolanguage-sessionen.

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

När en ny nolanguage-session startar får användarna bara åtkomst till PowerShell-kommandon.

Om du vill lägga till en sessions konfigurations fil i en befintlig sessionsnyckel använder du cmdleten Set-PSSessionConfiguration och parametern Path. Detta påverkar alla nya sessioner som skapats med den angivna konfigurationen. Observera att Set-PSSessionConfiguration-cmdlet ändrar själva sessionen och ändrar inte konfigurations filen för sessionen.

Följande kommando lägger till exempel till nolanguage. PSSC-filen i konfigurationen av LockedDown-sessionen.

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

När användarna använder LockedDown för att skapa en session kommer de att kunna köra cmdlets, men de kommer inte att kunna skapa eller använda variabler, tilldela värden eller använda andra PowerShell-språkelement.

Följande kommando använder cmdleten New-PSSession för att skapa en session på datorn SRV01 som använder LockedDown och sparar en objekt referens till sessionen i $s variabeln. Åtkomst kontrol listan (åtkomst kontrol listan) för sessionen avgör vem som kan använda den för att skapa en session.

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

Eftersom inga språk begränsningar har lagts till i LockedDown-sessionen kommer användare i LockedDown-sessioner endast att kunna köra PowerShell-kommandon och cmdlets. Följande två kommandon använder exempelvis cmdleten Invoke-Command för att köra kommandon i sessionen som refereras i $s-variabeln. Det första kommandot, som kör Get-UICulture-cmdleten, och som inte använder några variabler, lyckas. Det andra kommandot, som hämtar värdet för variabeln $PSUICulture, Miss lyckas.

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a>Redigera en konfigurations fil för sessionen

Alla inställningar i en sessionsinformation förutom RunAsVirtualAccount och RunAsVirtualAccountGroups kan ändras genom att du redigerar den sessionens konfigurations fil som används av konfigurationen av sessionen. Börja med att hitta den aktiva kopian av sessionens konfigurations fil.

När du använder en konfigurations fil för sessionen i en konfiguration, skapar PowerShell en aktiv kopia av sessionens konfigurations fil och lagrar den \$ i \\ katalogen pshome SessionConfig på den lokala datorn.

Platsen för den aktiva kopian av en sessions konfigurations fil lagras i egenskapen ConfigFilePath för sessionens konfigurations objekt.

Följande kommando hämtar platsen för sessionens konfigurations fil för konfiguration av nolanguage-sessionen.

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

Kommandot returnerar en fil Sök väg som liknar följande:

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

Du kan redigera. PSSC-filen i valfri text redigerare. När filen har sparats kommer den att användas av alla nya sessioner som använder-sessionen.

Om du behöver ändra RunAsVirtualAccount-eller RunAsVirtualAccountGroups-inställningarna måste du avregistrera konfigurationen för sessionen och registrera en konfigurations fil för sessionen som innehåller de redigerade värdena.

## <a name="testing-a-session-configuration-file"></a>Testa en konfigurations fil för sessionen

Använd Test-PSSessionConfigurationFile-cmdlet för att testa manuellt redigerade konfigurationsfiler för sessioner. Det är viktigt: om filsyntaxen och värdena inte är giltiga kan användarna inte använda sessionen för att skapa en session.

Följande kommando testar till exempel den aktiva sessionens konfigurations fil för konfigurationen av nolanguage-sessionen.

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

Om syntaxen och värdena i konfigurations filen är giltiga Test-PSSessionConfigurationFile returnerar true. Om syntaxen och värdena inte är giltiga returnerar cmdleten false.

Du kan använda Test-PSSessionConfigurationFile för att testa en konfigurations fil för sessionen, inklusive filer som New-PSSessionConfiguration-cmdlet skapar. Mer information finns i hjälp avsnittet för Test-PSSessionConfigurationFile-cmdleten.

## <a name="removing-a-session-configuration-file"></a>Tar bort en konfigurations fil för sessionen

Du kan inte ta bort en sessions konfigurations fil från en sessions konfiguration.
Du kan dock ersätta filen med en ny fil som använder standardinställningarna. Detta avbryter de inställningar som används av den ursprungliga konfigurations filen.

Om du vill ersätta en sessions konfigurations fil skapar du en ny konfigurations fil för sessionen som använder standardinställningarna och använder sedan Set-PSSessionConfiguration-cmdlet: en för att ersätta den anpassade sessionens konfigurations fil med den nya filen.

Följande kommandon skapar till exempel en standardsessions konfigurations fil och ersätter sedan den aktiva sessionens konfigurations fil i konfigurationen för konfiguration av nolanguage.

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

När de här kommandona är slutförda, ger konfigurationen av nolanguages-sessionen faktiskt stöd för fullständigt språk (standardinställningen) för alla sessioner som skapats med den konfigurationen av sessionen.

Visa egenskaperna för en konfiguration av en session. de konfigurations objekt för sessionen som representerar sessionsinställningar med hjälp av konfigurationsfiler har ytterligare egenskaper som gör det enkelt att identifiera och analysera konfigurationen för sessionen. (Observera att det typnamn som visas nedan innehåller en formaterad vydefinition.) Du kan visa egenskaperna genom att köra cmdleten Get-PSSessionConfiguration och skicka tillbaka data till Get-Member-cmdlet:

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

De här egenskaperna gör det enkelt att söka efter vissa konfigurationer.
Du kan till exempel använda egenskapen ExecutionPolicy för att hitta en sessionsnyckel som stöder sessioner med RemoteSigned-körnings principen.
Observera att eftersom egenskapen ExecutionPolicy bara finns på sessioner som använder konfigurationsfiler för sessioner, kanske kommandot inte returnerar alla kvalificerade konfigurationer av konfigurationen.

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

Följande kommando hämtar sessionsinställningar där RunAsUser är Exchange-administratören.

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

Om du vill visa information om roll definitionerna som är associerade med en konfiguration använder du cmdleten Get-PSSessionCapability. Med den här cmdleten kan du bestämma vilka kommandon och miljö som är tillgängliga för vissa användare i vissa slut punkter.

## <a name="notes"></a>ANTECKNINGAR

Sessionsbaserade stöder också en typ av session som kallas "Empty"-session. Med en tom sessionsfil kan du skapa anpassade sessioner med valda kommandon. Om du inte lägger till moduler, funktioner eller skript i en tom session, är sessionen begränsad till uttryck och kanske inte är en praktisk användning. Egenskapen SessionType anger om du arbetar med en tom session eller inte.

## <a name="see-also"></a>SE ÄVEN

[about_Session_Configurations](about_Session_Configurations.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Aktivera – PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Registrera – PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Avregistrera-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[Get-PSSessionCapability](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[New-PSRoleCapabilityFile](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)

