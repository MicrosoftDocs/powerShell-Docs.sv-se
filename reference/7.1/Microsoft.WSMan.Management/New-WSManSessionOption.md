---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: c0730daaed26fac1e8e8023532f201233fd90013
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266403"
---
# <span data-ttu-id="a0775-103">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="a0775-103">New-WSManSessionOption</span></span>

## <span data-ttu-id="a0775-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a0775-104">SYNOPSIS</span></span>
<span data-ttu-id="a0775-105">Skapar en hash-tabell för sessionsinställningar som ska användas som indataparametrar för WS-Management-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="a0775-105">Creates session option hash table to use as input parameters for WS-Management cmdlets.</span></span>

## <span data-ttu-id="a0775-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0775-106">SYNTAX</span></span>

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## <span data-ttu-id="a0775-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a0775-107">DESCRIPTION</span></span>
<span data-ttu-id="a0775-108">Cmdlet: en **New-WSManSessionOption** skapar en hash-tabell för WSMan-session som kan skickas till WSMan-cmdlet: ar:</span><span class="sxs-lookup"><span data-stu-id="a0775-108">The **New-WSManSessionOption** cmdlet creates a WSMan Session option hash table which can be passed to WSMan cmdlets:</span></span>

- <span data-ttu-id="a0775-109">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0775-109">Get-WSManInstance</span></span>
- <span data-ttu-id="a0775-110">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0775-110">Set-WSManInstance</span></span>
- <span data-ttu-id="a0775-111">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="a0775-111">Invoke-WSManAction</span></span>
- <span data-ttu-id="a0775-112">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a0775-112">Connect-WSMan</span></span>

## <span data-ttu-id="a0775-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a0775-113">EXAMPLES</span></span>

### <span data-ttu-id="a0775-114">Exempel 1: skapa en anslutning som använder anslutnings alternativ</span><span class="sxs-lookup"><span data-stu-id="a0775-114">Example 1: Create a connection that uses connection options</span></span>

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

<span data-ttu-id="a0775-115">I det här exemplet skapas en anslutning till den fjärranslutna Server01-datorn med hjälp av anslutnings alternativen som definieras av **New-WSManSessionOption**.</span><span class="sxs-lookup"><span data-stu-id="a0775-115">This example creates a connection to the remote server01 computer by using the connection options that are defined by **New-WSManSessionOption**.</span></span>

<span data-ttu-id="a0775-116">Det första kommandot använder **New-WSManSessionOption** för att lagra en uppsättning anslutnings inställnings alternativ i variabeln $a.</span><span class="sxs-lookup"><span data-stu-id="a0775-116">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="a0775-117">I det här fallet har sessions alternativen en anslutnings tid på 30 sekunder (30 000 millisekunder).</span><span class="sxs-lookup"><span data-stu-id="a0775-117">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="a0775-118">Det andra kommandot använder parametern *SessionOption* för att skicka de autentiseringsuppgifter som lagras i variabeln $a för att **ansluta-WSMan**.</span><span class="sxs-lookup"><span data-stu-id="a0775-118">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="a0775-119">Sedan ansluter **-WSMan** till den fjärranslutna Server01-datorn med hjälp av de angivna session alternativen.</span><span class="sxs-lookup"><span data-stu-id="a0775-119">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

<span data-ttu-id="a0775-120">**Connect-WSMan** används vanligt vis i kontexten för WSMan-providern för att ansluta till en fjärrdator, i det här fallet Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="a0775-120">**Connect-WSMan** is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="a0775-121">Du kan dock använda cmdleten för att upprätta anslutningar till fjärrdatorer innan du byter till WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="a0775-121">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="a0775-122">Dessa anslutningar visas i listan **dator namn** .</span><span class="sxs-lookup"><span data-stu-id="a0775-122">Those connections appear in the **ComputerName** list.</span></span>

## <span data-ttu-id="a0775-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a0775-123">PARAMETERS</span></span>

### <span data-ttu-id="a0775-124">– Encryption</span><span class="sxs-lookup"><span data-stu-id="a0775-124">-NoEncryption</span></span>
<span data-ttu-id="a0775-125">Anger att anslutningen inte använder kryptering för fjärråtgärder över HTTP.</span><span class="sxs-lookup"><span data-stu-id="a0775-125">Indicates that the connection does not use encryption for remote operations over HTTP.</span></span>

<span data-ttu-id="a0775-126">Okrypterad trafik är som standard inte aktive rad.</span><span class="sxs-lookup"><span data-stu-id="a0775-126">By default, unencrypted traffic is not enabled.</span></span>
<span data-ttu-id="a0775-127">Den måste vara aktive rad i den lokala konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a0775-127">It must be enabled in the local configuration.</span></span>

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

