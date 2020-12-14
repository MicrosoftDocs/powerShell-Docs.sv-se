---
description: WSMan
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan-Provider
ms.openlocfilehash: 32baaaec3589fc9d6f4c2319f47d56bca777f738
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710327"
---
# <a name="wsman-provider"></a>WSMan-Provider

## <a name="provider-name"></a>Providernamn

WSMan

## <a name="drives"></a>Enheter

`WSMan:`

## <a name="short-description"></a>Kort beskrivning

Ger åtkomst till konfigurations information för hantering av webb tjänster (WS-Management).

## <a name="detailed-description"></a>Detaljerad beskrivning

Med **WSMan** -providern för PowerShell kan du lägga till, ändra, rensa och ta bort WS-Management konfigurations data på lokala eller fjärranslutna datorer.

**WSMan** -providern exponerar en PowerShell-enhet med en katalog struktur som motsvarar en logisk gruppering av WS-Management konfigurations inställningar. Dessa grupperingar kallas behållare.

Från och med Windows PowerShell 3,0 har **WSMan** -providern uppdaterats för att stödja nya egenskaper för sessionsinställningar, till exempel **OutputBufferingMode**. Sessionens konfigurationer visas som objekt i katalogen plugin-program för `WSMan:` enheten och egenskaperna visas som objekt i varje konfiguration av sessionen.

**WSMan** -providern stöder följande cmdletar, som beskrivs i den här artikeln.

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> Du kan använda kommandon i `WSMan:` enheten för att ändra värdena för de nya egenskaperna. Du kan dock inte använda `WSMan:` enheten i PowerShell 2,0 för att ändra egenskaper som introduceras i Windows PowerShell 3,0.
> Även om inget fel genereras är kommandona inte effektiva att ändra inställningarna, använda **WSMan** -enheten i Windows PowerShell 3,0.

### <a name="organization-of-the-wsman-drive"></a>Organisation för WSMan: Drive

- **Klient**: du kan konfigurera olika aspekter av WS-Management-klienten. Konfigurations informationen lagras i registret.

- **Tjänst**: du kan konfigurera olika aspekter av tjänsten WS-Management.
  Konfigurations informationen lagras i registret.
  > [!NOTE]
  > Tjänst konfigurationen kallas ibland för Server konfiguration.

- **Shell**: du kan konfigurera olika aspekter av WS-Management Shell, till exempel inställningen att tillåta fjärråtkomst (**AllowRemoteShellAccess**) och det maximala antalet samtidiga användare som tillåts (**MaxConcurrentUsers**).

- **Lyssnare**: du kan skapa och konfigurera en lyssnare. En lyssnare är en hanterings tjänst som implementerar WS-Management protokoll för att skicka och ta emot meddelanden.

- **Plugin**: plugin-program läses in och används av WS-Managements tjänsten för att tillhandahålla olika funktioner. Som standard tillhandahåller PowerShell tre plugin-program:
  - Plugin-programmet för Event Forwarding.
  - Microsoft. PowerShell-plugin-programmet.
  - Plugin-programmet för Windows Management Instrumentation (WMI) providern.
  Dessa tre plugin-program stöder vidarebefordran av händelser, konfiguration och WMI-åtkomst.

- **ClientCertificate**: du kan skapa och konfigurera ett klient certifikat.
  Ett klient certifikat används när den WS-Management klienten är konfigurerad för att använda certifikatautentisering.

### <a name="directory-hierarchy-of-the-wsman-provider"></a>Katalog-hierarki för WSMan-providern

Katalog-hierarkin för WSMan-providern för den lokala datorn är följande.

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

Hierarkin för WSMan-providern för en fjärrdator är samma som en lokal dator. Men för att få åtkomst till konfigurations inställningarna för en fjärrdator måste du upprätta en anslutning till fjärrdatorn med hjälp av [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan). När en anslutning har gjorts till en fjärrdator visas namnet på fjärrdatorn i providern.

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a>Navigera i filen WSMan: Drive

Detta kommando använder `Set-Location` cmdleten för att ändra den aktuella platsen till `WSMan:` enheten.

```powershell
Set-Location WSMan:
```

