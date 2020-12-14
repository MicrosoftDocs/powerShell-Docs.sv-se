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
# <span data-ttu-id="1144c-102">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="1144c-102">New-CimSessionOption</span></span>

## <span data-ttu-id="1144c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1144c-103">SYNOPSIS</span></span>
<span data-ttu-id="1144c-104">Anger avancerade alternativ för New-CimSession-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1144c-104">Specifies advanced options for the New-CimSession cmdlet.</span></span>

## <span data-ttu-id="1144c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1144c-105">SYNTAX</span></span>

### <span data-ttu-id="1144c-106">ProtocolTypeSet (standard)</span><span class="sxs-lookup"><span data-stu-id="1144c-106">ProtocolTypeSet (Default)</span></span>

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### <span data-ttu-id="1144c-107">WSManParameterSet</span><span class="sxs-lookup"><span data-stu-id="1144c-107">WSManParameterSet</span></span>

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### <span data-ttu-id="1144c-108">DcomParameterSet</span><span class="sxs-lookup"><span data-stu-id="1144c-108">DcomParameterSet</span></span>

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## <span data-ttu-id="1144c-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1144c-109">DESCRIPTION</span></span>

<span data-ttu-id="1144c-110">`New-CimSessionOption`Cmdleten skapar en instans av ett alternativ objekt för CIM-session.</span><span class="sxs-lookup"><span data-stu-id="1144c-110">The `New-CimSessionOption` cmdlet creates an instance of a CIM session options object.</span></span> <span data-ttu-id="1144c-111">Du kan använda ett alternativ för CIM-session som inmatat på `New-CimSession` cmdleten för att ange alternativen för en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="1144c-111">You use a CIM session options object as input to the `New-CimSession` cmdlet to specify the options for a CIM session.</span></span>

