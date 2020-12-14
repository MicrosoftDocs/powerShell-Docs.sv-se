---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: e7d7f132eb82dc1a709a88cbdef525aa83d867e4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709360"
---
# <span data-ttu-id="8bee1-102">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="8bee1-102">New-WSManSessionOption</span></span>

## <span data-ttu-id="8bee1-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8bee1-103">SYNOPSIS</span></span>
<span data-ttu-id="8bee1-104">Skapar en hash-tabell för sessionsinställningar som ska användas som indataparametrar för WS-Management-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="8bee1-104">Creates session option hash table to use as input parameters for WS-Management cmdlets.</span></span>

## <span data-ttu-id="8bee1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8bee1-105">SYNTAX</span></span>

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## <span data-ttu-id="8bee1-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8bee1-106">DESCRIPTION</span></span>
<span data-ttu-id="8bee1-107">Cmdlet: en **New-WSManSessionOption** skapar en hash-tabell för WSMan-session som kan skickas till WSMan-cmdlet: ar:</span><span class="sxs-lookup"><span data-stu-id="8bee1-107">The **New-WSManSessionOption** cmdlet creates a WSMan Session option hash table which can be passed to WSMan cmdlets:</span></span>

- <span data-ttu-id="8bee1-108">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8bee1-108">Get-WSManInstance</span></span>
- <span data-ttu-id="8bee1-109">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8bee1-109">Set-WSManInstance</span></span>
- <span data-ttu-id="8bee1-110">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="8bee1-110">Invoke-WSManAction</span></span>
- <span data-ttu-id="8bee1-111">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="8bee1-111">Connect-WSMan</span></span>

## <span data-ttu-id="8bee1-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8bee1-112">EXAMPLES</span></span>

### <span data-ttu-id="8bee1-113">Exempel 1: skapa en anslutning som använder anslutnings alternativ</span><span class="sxs-lookup"><span data-stu-id="8bee1-113">Example 1: Create a connection that uses connection options</span></span>

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="8bee1-114">I det här exemplet skapas en anslutning till den fjärranslutna Server01-datorn med hjälp av anslutnings alternativen som definieras av **New-WSManSessionOption**.</span><span class="sxs-lookup"><span data-stu-id="8bee1-114">This example creates a connection to the remote server01 computer by using the connection options that are defined by **New-WSManSessionOption**.</span></span>

<span data-ttu-id="8bee1-115">Det första kommandot använder **New-WSManSessionOption** för att lagra en uppsättning anslutnings inställnings alternativ i variabeln $a.</span><span class="sxs-lookup"><span data-stu-id="8bee1-115">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="8bee1-116">I det här fallet har sessions alternativen en anslutnings tid på 30 sekunder (30 000 millisekunder).</span><span class="sxs-lookup"><span data-stu-id="8bee1-116">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="8bee1-117">Det andra kommandot använder parametern *SessionOption* för att skicka de autentiseringsuppgifter som lagras i variabeln $a för att **ansluta-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="8bee1-117">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="8bee1-118">Sedan ansluter **-WSMan** till den fjärranslutna Server01-datorn med hjälp av de angivna session alternativen.</span><span class="sxs-lookup"><span data-stu-id="8bee1-118">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

<span data-ttu-id="8bee1-119">**Connect-WSMan** används vanligt vis i kontexten för WSMan-providern för att ansluta till en fjärrdator, i det här fallet Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="8bee1-119">**Connect-WSMan** is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="8bee1-120">Du kan dock använda cmdleten för att upprätta anslutningar till fjärrdatorer innan du byter till WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="8bee1-120">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="8bee1-121">Dessa anslutningar visas i listan **dator namn** .</span><span class="sxs-lookup"><span data-stu-id="8bee1-121">Those connections appear in the **ComputerName** list.</span></span>

## <span data-ttu-id="8bee1-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8bee1-122">PARAMETERS</span></span>

### <span data-ttu-id="8bee1-123">– Encryption</span><span class="sxs-lookup"><span data-stu-id="8bee1-123">-NoEncryption</span></span>
<span data-ttu-id="8bee1-124">Anger att anslutningen inte använder kryptering för fjärråtgärder över HTTP.</span><span class="sxs-lookup"><span data-stu-id="8bee1-124">Indicates that the connection does not use encryption for remote operations over HTTP.</span></span>