### <span data-ttu-id="a0775-128">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="a0775-128">-OperationTimeout</span></span>
<span data-ttu-id="a0775-129">Anger tids gräns i millisekunder för WS-Management åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a0775-129">Specifies the time-out, in milliseconds, for the WS-Management operation.</span></span>

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

### <span data-ttu-id="a0775-130">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="a0775-130">-ProxyAccessType</span></span>
<span data-ttu-id="a0775-131">Anger den mekanism som proxyservern finns i.</span><span class="sxs-lookup"><span data-stu-id="a0775-131">Specifies the mechanism by which the proxy server is located.</span></span>
<span data-ttu-id="a0775-132">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="a0775-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a0775-133">ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="a0775-133">ProxyIEConfig.</span></span>
<span data-ttu-id="a0775-134">Använd proxy-konfigurationen i Internet Explorer för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="a0775-134">Use the Internet Explorer proxy configuration for the current user.</span></span>
- <span data-ttu-id="a0775-135">ProxyWinHttpConfig.</span><span class="sxs-lookup"><span data-stu-id="a0775-135">ProxyWinHttpConfig.</span></span>
<span data-ttu-id="a0775-136">WSMan-klienten använder proxyinställningarna som kon figurer ATS för WinHTTP med hjälp av ProxyCfg.exe-verktyget.</span><span class="sxs-lookup"><span data-stu-id="a0775-136">The WSMan client uses the proxy settings configured for WinHTTP, using the ProxyCfg.exe utility.</span></span>
- <span data-ttu-id="a0775-137">ProxyAutoDetect.</span><span class="sxs-lookup"><span data-stu-id="a0775-137">ProxyAutoDetect.</span></span>
<span data-ttu-id="a0775-138">Framtvinga automatisk identifiering av en proxyserver.</span><span class="sxs-lookup"><span data-stu-id="a0775-138">Force auto-detection of a proxy server.</span></span>
- <span data-ttu-id="a0775-139">ProxyNoProxyServer.</span><span class="sxs-lookup"><span data-stu-id="a0775-139">ProxyNoProxyServer.</span></span>
<span data-ttu-id="a0775-140">Använd inte en proxyserver.</span><span class="sxs-lookup"><span data-stu-id="a0775-140">Do not use a proxy server.</span></span>
<span data-ttu-id="a0775-141">Matcha alla värdnamn lokalt.</span><span class="sxs-lookup"><span data-stu-id="a0775-141">Resolve all host names locally.</span></span>

<span data-ttu-id="a0775-142">Standardvärdet är ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="a0775-142">The default value is ProxyIEConfig.</span></span>

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

### <span data-ttu-id="a0775-143">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="a0775-143">-ProxyAuthentication</span></span>
<span data-ttu-id="a0775-144">Anger autentiseringsmetoden som ska användas vid proxyservern.</span><span class="sxs-lookup"><span data-stu-id="a0775-144">Specifies the authentication method to use at the proxy.</span></span>
<span data-ttu-id="a0775-145">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="a0775-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a0775-146">Frö.</span><span class="sxs-lookup"><span data-stu-id="a0775-146">Basic.</span></span>
<span data-ttu-id="a0775-147">Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.</span><span class="sxs-lookup"><span data-stu-id="a0775-147">Basic is a scheme in which the user name and password are sent in clear-text to the server or proxy.</span></span>
- <span data-ttu-id="a0775-148">Nedbrytning.</span><span class="sxs-lookup"><span data-stu-id="a0775-148">Digest.</span></span>
<span data-ttu-id="a0775-149">Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.</span><span class="sxs-lookup"><span data-stu-id="a0775-149">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="a0775-150">Fram.</span><span class="sxs-lookup"><span data-stu-id="a0775-150">Negotiate.</span></span>
<span data-ttu-id="a0775-151">Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a0775-151">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine which scheme to use for authentication.</span></span>
<span data-ttu-id="a0775-152">Exempel är Kerberos-protokollet och NTLM.</span><span class="sxs-lookup"><span data-stu-id="a0775-152">Examples are the Kerberos protocol and NTLM.</span></span>

<span data-ttu-id="a0775-153">Standardvärdet är Negotiate.</span><span class="sxs-lookup"><span data-stu-id="a0775-153">The default value is Negotiate.</span></span>

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

### <span data-ttu-id="a0775-154">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a0775-154">-ProxyCredential</span></span>
<span data-ttu-id="a0775-155">Anger ett användar konto som har behörighet att få åtkomst via en mellanliggande webbproxy.</span><span class="sxs-lookup"><span data-stu-id="a0775-155">Specifies a user account that has permission to gain access through an intermediate Web proxy.</span></span>

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

