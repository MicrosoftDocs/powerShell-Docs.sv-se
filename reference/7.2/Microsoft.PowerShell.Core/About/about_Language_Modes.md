---
description: Förklarar språk lägen och deras inverkan på PowerShell-sessioner.
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 9e4b1ec2dd16d3442c553460ff217e7e0223f41f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708498"
---
# <a name="about-language-modes"></a>Om språk lägen

## <a name="short-description"></a>KORT BESKRIVNING
Förklarar språk lägen och deras inverkan på PowerShell-sessioner.

## <a name="long-description"></a>LÅNG BESKRIVNING

Språk läget i en PowerShell-session bestämmer delvis vilka element i PowerShell-språket som kan användas i sessionen.

PowerShell har stöd för följande språk lägen:

- FullLanguage
- ConstrainedLanguage (lanserades i PowerShell 3,0)
- RestrictedLanguage
- Inget språk

### <a name="what-is-a-language-mode"></a>VAD ÄR ETT SPRÅK LÄGE?

Språk läget avgör vilka språk element som tillåts i sessionen.

Språk läget är i själva verket en egenskap för den session konfiguration (eller "slut punkt") som används för att skapa sessionen. Alla sessioner som använder en viss konfiguration av sessionen har språk läget i konfigurationen av sessionen.

Alla PowerShell-sessioner har ett språk läge, inklusive PSSessions som du skapar med hjälp av `New-PSSession` cmdleten, tillfälliga sessioner som använder parametern ComputerName och de standardsessioner som visas när du startar PowerShell.

Fjärrsessioner skapas med hjälp av sessionens konfigurationer på fjärrdatorn. Språk läget som anges i konfigurationen bestämmer sessionens språkläge. Om du vill ange PSSession för en använder du parametern ConfigurationName för cmdletar som skapar en session.

### <a name="language-modes"></a>SPRÅK LÄGEN

I det här avsnittet beskrivs språk lägena i PowerShell-sessioner.

#### <a name="full-language-fulllanguage"></a>FULLSTÄNDIGT språk (FullLanguage)

FullLanguage-läget tillåter alla språk element i sessionen.
FullLanguage är standard språk läget för standardsessioner i alla versioner av Windows förutom Windows RT.

#### <a name="restricted-language-restrictedlanguage"></a>BEGRÄNSAT språk (RestrictedLanguage)

I RestrictedLanguage-läge kan användare köra kommandon (cmdlets, functions, CIM-kommandon och arbets flöden) men får inte använda skript block.

Som standard tillåts endast följande variabler i RestrictedLanguage-läge:

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

Modul manifest, som använder RestrictedLanguage-läge, tillåter även följande ytterligare variabler:

- `$PSScriptRoot`
- `$PSEdition` (i PowerShell Core)
- `$EnabledExperimentalFeatures` (i PowerShell Core)

Endast följande jämförelse operatorer tillåts:

- `-eq` Skeppningskvantiteten
- `-gt` (större än)
- `-lt` (mindre än)

Tilldelnings instruktioner, egenskaps referenser och metod anrop är inte tillåtna.

#### <a name="no-language-nolanguage"></a>INGET språk (nolanguage)

Nospråks läge kan bara användas via API: et. Nospråk läge innebär att ingen skript text för något formulär tillåts. Detta utesluter användningen av metoden **AddScript ()** som skickar fragment av PowerShell-skript för att parsas och köras. Du kan bara använda **AddCommand ()** och **AddParameter ()** som inte går igenom parsern.

#### <a name="constrained-language-constrained-language"></a>BEGRÄNSAT språk (begränsat språk)

ConstrainedLanguage-läget tillåter alla cmdletar och alla PowerShell-språkelement, men det begränsar tillåtna typer.

ConstrainedLanguage-läget har utformats för att stödja kod integritet i användarläge (UMCI) på Windows RT. Det är det enda språk läge som stöds i Windows RT, men det är tillgängligt i alla system som stöds.

UMCI skyddar ARM-enheter genom att bara tillåta att Microsoft-signerade och Microsoft-certifierade appar installeras på Windows RT-baserade enheter.
ConstrainedLanguage-läget hindrar användare från att använda PowerShell för att kringgå eller bryta mot UMCI.

Funktionerna i ConstrainedLanguage-läge är följande:

- Alla cmdletar i Windows-moduler och andra UMCI-godkända cmdlets är fullt funktionella och har fullständig åtkomst till system resurser, förutom vad som anges.

- Alla element i PowerShell-skript språket är tillåtna.

- Alla moduler som ingår i Windows kan importeras och alla kommandon som modulerna exporterar körs i sessionen.

