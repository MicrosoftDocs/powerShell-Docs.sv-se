---
title: Nyheter i PowerShell 7,1
description: Nya funktioner och ändringar som lanseras i PowerShell 7,1
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577215"
---
# <a name="whats-new-in-powershell-71"></a>Nyheter i PowerShell 7,1

Den 11 november 2020 [presenterade](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) vi den allmänna tillgängligheten för PowerShell 7,1. Vi bygger på stiftelsen som etablerats i PowerShell 7,0, våra ansträngningar fokuserar på community-problem och inkluderar ett antal förbättringar och korrigeringar. Vi strävar efter att se till att PowerShell är en stabil och genomförd plattform.

PowerShell 7,1 innehåller följande funktioner, uppdateringar och brytande ändringar.

- PSReadLine 2.1.0, som innehåller förutsägande IntelliSense
- PowerShell 7,1 har publicerats på Microsoft Store
- Installations paket har uppdaterats för nya OS-versioner med stöd för ARM64
- 4 nya experimentella funktioner och 2 experimentella funktioner upphöjt till vanlig
- Flera större ändringar för att förbättra användbarhet

En fullständig lista över ändringar finns i [ändringsloggen](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) i GitHub-lagringsplatsen.

## <a name="psreadline-210"></a>PSReadLine 2.1.0

PowerShell 7,1 inkluderar även PSReadLine 2.1.0. Den här versionen innehåller förutsägande IntelliSense. Mer information om funktionen förutsägande IntelliSense finns i [meddelandet](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) i PowerShell-bloggen.

## <a name="microsoft-store-installer-package"></a>Microsoft Store installations paket

PowerShell 7,1 har publicerats till Microsoft Store. Du hittar PowerShell-versionen på [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) webbplats eller i Store-programmet i Windows.

Fördelar med Microsoft Store-paketet:

- Automatiska uppdateringar har skapats direkt i Windows 10
- Integreras med andra mekanismer för program varu distribution som Intune och SCCM

> [!NOTE]
> Eventuella konfigurations inställningar på system nivå som lagras i `$PSHOME` kan inte ändras. Detta inkluderar WSMAN-konfigurationen. Detta förhindrar att fjärrsessioner ansluter till Store-baserade installationer av PowerShell. Konfigurationer på användar nivå och SSH-fjärrkommunikation stöds.

## <a name="other-installers"></a>Andra installations program

Mer uppdaterad information om operativ system och support livs cykel som stöds finns i [PowerShell-Supportens livs cykel](/powershell/scripting/powershell-support-lifecycle).

Kontrol lera installations anvisningarna för det önskade operativ systemet:

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

Dessutom stöder PowerShell 7,1 ARM32 och ARM64 varianter för Debian, Ubuntu och ARM64 Alpine Linux.