### <span data-ttu-id="a0775-156">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="a0775-156">-SkipCACheck</span></span>
<span data-ttu-id="a0775-157">Anger att när den ansluter via HTTPS, verifierar inte klienten att Server certifikatet är signerat av en betrodd certifikat utfärdare (CA).</span><span class="sxs-lookup"><span data-stu-id="a0775-157">Specifies that, when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>
<span data-ttu-id="a0775-158">Använd bara det här alternativet när fjärrdatorn är betrodd av en annan metod, till exempel om fjärrdatorn är en del av ett nätverk som är fysiskt säkert och isolerat eller om fjärrdatorn visas som en betrodd värd i WS-Management-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a0775-158">Use this option only when the remote computer is trusted by another method, for example, if the remote computer is part of a network that is physically secure and isolated or the remote computer is listed as a trusted host in the WS-Management configuration.</span></span>

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

### <span data-ttu-id="a0775-159">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="a0775-159">-SkipCNCheck</span></span>
<span data-ttu-id="a0775-160">Anger att serverns certifikats allmänna namn inte behöver matcha serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="a0775-160">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="a0775-161">Detta används endast i fjärråtgärder med hjälp av HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0775-161">This is used only in remote operations using HTTPS.</span></span>
<span data-ttu-id="a0775-162">Det här alternativet bör endast användas för betrodda datorer.</span><span class="sxs-lookup"><span data-stu-id="a0775-162">This option should only be used for trusted computers.</span></span>

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

### <span data-ttu-id="a0775-163">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="a0775-163">-SkipRevocationCheck</span></span>
<span data-ttu-id="a0775-164">Anger att anslutningen inte verifierar åter kallelse statusen för Server certifikatet.</span><span class="sxs-lookup"><span data-stu-id="a0775-164">Indicates that the connection does not validate the revocation status on the server certificate.</span></span>

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

### <span data-ttu-id="a0775-165">-SPNPort</span><span class="sxs-lookup"><span data-stu-id="a0775-165">-SPNPort</span></span>
<span data-ttu-id="a0775-166">Anger ett port nummer som ska läggas till i anslutnings tjänstens huvud namn (SPN) för fjärrservern.</span><span class="sxs-lookup"><span data-stu-id="a0775-166">Specifies a port number to append to the connection Service Principal Name (SPN) of the remote server.</span></span>
<span data-ttu-id="a0775-167">Ett SPN används när autentiseringsmekanismen är Kerberos eller förhandla.</span><span class="sxs-lookup"><span data-stu-id="a0775-167">An SPN is used when the authentication mechanism is Kerberos or Negotiate.</span></span>

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

### <span data-ttu-id="a0775-168">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="a0775-168">-UseUTF16</span></span>
<span data-ttu-id="a0775-169">Anger att anslutningen kodar begäran i UTF16-format istället för UTF8-format.</span><span class="sxs-lookup"><span data-stu-id="a0775-169">Indicates that the connection encodes the request in UTF16 format instead of UTF8 format.</span></span>
<span data-ttu-id="a0775-170">Standardvärdet är UTF8-kodning.</span><span class="sxs-lookup"><span data-stu-id="a0775-170">The default is UTF8 encoding.</span></span>

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

### <span data-ttu-id="a0775-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0775-171">CommonParameters</span></span>
<span data-ttu-id="a0775-172">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0775-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0775-173">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a0775-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0775-174">INDATA</span><span class="sxs-lookup"><span data-stu-id="a0775-174">INPUTS</span></span>

## <span data-ttu-id="a0775-175">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a0775-175">OUTPUTS</span></span>

### <span data-ttu-id="a0775-176">SessionOption</span><span class="sxs-lookup"><span data-stu-id="a0775-176">SessionOption</span></span>

## <span data-ttu-id="a0775-177">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a0775-177">NOTES</span></span>

## <span data-ttu-id="a0775-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a0775-178">RELATED LINKS</span></span>

[<span data-ttu-id="a0775-179">Anslut-WSMan</span><span class="sxs-lookup"><span data-stu-id="a0775-179">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="a0775-180">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a0775-180">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="a0775-181">Koppla från-WSMan</span><span class="sxs-lookup"><span data-stu-id="a0775-181">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="a0775-182">Aktivera – WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a0775-182">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="a0775-183">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a0775-183">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="a0775-184">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0775-184">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="a0775-185">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="a0775-185">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="a0775-186">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0775-186">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="a0775-187">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0775-187">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="a0775-188">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0775-188">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="a0775-189">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="a0775-189">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="a0775-190">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="a0775-190">Test-WSMan</span></span>](Test-WSMan.md)

