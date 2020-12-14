---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 54a2ca8a28d54bfe1d9676acdaace4592f62620f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708555"
---
# New-CimSessionOption

## SAMMANFATTNING
Anger avancerade alternativ för New-CimSession-cmdleten.

## SYNTAX

### ProtocolTypeSet (standard)

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### WSManParameterSet

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### DcomParameterSet

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## BESKRIVNING

`New-CimSessionOption`Cmdleten skapar en instans av ett alternativ objekt för CIM-session. Du kan använda ett alternativ för CIM-session som inmatat på `New-CimSession` cmdleten för att ange alternativen för en CIM-session.

Denna cmdlet har två parameter uppsättningar, en för WsMan-alternativ och en för DCOM-alternativ (Distributed Component Object Model). Beroende på vilka parametrar du använder returnerar cmdleten antingen en instans av DCOM-session alternativ eller returnerar WsMan-session alternativ.

## EXEMPEL

### Exempel 1: skapa ett alternativ objekt för CIM-session för DCOM

I det här exemplet skapas ett objekt av alternativen CIM-session för DCOM-protokollet och det lagras i en variabel med namnet `$so` . Innehållet i variabeln skickas sedan till- `New-CimSession` cmdleten.
`New-CimSession` skapar sedan en ny CIM-session med fjärrservern med namnet Server01 med hjälp av de alternativ som definierats i variabeln.

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### Exempel 2: skapa ett alternativ objekt för CIM-sessionen för WsMan

I det här exemplet skapas ett objekt av alternativen för CIM-sessionen för WsMan-protokollet. Objektet innehåller konfigurationen för autentiseringsläget för **Kerberos** som anges av parametern **ProxyAuthentication** , de autentiseringsuppgifter som anges av parametern **ProxyCredential** och anger att kommandot är att hoppa över ca-kontrollen, hoppa över CN-kontrollen och använda SSL.

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### Exempel 3: skapa ett objekt för CIM-session med den angivna kulturen

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

I det här exemplet anges kulturen som används för CIM-sessionen. Som standard används-kulturen för-klienten när du utför åtgärder. Standard kulturen kan dock åsidosättas med hjälp av **kultur** parametern.

## PARAMETRAR

### – Kultur

Anger användar gränssnitts kulturen som ska användas för CIM-sessionen. Ange värdet för den här parametern med något av följande format:

- Ett kultur namn i `<languagecode2>-<country/regioncode2>` formatet "en-US".
- En variabel som innehåller ett **CultureInfo** -objekt.
- Ett kommando som hämtar ett **CultureInfo** -objekt, till exempel [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EncodePortInServicePrincipalName

Anger att Kerberos-anslutningen ansluter till en tjänst vars tjänst huvud namn (SPN) innehåller tjänstens port nummer. Den här typen av anslutning är inte vanlig.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

Anger kodningen som används för WsMan-protokollet. De acceptabla värdena för den här parametern är: **default**, **Utf8** eller **Utf16**.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -HttpPrefix

Anger del av HTTP-URL efter dator namn och port nummer. Det är inte vanligt att ändra detta. Som standard är värdet för den här parametern **/WSMan**.

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Personifiering

Skapar en DCOM-session som Windows Management Instrumentation (WMI) med hjälp av personifiering.

Giltiga värden för den här parametern är:

- Standard: DCOM kan välja personifieringsnivå med hjälp av sin normala algoritm för säkerhets förhandling.
- Ingen: klienten är anonym för servern. Server processen kan personifiera klienten, men personifieringstoken innehåller ingen information och kan inte användas.
- Identifiera: tillåter objekt att fråga om autentiseringsuppgifterna för anroparen.
- Personifiera: tillåter att objekt använder autentiseringsuppgifterna för anroparen.
- Delegera: tillåter objekt att tillåta att andra objekt använder autentiseringsuppgifterna för anroparen.

Om ingen **personifiering** har angetts `New-CimSession` använder cmdleten värdet **impersonate**.

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxEnvelopeSizeKB

Anger storleks gränsen för WsMan-XML-meddelanden för båda riktningarna.

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Encryption

Anger att data kryptering är inaktive rad.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketIntegrity

Anger att DCOM-sessionen som skapats till WMI Component Object Model använder _PacketIntegrity_ -funktionen (com). Som standard har alla CIM-sessioner som skapats med hjälp av DCOM parametern **PacketIntegrity** inställd på **True**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketPrivacy

Skapar en DCOM-session för WMI med hjälp av COM- _PacketPrivacy_. Som standard har alla CIM-sessioner som skapats med hjälp av DCOM parametern **PacketPrivacy** inställd på **True**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Anger vilket protokoll som ska användas. De acceptabla värdena för den här parametern är: **DCOM**, **default** eller **WSMan**.

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyAuthentication

Anger autentiseringsmetoden som ska användas för proxy-matchning. De acceptabla värdena för den här parametern är: **standard**, **Digest**, **Negotiate**, **Basic**, **Kerberos**, **NtlmDomain** eller **CredSsp**.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCertificateThumbprint

Anger det digitala offentliga nyckel certifikatet (x. 509) för ett användar konto för proxyautentisering.
Ange certifikatets tumavtryck. Certifikat används i klient certifikat-baserad autentisering. De kan bara mappas till lokala användar konton och de fungerar inte med domän konton.

Använd cmdletarna eller i PowerShell-certifikatet för att hämta ett tumavtryck för certifikatet `Get-Item` `Get-ChildItem` : enhet.

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Anger de autentiseringsuppgifter som ska användas för proxyautentisering. Ange något av följande:

- En variabel som innehåller ett PSCredential-objekt.
- Ett kommando som hämtar ett PSCredential-objekt, till exempel `Get-Credential`

Om det här alternativet inte har angetts kan du inte ange några autentiseringsuppgifter.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyType

Anger den värd namn matchnings funktion som ska användas. De acceptabla värdena för den här parametern är: **ingen**, **WinHTTP**, **Auto** eller **InternetExplorer**.

Standardvärdet för den här parametern är **InternetExplorer**.

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCACheck

Anger att när du ansluter via HTTPS, verifierar inte klienten att Server certifikatet är signerat av en betrodd certifikat utfärdare (CA).

Använd bara den här parametern om fjärrdatorn är betrodd med en annan mekanism, t. ex. när fjärrdatorn är en del av ett nätverk som är fysiskt säkert och isolerat, eller när fjärrdatorn visas som en betrodd värd i en WinRM-konfiguration.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCNCheck

Anger att serverns certifikats allmänna namn inte behöver matcha Server namnet för servern. Använd den här parametern endast för fjärråtgärder med betrodda datorer som använder HTTPS-protokollet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipRevocationCheck

Anger att återkallnings kontrollen för Server certifikat hoppas över. Använd endast den här parametern för betrodda datorer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Värdet

Anger användar gränssnitts kulturen som ska användas för CIM-sessionen. Ange värdet för den här parametern med något av följande format:

- Ett kultur namn i `<languagecode2>-<country/regioncode2>` formatet "en-US".
- En variabel som innehåller ett CultureInfo-objekt.
- Ett kommando som hämtar ett CultureInfo-objekt, till exempel `Get-Culture` .

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseSsl

Anger att SSL ska användas för att upprätta en anslutning till fjärrdatorn. Som standard används inte SSL. WsMan krypterar allt innehåll som överförs via nätverket, även när du använder HTTP.

Med den här parametern kan du ange ytterligare skydd av HTTPS i stället för HTTP. Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.

Vi rekommenderar att du bara använder den här parametern när parametern **PacketPrivacy** inte anges.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

Denna cmdlet accepterar inga inobjekt.

## UTDATA

### CIMSessionOption

Den här cmdleten returnerar ett objekt som innehåller information om CIM-sessionsinformation.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-ChildItem](../microsoft.powershell.management/get-childitem.md)

[Get-Credential](../microsoft.powershell.security/get-credential.md)

[Get-Culture](../microsoft.powershell.utility/get-culture.md)

[Hämta objekt](../microsoft.powershell.management/get-item.md)

[New-CimSession](New-CimSession.md)