<span data-ttu-id="8bee1-125">Okrypterad trafik är som standard inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="8bee1-125">By default, unencrypted traffic is not enabled.</span></span>
<span data-ttu-id="8bee1-126">Den måste vara aktive rad i den lokala konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8bee1-126">It must be enabled in the local configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-127">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="8bee1-127">-OperationTimeout</span></span>
<span data-ttu-id="8bee1-128">Anger tids gräns i millisekunder för WS-Management åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8bee1-128">Specifies the time-out, in milliseconds, for the WS-Management operation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-129">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="8bee1-129">-ProxyAccessType</span></span>
<span data-ttu-id="8bee1-130">Anger den mekanism som proxyservern finns i.</span><span class="sxs-lookup"><span data-stu-id="8bee1-130">Specifies the mechanism by which the proxy server is located.</span></span>
<span data-ttu-id="8bee1-131">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="8bee1-131">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8bee1-132">ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="8bee1-132">ProxyIEConfig.</span></span>
<span data-ttu-id="8bee1-133">Använd proxy-konfigurationen i Internet Explorer för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="8bee1-133">Use the Internet Explorer proxy configuration for the current user.</span></span>
- <span data-ttu-id="8bee1-134">ProxyWinHttpConfig.</span><span class="sxs-lookup"><span data-stu-id="8bee1-134">ProxyWinHttpConfig.</span></span>
<span data-ttu-id="8bee1-135">WSMan-klienten använder proxyinställningarna som kon figurer ATS för WinHTTP med hjälp av ProxyCfg.exe-verktyget.</span><span class="sxs-lookup"><span data-stu-id="8bee1-135">The WSMan client uses the proxy settings configured for WinHTTP, using the ProxyCfg.exe utility.</span></span>
- <span data-ttu-id="8bee1-136">ProxyAutoDetect.</span><span class="sxs-lookup"><span data-stu-id="8bee1-136">ProxyAutoDetect.</span></span>
<span data-ttu-id="8bee1-137">Framtvinga automatisk identifiering av en proxyserver.</span><span class="sxs-lookup"><span data-stu-id="8bee1-137">Force auto-detection of a proxy server.</span></span>
- <span data-ttu-id="8bee1-138">ProxyNoProxyServer.</span><span class="sxs-lookup"><span data-stu-id="8bee1-138">ProxyNoProxyServer.</span></span>
<span data-ttu-id="8bee1-139">Använd inte en proxyserver.</span><span class="sxs-lookup"><span data-stu-id="8bee1-139">Do not use a proxy server.</span></span>
<span data-ttu-id="8bee1-140">Matcha alla värdnamn lokalt.</span><span class="sxs-lookup"><span data-stu-id="8bee1-140">Resolve all host names locally.</span></span>

<span data-ttu-id="8bee1-141">Standardvärdet är ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="8bee1-141">The default value is ProxyIEConfig.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-142">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="8bee1-142">-ProxyAuthentication</span></span>
<span data-ttu-id="8bee1-143">Anger autentiseringsmetoden som ska användas vid proxyservern.</span><span class="sxs-lookup"><span data-stu-id="8bee1-143">Specifies the authentication method to use at the proxy.</span></span>
<span data-ttu-id="8bee1-144">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="8bee1-144">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8bee1-145">Frö.</span><span class="sxs-lookup"><span data-stu-id="8bee1-145">Basic.</span></span>
<span data-ttu-id="8bee1-146">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="8bee1-146">Basic is a scheme in which the user name and password are sent in clear-text to the server or proxy.</span></span>
- <span data-ttu-id="8bee1-147">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="8bee1-147">Digest.</span></span>
<span data-ttu-id="8bee1-148">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="8bee1-148">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="8bee1-149">Fram.</span><span class="sxs-lookup"><span data-stu-id="8bee1-149">Negotiate.</span></span>
<span data-ttu-id="8bee1-150">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8bee1-150">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine which scheme to use for authentication.</span></span>
<span data-ttu-id="8bee1-151">Exempel är Kerberos-protokollet och NTLM.</span><span class="sxs-lookup"><span data-stu-id="8bee1-151">Examples are the Kerberos protocol and NTLM.</span></span>