Om du vill återgå till en fil systemen het skriver du enhetens namn. Skriv till exempel.

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a>Navigera till en lagrings plats för fjärrsystem

Det här kommandot använder `Set-Location` kommandot för att ändra den aktuella platsen till rot platsen på den fjärranslutna system lagrings platsen. Använd ett omvänt snedstreck eller ett snedstreck `\` `/` för att ange `WSMan:` enhetens nivå.

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> Kommandot ovan förutsätter att det redan finns en anslutning till fjärrdatorn.

## <a name="displaying-the-contents-of-the-wsman-drive"></a>Visar innehållet i filen WSMan: Drive

Det här kommandot använder `Get-Childitem` cmdlet: en för att visa WS-Management butikerna på localhost-lagringsplatsen.

```powershell
Get-ChildItem -path WSMan:\Localhost
```

Om du är i `WSMan:` enheten kan du utelämna enhets namnet.

Det här kommandot använder `Get-Childitem` cmdleten för att visa WS-Management butiker på fjärrdatorn "SERVER01".

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> Kommandot ovan förutsätter att det redan finns en anslutning till fjärrdatorn.

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a>Ange värdet för objekt i WSMAN: Drive

Du kan använda `Set-Item` cmdleten för att ändra konfigurations inställningarna i `WSMAN` enheten. I följande exempel anges värdet **TrustedHosts** för att acceptera alla värdar med suffixet "contoso.com".

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

`Set-Item`Cmdleten stöder ytterligare en parameter `-Concatenate` som lägger till ett värde i stället för att ändra det. I följande exempel läggs ett nytt värde "*. domain2.com" till i det gamla värdet som är lagrat i `TrustedHost:`

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a>Skapa objekt i WSMAN: Drive

### <a name="creating-a-new-listener"></a>Skapa en ny lyssnare

`New-Item`Cmdleten skapar objekt i en provider. Varje provider har olika objekt typer som du kan skapa. I `WSMAN:` enheten kan du skapa *lyssnare* som du konfigurerar för att ta emot och svara på fjärrbegäranden. Följande kommando skapar en ny HTTP-lyssnare med hjälp av `New-Item` cmdleten.

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a>Skapa ett nytt plugin-program

Det här kommandot skapar (registrerar) ett plugin-program för tjänsten WS-Management.

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a>Skapa en ny resurs post

Det här kommandot skapar en resurs post i resurs katalogen i en TestPlugin. Det här kommandot förutsätter att en TestPlugin har skapats med ett separat kommando.

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a>Skapa en ny säkerhets post för en resurs

Det här kommandot skapar en säkerhets post i säkerhets katalogen för Resource_5967683 (en angiven resurs). Det här kommandot förutsätter att resurs posten har skapats med ett separat kommando.

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a>Skapa ett nytt klient certifikat

Det här kommandot skapar **ClientCertificate** -poster som kan användas av den WS-Management klienten. Den nya **ClientCertificate** visas under katalogen **ClientCertificate** som "ClientCertificate_1234567890". Alla parametrar är obligatoriska. **Utfärdaren** måste vara tumavtryck för utfärdarcertifikatet.

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a>Skapa en ny initierings parameter

Det här kommandot skapar en initierings parameter med namnet "testparametername" i katalogen "InitializationParameters". Det här kommandot förutsätter att "TestPlugin" har skapats med ett separat kommando.

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.

### <a name="address-string"></a>Adresspool \<String\>

Anger adressen som den här lyssnaren skapades för. Värdet kan vara något av följande:

- Den litterala strängen "*". (Jokertecknet ( `*` ) gör att kommandot binder alla IP-adresser på alla nätverkskort.)
- Den litterala strängen "IP:" följt av en giltig IP-adress i antingen IPv4 punktavgränsat decimal format eller i IPv6-klonat-hexadecimalt format.
- Den litterala strängen "MAC:" följt av MAC-adressen för ett kort.
  Till exempel: MAC: 32-a3-58 -90-CC.

> [!NOTE]
> Värdet Address anges när du skapar en lyssnare.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a>Funktionen \<Enumeration\>

När du arbetar med *plugin-program,* anger den här parametern en åtgärd som stöds på den här Uniform Resource Identifier (URI). Du måste skapa en post för varje typ av åtgärd som URI: n stöder. Du kan ange giltiga attribut för en specifik åtgärd, om åtgärden stöder det.

Dessa attribut är **SupportsFiltering** och **SupportsFragment**.

- **Skapa**: skapa-åtgärder stöds på URI: n.
  - Attributet **SupportFragment**  används om Create-åtgärden stöder konceptet.
  - Attributet **SupportFiltering** är inte giltigt för Create-åtgärder och ska vara inställt på "false".
  > [!NOTE]
  > Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.
- **Ta bort**: borttagnings åtgärder stöds på URI: n.
  - Attributet **SupportFragment** används om borttagnings åtgärden stöder konceptet.
  - Attributet **SupportFiltering** är inte giltigt för Delete-åtgärder och ska vara inställt på "false".
  > [!NOTE]
  > Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.
- **Uppräkning**: uppräknings åtgärder stöds på URI: n.
  - Attributet **SupportFragment** stöds inte för uppräknings åtgärder och ska vara inställt på false.
  - Attributet **SupportFiltering** är giltigt och om plugin-programmet stöder filtrering ska det här attributet anges till "true".
  > [!NOTE]
  > Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.
- **Get**: get-åtgärder stöds på URI: n.
  - Attributet **SupportFragment** används om Get-åtgärden stöder konceptet.
  - Attributet **SupportFiltering** är inte giltigt för Get-åtgärder och ska vara inställt på "false".
  > [!NOTE]
  > Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.
- **Invoke**: Invoke-åtgärder stöds på URI: n.
  - Attributet **SupportFragment** stöds inte för Invoke-åtgärder och ska vara inställt på false.
  - Attributet **SupportFiltering** är inte giltigt och ska vara inställt på "false".
  > [!NOTE]
  > Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.
- **Lägg** till: placerings åtgärder stöds på URI: n.
  - Attributet **SupportFragment** används om åtgärden Lägg till stöder konceptet.
  - Attributet **SupportFiltering** är inte giltigt för att införa åtgärder och ska vara inställt på "false".
  > [!NOTE]
  > Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.
- **Prenumerera**: prenumerations åtgärder stöds på URI: n.
  - Attributet **SupportFragment** stöds inte för prenumerations åtgärder och ska vara inställt på false.
  - Attributet **SupportFiltering** är inte giltigt för prenumerations åtgärder och ska vara inställt på "false".
  > [!NOTE]
  > Den här åtgärden är inte giltig för en URI om Shell-åtgärder också stöds.
- **Shell**: Shell-åtgärder stöds på URI: n.
  - Attributet **SupportFragment** stöds inte för Shell-åtgärder och ska vara inställt på "false".
  - Attributet **SupportFiltering** är inte giltigt för Shell-åtgärder och ska vara inställt på "false".
  > [!NOTE]
  > Den här åtgärden är inte giltig för en URI om en annan åtgärd också stöds.
  > [!NOTE]
  > Om en gränssnitts åtgärd har kon figurer ATS för en URI, get-, get-, Create-, DELETE-, Invoke-och Enumeration-åtgärder bearbetas internt i WS-Management (WinRM)-tjänsten för att hantera gränssnitt. Därför kan plugin-programmet inte hantera åtgärderna.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a>CertificateThumbprint \<String\>

Anger tumavtrycket för tjänst certifikatet.

Det här värdet representerar strängen med tvåsiffriga hexadecimala värden i certifikatets tumavtryck-fält. Den anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden. Certifikat används i klient certifikat-baserad autentisering. De kan endast mappas till lokala användar konton och de fungerar inte med domän konton. Använd `Get-Item` `Get-ChildItem` cmdletarna eller i PowerShell-enheten för att hämta ett tumavtryck för certifikatet `Cert:` .

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a>Aktiva \<Boolean\>

Anger om lyssnaren är aktive rad eller inaktive rad. Standardvärdet är true.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a>Fil namn (plugin-program) \<String\>

Anger fil namnet för åtgärds-plugin-programmet. Alla miljövariabler som placeras i den här posten kommer att expanderas i användarnas kontext när en begäran tas emot. Eftersom varje användare kan ha en annan version av samma miljö variabel kan varje användare ha olika plugin-program. Den här posten får inte vara tom och måste peka på ett giltigt plugin-program.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a>Värdnamn \<String\>

Anger värd namnet för den dator där tjänsten WS-Management (WinRM) körs.

Värdet måste vara ett fullständigt kvalificerat domän namn, en IPv4-eller IPv6 literal sträng eller ett jokertecken.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a>Utfärdare \<String\>

Anger namnet på den certifikat utfärdare som utfärdade certifikatet.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a>Plugin \<\> -program för WS-Management plugin-program är interna DLL-bibliotek (Dynamic Link Libraries)

den ansluter till och utökar funktionerna i WS-Management. API: et för WSW-Management-plugin innehåller funktioner som gör att en användare kan skriva plugin-program genom att implementera vissa API: er för resurs-URI: er och åtgärder som stöds. När plugin-programmen har kon figurer ATS för antingen tjänsten WS-Management (WinRM) eller för Internet Information Services (IIS), läses plugin-programmen in i WS-Management-värden eller IIS-värden. Fjärrbegäranden dirigeras till dessa plugin-ingångs punkter för att utföra åtgärder.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a>Lastning \<Unsigned Short Integer\>

Anger den TCP-port som den här lyssnaren har skapats för. Du kan ange ett värde mellan 1 och 65535.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Klusterresursen \<String\>

Anger en slut punkt som representerar en distinkt typ av hanterings åtgärd eller värde. En tjänst exponerar en eller flera resurser och vissa resurser kan ha mer än en instans. En hanterings resurs liknar en WMI-klass eller en databas tabell, och en instans liknar en instans av klassen eller en rad i tabellen. **Win32_LogicalDisk** -klassen representerar till exempel en resurs. `Win32_LogicalDisk="C:\\"` är en angiven instans av resursen.

En Uniform Resource Identifier (URI) innehåller ett prefix och en sökväg till en resurs.
Exempel:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Klusterresursen \<String\>

Anger Uniform Resource Identifier (URI) som identifierar en speciell typ av resurs, till exempel en disk eller en process, på en dator.

En URI består av ett prefix och en sökväg till en resurs. Exempel:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a>SDKVersion \<String\>

Anger versionen för WS-Management plugin-programmet SDK. Det enda giltiga värdet är
1.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a>Motiv \<String\>

Anger den entitet som identifieras av certifikatet.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a>Källtransportadr \<String\>

Anger vilken transport som ska användas för att skicka och ta emot WS-Management protokoll förfrågningar och svar. Värdet måste vara antingen HTTP eller HTTPS.

Obs: transport svärdet anges när du skapar en lyssnare.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a>URI \<String\>

Identifierar den URI för vilken åtkomst är tillåten baserat på värdet för SDDL-parametern.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a>URLPrefix \<String\>

Ett URL-prefix som accepterar HTTP-eller HTTPS-begäranden. Detta är en sträng som endast innehåller tecknen `[a-z]` , `[A-Z]` , `[9-0]` , under streck ( `_` ) och omvänt snedstreck ( `/` ). Strängen får inte börja med eller sluta med ett omvänt snedstreck ( `/` ). Om dator namnet till exempel är "SampleComputer" anger WS-Management klienten `http://SampleMachine/URLPrefix` i mål adressen.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a>Värde \<String\>

Anger värdet för en initierings parameter, vilket är ett plugin-/regionsspecifika värde som används för att ange konfigurations alternativ.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a>XMLRenderingType \<String\>

Anger det format i vilket XML skickas till plugin-program via **WSMAN_DATA** -objektet. Följande är giltiga värden:

- Text: inkommande XML-data finns i en **WSMAN_DATA_TYPE_TEXT** -struktur som representerar XML-filen som **PCWSTR** -minnesbuffert.
- XMLReader: inkommande XML-data finns i en **WSMAN_DATA_TYPE_WS_XML_READER** -struktur som representerar XML som ett **XmlReader** -objekt, som definieras i huvud filen "WebServices. h".

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>Använda pipelinen

Provider-cmdletar accepterar pipeline-ininformation. Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.
Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.

## <a name="getting-help"></a>Få hjälp

Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.

Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a>Se även

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