- I PowerShell-arbetsflöde kan du skriva och köra skript arbets flöden (arbets flöden skrivna i PowerShell-språket). XAML-baserade arbets flöden stöds inte och du kan inte köra XAML i ett skript arbets flöde, till exempel med hjälp av `Invoke-Expression -Language XAML` . Arbets flöden kan heller inte anropa andra arbets flöden, även om kapslade arbets flöden tillåts.

- `Add-Type`Cmdleten kan läsa in signerade sammansättningar, men det går inte att läsa in godtycklig C#-kod eller Win32-API: er.

- `New-Object`Cmdleten kan endast användas för tillåtna typer (visas nedan).

- Endast tillåtna typer (listade nedan) kan användas i PowerShell. Andra typer är inte tillåtna.

- Typ konvertering tillåts, men endast om resultatet är en tillåten typ.

- Cmdlet-parametrar som konverterar inmatade strängar till typer fungerar endast när den resulterande typen är en tillåten typ.

- Metoden **toString ()** och .net-metoderna för tillåtna typer (listas nedan) kan anropas. Det går inte att anropa andra metoder.

- Användare kan hämta alla egenskaper av tillåtna typer. Användare kan bara ange värden för egenskaper för kärn typer. Endast följande COM-objekt tillåts:

  - **Skript. ord lista**
  - **Scripting. FileSystemObject**
  - **VBScript. RegExp**

Följande typer tillåts i ConstrainedLanguage-läge. Användare kan få egenskaper, anropa metoder och konvertera objekt till de här typerna.

Tillåtna typer:

- AliasAttribute
- AllowEmptyCollectionAttribute
- AllowEmptyStringAttribute
- AllowNullAttribute
- Matris
- Bool
- stor
- char
- CmdletBindingAttribute
- DateTime
- decimal
- DirectoryEntry
- DirectorySearcher
- double
- flyt
- GUID
- Hash
- int
- Int16
- long
- ManagementClass
- ManagementObject
- ManagementObjectSearcher
- NullString
- OutputTypeAttribute
- ParameterAttribute
- PSCredential
- PSDefaultValueAttribute
- PSListModifier
- PSObject
- PSPrimitiveDictionary
- PSReference
- PSTypeNameAttribute
- Verifiering
- SByte
- sträng
- SupportsWildcardsAttribute
- SwitchParameter
- System. globalisering. CultureInfo
- System .net. IPAddress
- System .net. mail. mail-adress
- System. Numerics. BigInteger
- System. Security. SecureString
- TimeSpan
- UInt16
- UInt32
- UInt64

### <a name="finding-the-language-mode-of-a-session-configuration"></a>HITTA SPRÅK LÄGET FÖR EN SESSIONS KONFIGURATION

När en sessions konfiguration skapas med hjälp av en konfigurations fil för en session, har sessionen en LanguageMode-egenskap. Du kan hitta språk läget genom att hämta värdet för egenskapen LanguageMode.

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

I andra konfigurationer av sessioner kan du hitta språk läget indirekt genom att söka efter språk läge för en session som skapats med hjälp av konfigurationen av sessionen.

### <a name="finding-the-language-mode-of-a-session"></a>HITTA SPRÅK LÄGET FÖR EN SESSION

Du kan hitta språk läget för en FullLanguage-eller ConstrainedLanguage-session genom att hämta värdet för egenskapen LanguageMode för sessionens tillstånd.

Exempel:

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

I sessioner med RestrictedLanguage-och nolanguage-lägen kan du dock inte använda punkt metoden för att hämta egenskaps värden. I stället visar fel meddelandet språk läge.

När du kör `$ExecutionContext.SessionState.LanguageMode` kommandot i en RestrictedLanguage-session returnerar PowerShell fel meddelandena PropertyReferenceNotSupportedInDataSection och VariableReferenceNotSupportedInDataSection.

- PropertyReferenceNotSupportedInDataSection: egenskaps referenser är inte tillåtna i begränsat språk läge eller i ett data avsnitt.
- VariableReferenceNotSupportedInDataSection en variabel som inte kan refereras till i begränsat språk läge eller ett data avsnitt som refereras till.

När du kör `$ExecutionContext.SessionState.LanguageMode` kommandot i en nolanguage-session, returnerar PowerShell fel meddelandet ScriptsNotAllowed.

- ScriptsNotAllowed: syntaxen stöds inte av den här körnings utrymme. Detta kan bero på att det inte är i något språk läge.

## <a name="see-also"></a>SE ÄVEN

- [about_Session_Configuration_Files](about_Session_Configuration_Files.md)
- [about_Session_Configurations](about_Session_Configurations.md)