<span data-ttu-id="8bee1-152">Standardvärdet är Negotiate.</span><span class="sxs-lookup"><span data-stu-id="8bee1-152">The default value is Negotiate.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="8bee1-153">-ProxyCredential</span></span>
<span data-ttu-id="8bee1-154">Anger ett användar konto som har behörighet att få åtkomst via en mellanliggande webbproxy.</span><span class="sxs-lookup"><span data-stu-id="8bee1-154">Specifies a user account that has permission to gain access through an intermediate Web proxy.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-155">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="8bee1-155">-SkipCACheck</span></span>
<span data-ttu-id="8bee1-156">Anger att när den ansluter via HTTPS, verifierar inte klienten att Server certifikatet är signerat av en betrodd certifikat utfärdare (CA).</span><span class="sxs-lookup"><span data-stu-id="8bee1-156">Specifies that, when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>
<span data-ttu-id="8bee1-157">Använd bara det här alternativet när fjärrdatorn är betrodd av en annan metod, till exempel om fjärrdatorn är en del av ett nätverk som är fysiskt säkert och isolerat eller om fjärrdatorn visas som en betrodd värd i WS-Management-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8bee1-157">Use this option only when the remote computer is trusted by another method, for example, if the remote computer is part of a network that is physically secure and isolated or the remote computer is listed as a trusted host in the WS-Management configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-158">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="8bee1-158">-SkipCNCheck</span></span>
<span data-ttu-id="8bee1-159">Anger att serverns certifikats allmänna namn inte behöver matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="8bee1-159">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="8bee1-160">Detta används endast i fjärråtgärder med hjälp av HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8bee1-160">This is used only in remote operations using HTTPS.</span></span>
<span data-ttu-id="8bee1-161">Det här alternativet bör endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="8bee1-161">This option should only be used for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-162">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="8bee1-162">-SkipRevocationCheck</span></span>
<span data-ttu-id="8bee1-163">Anger att anslutningen inte verifierar åter kallelse statusen för Server certifikatet.</span><span class="sxs-lookup"><span data-stu-id="8bee1-163">Indicates that the connection does not validate the revocation status on the server certificate.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-164">-SPNPort</span><span class="sxs-lookup"><span data-stu-id="8bee1-164">-SPNPort</span></span>
<span data-ttu-id="8bee1-165">Anger ett port nummer som ska läggas till i anslutnings tjänstens huvud namn (SPN) för fjärrservern.</span><span class="sxs-lookup"><span data-stu-id="8bee1-165">Specifies a port number to append to the connection Service Principal Name (SPN) of the remote server.</span></span>
<span data-ttu-id="8bee1-166">Ett SPN används när autentiseringsmekanismen är Kerberos eller förhandla.</span><span class="sxs-lookup"><span data-stu-id="8bee1-166">An SPN is used when the authentication mechanism is Kerberos or Negotiate.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-167">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="8bee1-167">-UseUTF16</span></span>
<span data-ttu-id="8bee1-168">Anger att anslutningen kodar begäran i UTF16-format istället för UTF8-format.</span><span class="sxs-lookup"><span data-stu-id="8bee1-168">Indicates that the connection encodes the request in UTF16 format instead of UTF8 format.</span></span>
<span data-ttu-id="8bee1-169">Standardvärdet är UTF8-kodning.</span><span class="sxs-lookup"><span data-stu-id="8bee1-169">The default is UTF8 encoding.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8bee1-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8bee1-170">CommonParameters</span></span>
<span data-ttu-id="8bee1-171">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8bee1-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8bee1-172">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8bee1-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8bee1-173">INDATA</span><span class="sxs-lookup"><span data-stu-id="8bee1-173">INPUTS</span></span>

## <span data-ttu-id="8bee1-174">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8bee1-174">OUTPUTS</span></span>

### <span data-ttu-id="8bee1-175">SessionOption</span><span class="sxs-lookup"><span data-stu-id="8bee1-175">SessionOption</span></span>

## <span data-ttu-id="8bee1-176">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8bee1-176">NOTES</span></span>

## <span data-ttu-id="8bee1-177">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8bee1-177">RELATED LINKS</span></span>

[<span data-ttu-id="8bee1-178">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="8bee1-178">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="8bee1-179">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8bee1-179">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="8bee1-180">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="8bee1-180">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="8bee1-181">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8bee1-181">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="8bee1-182">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="8bee1-182">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="8bee1-183">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8bee1-183">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="8bee1-184">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="8bee1-184">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="8bee1-185">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8bee1-185">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="8bee1-186">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8bee1-186">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="8bee1-187">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="8bee1-187">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="8bee1-188">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="8bee1-188">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="8bee1-189">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="8bee1-189">Test-WSMan</span></span>](Test-WSMan.md)