<span data-ttu-id="1144c-112">Denna cmdlet har två parameter uppsättningar, en för WsMan-alternativ och en för DCOM-alternativ (Distributed Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="1144c-112">This cmdlet has two parameter sets, one for WsMan options and one for Distributed Component Object Model (DCOM) options.</span></span> <span data-ttu-id="1144c-113">Beroende på vilka parametrar du använder returnerar cmdleten antingen en instans av DCOM-session alternativ eller returnerar WsMan-session alternativ.</span><span class="sxs-lookup"><span data-stu-id="1144c-113">Depending on which parameters you use, the cmdlet returns either an instance of DCOM session options or returns WsMan session options.</span></span>

## <span data-ttu-id="1144c-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1144c-114">EXAMPLES</span></span>

### <span data-ttu-id="1144c-115">Exempel 1: skapa ett alternativ objekt för CIM-session för DCOM</span><span class="sxs-lookup"><span data-stu-id="1144c-115">Example 1: Create a CIM session options object for DCOM</span></span>

<span data-ttu-id="1144c-116">I det här exemplet skapas ett objekt av alternativen CIM-session för DCOM-protokollet och det lagras i en variabel med namnet `$so` .</span><span class="sxs-lookup"><span data-stu-id="1144c-116">This example creates a CIM session options object for the DCOM protocol and stores it in a variable named `$so`.</span></span> <span data-ttu-id="1144c-117">Innehållet i variabeln skickas sedan till- `New-CimSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1144c-117">The contents of the variable are then passed to the `New-CimSession` cmdlet.</span></span>
<span data-ttu-id="1144c-118">`New-CimSession` skapar sedan en ny CIM-session med fjärrservern med namnet Server01 med hjälp av de alternativ som definierats i variabeln.</span><span class="sxs-lookup"><span data-stu-id="1144c-118">`New-CimSession` then creates a new CIM session with the remote server named Server01, using the options defined in the variable.</span></span>

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### <span data-ttu-id="1144c-119">Exempel 2: skapa ett alternativ objekt för CIM-sessionen för WsMan</span><span class="sxs-lookup"><span data-stu-id="1144c-119">Example 2: Create a CIM session options object for WsMan</span></span>

<span data-ttu-id="1144c-120">I det här exemplet skapas ett objekt av alternativen för CIM-sessionen för WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="1144c-120">This example creates a CIM session options object for the WsMan protocol.</span></span> <span data-ttu-id="1144c-121">Objektet innehåller konfigurationen för autentiseringsläget för **Kerberos** som anges av parametern **ProxyAuthentication** , de autentiseringsuppgifter som anges av parametern **ProxyCredential** och anger att kommandot är att hoppa över ca-kontrollen, hoppa över CN-kontrollen och använda SSL.</span><span class="sxs-lookup"><span data-stu-id="1144c-121">The object contains configuration for the authentication mode of **Kerberos** specified by the **ProxyAuthentication** parameter, the credentials specified by the **ProxyCredential** parameter, and specifies that the command is to skip the CA check, skip the CN check, and use SSL.</span></span>

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### <span data-ttu-id="1144c-122">Exempel 3: skapa ett objekt för CIM-session med den angivna kulturen</span><span class="sxs-lookup"><span data-stu-id="1144c-122">Example 3: Create a CIM session options object with the culture specified</span></span>

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

<span data-ttu-id="1144c-123">I det här exemplet anges kulturen som används för CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1144c-123">This example specifies the culture that is used for the CIM session.</span></span> <span data-ttu-id="1144c-124">Som standard används-kulturen för-klienten när du utför åtgärder.</span><span class="sxs-lookup"><span data-stu-id="1144c-124">By default, the culture of the client is used when performing operations.</span></span> <span data-ttu-id="1144c-125">Standard kulturen kan dock åsidosättas med hjälp av **kultur** parametern.</span><span class="sxs-lookup"><span data-stu-id="1144c-125">However, the default culture can be overridden using the **Culture** parameter.</span></span>

## <span data-ttu-id="1144c-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1144c-126">PARAMETERS</span></span>

### <span data-ttu-id="1144c-127">– Kultur</span><span class="sxs-lookup"><span data-stu-id="1144c-127">-Culture</span></span>

<span data-ttu-id="1144c-128">Anger användar gränssnitts kulturen som ska användas för CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1144c-128">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="1144c-129">Ange värdet för den här parametern med något av följande format:</span><span class="sxs-lookup"><span data-stu-id="1144c-129">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="1144c-130">Ett kultur namn i `<languagecode2>-<country/regioncode2>` formatet "en-US".</span><span class="sxs-lookup"><span data-stu-id="1144c-130">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="1144c-131">En variabel som innehåller ett **CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1144c-131">A variable that contains a **CultureInfo** object.</span></span>
- <span data-ttu-id="1144c-132">Ett kommando som hämtar ett **CultureInfo** -objekt, till exempel [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)</span><span class="sxs-lookup"><span data-stu-id="1144c-132">A command that gets a **CultureInfo** object, such as [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)</span></span>

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

### <span data-ttu-id="1144c-133">-EncodePortInServicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="1144c-133">-EncodePortInServicePrincipalName</span></span>

<span data-ttu-id="1144c-134">Anger att Kerberos-anslutningen ansluter till en tjänst vars tjänst huvud namn (SPN) innehåller tjänstens port nummer.</span><span class="sxs-lookup"><span data-stu-id="1144c-134">Indicates that the Kerberos connection is connecting to a service whose service principal name (SPN) includes the service port number.</span></span> <span data-ttu-id="1144c-135">Den här typen av anslutning är inte vanlig.</span><span class="sxs-lookup"><span data-stu-id="1144c-135">This type of connection is not common.</span></span>

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

### <span data-ttu-id="1144c-136">-Encoding</span><span class="sxs-lookup"><span data-stu-id="1144c-136">-Encoding</span></span>

<span data-ttu-id="1144c-137">Anger kodningen som används för WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="1144c-137">Specifies the encoding used for the WsMan protocol.</span></span> <span data-ttu-id="1144c-138">De acceptabla värdena för den här parametern är: **default**, **Utf8** eller **Utf16**.</span><span class="sxs-lookup"><span data-stu-id="1144c-138">The acceptable values for this parameter are: **Default**, **Utf8**, or **Utf16**.</span></span>

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

### <span data-ttu-id="1144c-139">-HttpPrefix</span><span class="sxs-lookup"><span data-stu-id="1144c-139">-HttpPrefix</span></span>

<span data-ttu-id="1144c-140">Anger del av HTTP-URL efter dator namn och port nummer.</span><span class="sxs-lookup"><span data-stu-id="1144c-140">Specifies the part of the HTTP URL after the computer name and port number.</span></span> <span data-ttu-id="1144c-141">Det är inte vanligt att ändra detta.</span><span class="sxs-lookup"><span data-stu-id="1144c-141">Changing this is not common.</span></span> <span data-ttu-id="1144c-142">Som standard är värdet för den här parametern **/WSMan**.</span><span class="sxs-lookup"><span data-stu-id="1144c-142">By default, the value of this parameter is **/wsman**.</span></span>

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

### <span data-ttu-id="1144c-143">-Personifiering</span><span class="sxs-lookup"><span data-stu-id="1144c-143">-Impersonation</span></span>

<span data-ttu-id="1144c-144">Skapar en DCOM-session som Windows Management Instrumentation (WMI) med hjälp av personifiering.</span><span class="sxs-lookup"><span data-stu-id="1144c-144">Creates a DCOM session to Windows Management Instrumentation (WMI) using impersonation.</span></span>

<span data-ttu-id="1144c-145">Giltiga värden för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="1144c-145">Valid values for this parameter are:</span></span>

- <span data-ttu-id="1144c-146">Standard: DCOM kan välja personifieringsnivå med hjälp av sin normala algoritm för säkerhets förhandling.</span><span class="sxs-lookup"><span data-stu-id="1144c-146">Default: DCOM can choose the impersonation level using its normal security negotiation algorithm.</span></span>
- <span data-ttu-id="1144c-147">Ingen: klienten är anonym för servern.</span><span class="sxs-lookup"><span data-stu-id="1144c-147">None: The client is anonymous to the server.</span></span> <span data-ttu-id="1144c-148">Server processen kan personifiera klienten, men personifieringstoken innehåller ingen information och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="1144c-148">The server process can impersonate the client, but the impersonation token does not contain any information and cannot be used.</span></span>
- <span data-ttu-id="1144c-149">Identifiera: tillåter objekt att fråga om autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="1144c-149">Identify: Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="1144c-150">Personifiera: tillåter att objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="1144c-150">Impersonate: Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="1144c-151">Delegera: tillåter objekt att tillåta att andra objekt använder autentiseringsuppgifterna för anroparen.</span><span class="sxs-lookup"><span data-stu-id="1144c-151">Delegate: Allows objects to permit other objects to use the credentials of the caller.</span></span>

<span data-ttu-id="1144c-152">Om ingen **personifiering** har angetts `New-CimSession` använder cmdleten värdet **impersonate**.</span><span class="sxs-lookup"><span data-stu-id="1144c-152">If **Impersonation** is not specified, the `New-CimSession` cmdlet uses the value of **Impersonate**.</span></span>

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

### <span data-ttu-id="1144c-153">-MaxEnvelopeSizeKB</span><span class="sxs-lookup"><span data-stu-id="1144c-153">-MaxEnvelopeSizeKB</span></span>

<span data-ttu-id="1144c-154">Anger storleks gränsen för WsMan-XML-meddelanden för båda riktningarna.</span><span class="sxs-lookup"><span data-stu-id="1144c-154">Specifies the size limit of WsMan XML messages for either direction.</span></span>

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

### <span data-ttu-id="1144c-155">– Encryption</span><span class="sxs-lookup"><span data-stu-id="1144c-155">-NoEncryption</span></span>

<span data-ttu-id="1144c-156">Anger att data kryptering är inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="1144c-156">Specifies that data encryption is turned off.</span></span>

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

### <span data-ttu-id="1144c-157">-PacketIntegrity</span><span class="sxs-lookup"><span data-stu-id="1144c-157">-PacketIntegrity</span></span>

<span data-ttu-id="1144c-158">Anger att DCOM-sessionen som skapats till WMI Component Object Model använder _PacketIntegrity_ -funktionen (com).</span><span class="sxs-lookup"><span data-stu-id="1144c-158">Specifies that the DCOM session created to WMI uses the Component Object Model (COM) _PacketIntegrity_ functionality.</span></span> <span data-ttu-id="1144c-159">Som standard har alla CIM-sessioner som skapats med hjälp av DCOM parametern **PacketIntegrity** inställd på **True**.</span><span class="sxs-lookup"><span data-stu-id="1144c-159">By default, all CIM sessions created using DCOM have the **PacketIntegrity** parameter set to **True**.</span></span>

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

### <span data-ttu-id="1144c-160">-PacketPrivacy</span><span class="sxs-lookup"><span data-stu-id="1144c-160">-PacketPrivacy</span></span>

<span data-ttu-id="1144c-161">Skapar en DCOM-session för WMI med hjälp av COM- _PacketPrivacy_.</span><span class="sxs-lookup"><span data-stu-id="1144c-161">Creates a DCOM session to WMI using the COM _PacketPrivacy_.</span></span> <span data-ttu-id="1144c-162">Som standard har alla CIM-sessioner som skapats med hjälp av DCOM parametern **PacketPrivacy** inställd på **True**.</span><span class="sxs-lookup"><span data-stu-id="1144c-162">By default, all CIM sessions created using DCOM have the **PacketPrivacy** parameter set to **true**.</span></span>

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

### <span data-ttu-id="1144c-163">-Protocol</span><span class="sxs-lookup"><span data-stu-id="1144c-163">-Protocol</span></span>

<span data-ttu-id="1144c-164">Anger vilket protokoll som ska användas.</span><span class="sxs-lookup"><span data-stu-id="1144c-164">Specifies the protocol to use.</span></span> <span data-ttu-id="1144c-165">De acceptabla värdena för den här parametern är: **DCOM**, **default** eller **WSMan**.</span><span class="sxs-lookup"><span data-stu-id="1144c-165">The acceptable values for this parameter are: **DCOM**, **Default**, or **Wsman**.</span></span>

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

### <span data-ttu-id="1144c-166">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="1144c-166">-ProxyAuthentication</span></span>

<span data-ttu-id="1144c-167">Anger autentiseringsmetoden som ska användas för proxy-matchning.</span><span class="sxs-lookup"><span data-stu-id="1144c-167">Specifies the authentication method to use for proxy resolution.</span></span> <span data-ttu-id="1144c-168">De acceptabla värdena för den här parametern är: **standard**, **Digest**, **Negotiate**, **Basic**, **Kerberos**, **NtlmDomain** eller **CredSsp**.</span><span class="sxs-lookup"><span data-stu-id="1144c-168">The acceptable values for this parameter are: **Default**, **Digest**, **Negotiate**, **Basic**, **Kerberos**, **NtlmDomain**, or **CredSsp**.</span></span>

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

### <span data-ttu-id="1144c-169">-ProxyCertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="1144c-169">-ProxyCertificateThumbprint</span></span>

<span data-ttu-id="1144c-170">Anger det digitala offentliga nyckel certifikatet (x. 509) för ett användar konto för proxyautentisering.</span><span class="sxs-lookup"><span data-stu-id="1144c-170">Specifies the (x.509) digital public key certificate of a user account for proxy authentication.</span></span>
<span data-ttu-id="1144c-171">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="1144c-171">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="1144c-172">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="1144c-172">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="1144c-173">De kan bara mappas till lokala användar konton och de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="1144c-173">They can only be mapped to local user accounts and they do not work with domain accounts.</span></span>

<span data-ttu-id="1144c-174">Använd cmdletarna eller i PowerShell-certifikatet för att hämta ett tumavtryck för certifikatet `Get-Item` `Get-ChildItem` : enhet.</span><span class="sxs-lookup"><span data-stu-id="1144c-174">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="1144c-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="1144c-175">-ProxyCredential</span></span>

<span data-ttu-id="1144c-176">Anger de autentiseringsuppgifter som ska användas för proxyautentisering.</span><span class="sxs-lookup"><span data-stu-id="1144c-176">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="1144c-177">Ange något av följande:</span><span class="sxs-lookup"><span data-stu-id="1144c-177">Enter one of the following:</span></span>

- <span data-ttu-id="1144c-178">En variabel som innehåller ett PSCredential-objekt.</span><span class="sxs-lookup"><span data-stu-id="1144c-178">A variable that contains a PSCredential object.</span></span>
- <span data-ttu-id="1144c-179">Ett kommando som hämtar ett PSCredential-objekt, till exempel `Get-Credential`</span><span class="sxs-lookup"><span data-stu-id="1144c-179">A command that gets a PSCredential object, such as `Get-Credential`</span></span>

<span data-ttu-id="1144c-180">Om det här alternativet inte har angetts kan du inte ange några autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1144c-180">If this option is not set, then you cannot specify any credentials.</span></span>

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

### <span data-ttu-id="1144c-181">-ProxyType</span><span class="sxs-lookup"><span data-stu-id="1144c-181">-ProxyType</span></span>

<span data-ttu-id="1144c-182">Anger den värd namn matchnings funktion som ska användas.</span><span class="sxs-lookup"><span data-stu-id="1144c-182">Specifies the host name resolution mechanism to use.</span></span> <span data-ttu-id="1144c-183">De acceptabla värdena för den här parametern är: **ingen**, **WinHTTP**, **Auto** eller **InternetExplorer**.</span><span class="sxs-lookup"><span data-stu-id="1144c-183">The acceptable values for this parameter are: **None**, **WinHttp**, **Auto**, or **InternetExplorer**.</span></span>

<span data-ttu-id="1144c-184">Standardvärdet för den här parametern är **InternetExplorer**.</span><span class="sxs-lookup"><span data-stu-id="1144c-184">The default value of this parameter is **InternetExplorer**.</span></span>

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

### <span data-ttu-id="1144c-185">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="1144c-185">-SkipCACheck</span></span>

<span data-ttu-id="1144c-186">Anger att när du ansluter via HTTPS, verifierar inte klienten att Server certifikatet är signerat av en betrodd certifikat utfärdare (CA).</span><span class="sxs-lookup"><span data-stu-id="1144c-186">Indicates that when connecting over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="1144c-187">Använd bara den här parametern om fjärrdatorn är betrodd med en annan mekanism, t. ex. när fjärrdatorn är en del av ett nätverk som är fysiskt säkert och isolerat, eller när fjärrdatorn visas som en betrodd värd i en WinRM-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="1144c-187">Use this parameter only when the remote computer is trusted using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated, or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

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

### <span data-ttu-id="1144c-188">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="1144c-188">-SkipCNCheck</span></span>

<span data-ttu-id="1144c-189">Anger att serverns certifikats allmänna namn inte behöver matcha Server namnet för servern.</span><span class="sxs-lookup"><span data-stu-id="1144c-189">Indicates that the certificate common name (CN) of the server does not need to match the hostname of the server.</span></span> <span data-ttu-id="1144c-190">Använd den här parametern endast för fjärråtgärder med betrodda datorer som använder HTTPS-protokollet.</span><span class="sxs-lookup"><span data-stu-id="1144c-190">Use this parameter for remote operations only with trusted computers that use the HTTPS protocol.</span></span>

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

### <span data-ttu-id="1144c-191">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="1144c-191">-SkipRevocationCheck</span></span>

<span data-ttu-id="1144c-192">Anger att återkallnings kontrollen för Server certifikat hoppas över.</span><span class="sxs-lookup"><span data-stu-id="1144c-192">Indicates that the revocation check for server certificates is skipped.</span></span> <span data-ttu-id="1144c-193">Använd endast den här parametern för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="1144c-193">Use this parameter only for trusted computers.</span></span>

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

### <span data-ttu-id="1144c-194">– Värdet</span><span class="sxs-lookup"><span data-stu-id="1144c-194">-UICulture</span></span>

<span data-ttu-id="1144c-195">Anger användar gränssnitts kulturen som ska användas för CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1144c-195">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="1144c-196">Ange värdet för den här parametern med något av följande format:</span><span class="sxs-lookup"><span data-stu-id="1144c-196">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="1144c-197">Ett kultur namn i `<languagecode2>-<country/regioncode2>` formatet "en-US".</span><span class="sxs-lookup"><span data-stu-id="1144c-197">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="1144c-198">En variabel som innehåller ett CultureInfo-objekt.</span><span class="sxs-lookup"><span data-stu-id="1144c-198">A variable that contains a CultureInfo object.</span></span>
- <span data-ttu-id="1144c-199">Ett kommando som hämtar ett CultureInfo-objekt, till exempel `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="1144c-199">A command that gets a CultureInfo object, such as `Get-Culture`.</span></span>

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

### <span data-ttu-id="1144c-200">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="1144c-200">-UseSsl</span></span>

<span data-ttu-id="1144c-201">Anger att SSL ska användas för att upprätta en anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="1144c-201">Indicates that SSL should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="1144c-202">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="1144c-202">By default, SSL is not used.</span></span> <span data-ttu-id="1144c-203">WsMan krypterar allt innehåll som överförs via nätverket, även när du använder HTTP.</span><span class="sxs-lookup"><span data-stu-id="1144c-203">WsMan encrypts all content that is transmitted over the network, even when using HTTP.</span></span>

<span data-ttu-id="1144c-204">Med den här parametern kan du ange ytterligare skydd av HTTPS i stället för HTTP.</span><span class="sxs-lookup"><span data-stu-id="1144c-204">This parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="1144c-205">Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="1144c-205">If SSL is not available on the port used for the connection and you specify this parameter, then the command fails.</span></span>

<span data-ttu-id="1144c-206">Vi rekommenderar att du bara använder den här parametern när parametern **PacketPrivacy** inte anges.</span><span class="sxs-lookup"><span data-stu-id="1144c-206">It is recommended that you use this parameter only when the **PacketPrivacy** parameter is not specified.</span></span>

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

### <span data-ttu-id="1144c-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1144c-207">CommonParameters</span></span>

<span data-ttu-id="1144c-208">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1144c-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1144c-209">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1144c-209">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1144c-210">INDATA</span><span class="sxs-lookup"><span data-stu-id="1144c-210">INPUTS</span></span>

### <span data-ttu-id="1144c-211">Inga</span><span class="sxs-lookup"><span data-stu-id="1144c-211">None</span></span>

<span data-ttu-id="1144c-212">Denna cmdlet accepterar inga inobjekt.</span><span class="sxs-lookup"><span data-stu-id="1144c-212">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="1144c-213">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1144c-213">OUTPUTS</span></span>

### <span data-ttu-id="1144c-214">CIMSessionOption</span><span class="sxs-lookup"><span data-stu-id="1144c-214">CIMSessionOption</span></span>

<span data-ttu-id="1144c-215">Den här cmdleten returnerar ett objekt som innehåller information om CIM-sessionsinformation.</span><span class="sxs-lookup"><span data-stu-id="1144c-215">This cmdlet returns an object that contains CIM session options information.</span></span>

## <span data-ttu-id="1144c-216">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1144c-216">NOTES</span></span>

## <span data-ttu-id="1144c-217">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1144c-217">RELATED LINKS</span></span>

[<span data-ttu-id="1144c-218">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1144c-218">Get-ChildItem</span></span>](../microsoft.powershell.management/get-childitem.md)

[<span data-ttu-id="1144c-219">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="1144c-219">Get-Credential</span></span>](../microsoft.powershell.security/get-credential.md)

[<span data-ttu-id="1144c-220">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="1144c-220">Get-Culture</span></span>](../microsoft.powershell.utility/get-culture.md)

[<span data-ttu-id="1144c-221">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="1144c-221">Get-Item</span></span>](../microsoft.powershell.management/get-item.md)

[<span data-ttu-id="1144c-222">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="1144c-222">New-CimSession</span></span>](New-CimSession.md)