Även om den inte stöds officiellt har communityn även tillhandahållit paket för [båge](https://aur.archlinux.org/packages/powershell/) och Kali Linux.

> [!NOTE]
> Debian 10 +, CentOS 8 +, Ubuntu 20,04, alpina och arm stöder för närvarande inte WinRM-fjärrkommunikation. Mer information om hur du konfigurerar SSH-baserad fjärr kommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="experimental-features"></a>Experimentella funktioner

Mer information om experiment funktionerna finns i [använda experimentella funktioner](../learn/experimental-features.md).

Följande experimentella funktioner är nu vanliga funktioner i den här versionen:

- [PSNullConditionalOperators](../learn/experimental-features.md#psnullconditionaloperators)
- [PSUnixFileStat](../learn/experimental-features.md#psunixfilestat)

Följande experimentella funktioner har lagts till i den här versionen:

- [Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - PowerShell 7,1 utökar den här experimentella funktionen för att lägga till **körnings utrymme** -parametern i alla `*-PSBreakpoint` cmdletar. Parametern **körnings utrymme** anger ett **körnings utrymme** -objekt som interagerar med Bryt punkter i den angivna körnings utrymme.

- [PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) – med den här funktionen kan du skicka PowerShell-providerns sökvägar till interna kommandon som inte stöder PowerShell-syntax för sökväg.

- [PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) – när den vänstra operanden i en `-replace` operator-instruktion inte är en sträng, konverteras den operanden till en sträng. När funktionen är aktive rad använder inte konverteringen kultur inställningar för sträng konvertering.

- [PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) hjälper till att stödja framtida förutsägande IntelliSense-plugin-program.

## <a name="breaking-changes-and-improvements"></a>Bryta ändringar och förbättringar

- Korrigera `$?` till inte `$false` när det interna kommandot skriver till `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))

  Det är vanligt att de interna kommandona skrivs till utan att det är `stderr` något som tyder på ett haveri.
  Med den här ändringen `$?` anges till `$false` endast när det inbyggda kommandot också har en slutkod som inte är noll. Den här ändringen är inte relaterad till experiment funktionen `PSNotApplyErrorActionToStderr` .

- `$ErrorActionPreference`Påverkar inte `stderr` utdata från interna kommandon ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))

  Det är vanligt att de interna kommandona skrivs till utan att det är `stderr` något som tyder på ett haveri.
  Med den här ändringen `stderr` fångas utdata fortfarande in i **ErrorRecord** -objekt, men körningen gäller inte längre `$ErrorActionPreference` om **ErrorRecord** kommer från ett internt kommando.

- Byt namn `-FromUnixTime` till `-UnixTimeSeconds` på för `Get-Date` att tillåta UNIX-tidsinformation ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (tack @aetos382 !)

  `-FromUnixTime`Parametern lades till under 7,1-för hands version. 2. Parametern har bytt namn för att bättre matcha data typen. Den här parametern använder ett heltals värde som representerar i sekunder sedan 1 januari 1970, 0:00:00.

  I det här exemplet konverteras en UNIX-tid (som representeras av antalet sekunder sedan 1970-01-01 0:00:00) till DateTime.

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- Tillåt explicit angiven namngiven parameter att ersätta samma med en hash-ihopbuntning (#13162)

  Med den här ändringen flyttas de namngivna parametrarna från ihopbuntning till slutet av parameter listan så att de binds efter att alla explicit angivna namngivna parametrar är kopplade till varandra. Parameter bindning för enkla funktioner genererar inte ett fel när det inte går att hitta en angiven namngiven parameter. Okända namngivna parametrar är kopplade till den `$args` enkla funktionens parameter. Om du flyttar ihopbuntning till slutet av argument listan ändras den ordning som parametrarna visas i `$args` .

  Exempel:

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  I föregående beteende är inte **sökvägen** kopplad till `-Path` eftersom det är det tredje argumentet i argument listan. # # Så att det slutar att vara fyllda i "$args" tillsammans med `Blah = "World"`

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  Med den här ändringen flyttas argumenten från `@hash` till slutet av argument listan. **Sökvägar** blir det första argumentet i listan, så den är kopplad till `-Path` .

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- Gör att växel parametern `-Qualifier` inte placeras för `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (tack @yecril71pl !)

- Matcha arbets katalogen som en litteral sökväg för `Start-Process` när den inte har angetts ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (tack @NoMoreFood !)

- Skapa `-OutFile` en parameter i webb-cmdlets som fungerar som `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (tack @iSazonov !)

- Korrigera sträng parameter bindning för `BigInteger` numeriska literaler ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (tack @vexx32 !)

- I Windows `Start-Process` skapar en process miljö med alla miljövariabler från den aktuella sessionen, med `-UseNewEnvironment` en ny standard process miljö ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (tack @iSazonov !)

- Bryt inte retur resultat i `PSObject` vid konvertering av ett `ScriptBlock` till ett ombud ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))

  När en `ScriptBlock` konverteras till en Delegerings typ som ska användas i C#-kontexten får du onödiga problem genom att figursätta resultatet i a `PSObject` :

  - När värdet konverteras till den delegerade retur typen, blir det i `PSObject` själva verket figursatt. Så den `PSObject` är inte nödvändig.
  - När den här svars typen är, omsluts `object` den i en `PSObject` gör det svårt att arbeta med i C#-kod.

  Efter den här ändringen är det returnerade objektet det underliggande objektet.
