---
ms.topic: reference
keywords: PowerShell cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094236"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="f7bea-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f7bea-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="f7bea-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f7bea-104">SYNOPSIS</span></span>

<span data-ttu-id="f7bea-105">Lägger till en ny auktoriseringsregel till Windows PowerShell® Web Access auktoriseringsregeluppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f7bea-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7bea-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7bea-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="f7bea-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="f7bea-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="f7bea-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="f7bea-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="f7bea-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="f7bea-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="f7bea-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="f7bea-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="f7bea-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f7bea-111">DESCRIPTION</span></span>

<span data-ttu-id="f7bea-112">Den **Add-PswaAuthorizationRule** cmdlet lägger till en ny auktoriseringsregel till Windows PowerShell® Web Access auktoriseringsregeluppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f7bea-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="f7bea-113">Du måste ange användare, datorer och Windows PowerShell-slutpunkter för den här regeln.</span><span class="sxs-lookup"><span data-stu-id="f7bea-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="f7bea-114">Du kan ange både användare och datorer genom att enskilda användarkonton och datornamn, eller genom att ange grupper.</span><span class="sxs-lookup"><span data-stu-id="f7bea-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="f7bea-115">För en dator som är ansluten till en Active Directory-domän, använder cmdlet: en säkerhetsidentifierare (SID) för datorn för att skapa regeln.</span><span class="sxs-lookup"><span data-stu-id="f7bea-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="f7bea-116">På så sätt kan du använda ett kort namn, ett fullständigt kvalificerat domännamn (FQDN) eller en IP-adress för den **datornamn** på sidan logga in.</span><span class="sxs-lookup"><span data-stu-id="f7bea-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="f7bea-117">Cmdleten skapar regeln med namnet på datorn som tillhandahålls av administratören för en dator som inte är ansluten till en Active Directory-domän.</span><span class="sxs-lookup"><span data-stu-id="f7bea-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="f7bea-118">För att ansluta till den här datorn, måste användaren ange datornamnet exakt som det visas i regeln.</span><span class="sxs-lookup"><span data-stu-id="f7bea-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="f7bea-119">Om det finns flera datorer med samma namn i nätverket, kan kort namn matcha till flera datorer.</span><span class="sxs-lookup"><span data-stu-id="f7bea-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="f7bea-120">Detta kan leda till tvetydighet när en anslutning upprättas.</span><span class="sxs-lookup"><span data-stu-id="f7bea-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="f7bea-121">Exempel: om det finns en regel för den arbetsgruppsdator med namnet ”*Server1*” och en ny dator med namnet *server1.contoso.com* är ansluten till nätverket med hjälp av auktoriseringsreglerna lyckas och Windows PowerShell-webbåtkomst försöker upprätta en anslutning till datorn med namnet ”*Server1*”.</span><span class="sxs-lookup"><span data-stu-id="f7bea-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="f7bea-122">Det är inte säkert att anslutningen har upprättats med den angivna arbetsgrupp-datorn. försöket kan göras på arbetsgruppen eller domän datorn med namnet ”*Server1*”.</span><span class="sxs-lookup"><span data-stu-id="f7bea-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="f7bea-123">Du rekommenderas att du använder det fullständiga Domännamnet för måldatorn när det är möjligt att skapa en auktoriseringsregel för att minska tvetydighet.</span><span class="sxs-lookup"><span data-stu-id="f7bea-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="f7bea-124">Auktoriseringsreglerna utvärdera den primära logga in autentiseringsuppgifterna för Windows PowerShell Web Access-användare, inte de alternativa autentiseringsuppgifterna (den andra uppsättningen av autentiseringsuppgifter finns i den **valfria anslutningsinställningar** delen av den på inloggningssidan).</span><span class="sxs-lookup"><span data-stu-id="f7bea-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="f7bea-125">Ett exempel på detta finns i exemplet 6.</span><span class="sxs-lookup"><span data-stu-id="f7bea-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="f7bea-126">Parametrar</span><span class="sxs-lookup"><span data-stu-id="f7bea-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="f7bea-127">-ComputerGroupName \<sträng\></span><span class="sxs-lookup"><span data-stu-id="f7bea-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="f7bea-128">Anger namnet på en datorgrupp i Active Directory Domain Services (AD DS) eller lokala grupper som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="f7bea-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="f7bea-129">Alias</span><span class="sxs-lookup"><span data-stu-id="f7bea-129">Aliases</span></span>                              | <span data-ttu-id="f7bea-130">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-130">none</span></span>                                 |
| <span data-ttu-id="f7bea-131">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="f7bea-131">Required?</span></span>                            | <span data-ttu-id="f7bea-132">SANT</span><span class="sxs-lookup"><span data-stu-id="f7bea-132">true</span></span>                                 |
| <span data-ttu-id="f7bea-133">Placering?</span><span class="sxs-lookup"><span data-stu-id="f7bea-133">Position?</span></span>                            | <span data-ttu-id="f7bea-134">med namnet</span><span class="sxs-lookup"><span data-stu-id="f7bea-134">named</span></span>                                |
| <span data-ttu-id="f7bea-135">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="f7bea-135">Default Value</span></span>                        | <span data-ttu-id="f7bea-136">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-136">none</span></span>                                 |
| <span data-ttu-id="f7bea-137">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="f7bea-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f7bea-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="f7bea-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="f7bea-139">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f7bea-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f7bea-140">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-140">false</span></span>                                |

### <a name="-computername-string"></a><span data-ttu-id="f7bea-141">-ComputerName \<sträng\></span><span class="sxs-lookup"><span data-stu-id="f7bea-141">-ComputerName \<String\></span></span>

<span data-ttu-id="f7bea-142">Anger namnet på datorn som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="f7bea-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="f7bea-143">Alias</span><span class="sxs-lookup"><span data-stu-id="f7bea-143">Aliases</span></span>                              | <span data-ttu-id="f7bea-144">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-144">none</span></span>                                 |
| <span data-ttu-id="f7bea-145">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="f7bea-145">Required?</span></span>                            | <span data-ttu-id="f7bea-146">SANT</span><span class="sxs-lookup"><span data-stu-id="f7bea-146">true</span></span>                                 |
| <span data-ttu-id="f7bea-147">Placering?</span><span class="sxs-lookup"><span data-stu-id="f7bea-147">Position?</span></span>                            | <span data-ttu-id="f7bea-148">med namnet</span><span class="sxs-lookup"><span data-stu-id="f7bea-148">named</span></span>                                |
| <span data-ttu-id="f7bea-149">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="f7bea-149">Default Value</span></span>                        | <span data-ttu-id="f7bea-150">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-150">none</span></span>                                 |
| <span data-ttu-id="f7bea-151">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="f7bea-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f7bea-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="f7bea-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="f7bea-153">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f7bea-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f7bea-154">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-154">false</span></span>                                |

### <a name="-configurationname-string"></a><span data-ttu-id="f7bea-155">-ConfigurationName \<sträng\></span><span class="sxs-lookup"><span data-stu-id="f7bea-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="f7bea-156">Anger namnet på sessionskonfigurationen för Windows PowerShell, även kallat körningsutrymme, som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="f7bea-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="f7bea-157">Alias</span><span class="sxs-lookup"><span data-stu-id="f7bea-157">Aliases</span></span>                              | <span data-ttu-id="f7bea-158">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-158">none</span></span>                                 |
| <span data-ttu-id="f7bea-159">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="f7bea-159">Required?</span></span>                            | <span data-ttu-id="f7bea-160">SANT</span><span class="sxs-lookup"><span data-stu-id="f7bea-160">true</span></span>                                 |
| <span data-ttu-id="f7bea-161">Placering?</span><span class="sxs-lookup"><span data-stu-id="f7bea-161">Position?</span></span>                            | <span data-ttu-id="f7bea-162">med namnet</span><span class="sxs-lookup"><span data-stu-id="f7bea-162">named</span></span>                                |
| <span data-ttu-id="f7bea-163">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="f7bea-163">Default Value</span></span>                        | <span data-ttu-id="f7bea-164">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-164">none</span></span>                                 |
| <span data-ttu-id="f7bea-165">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="f7bea-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f7bea-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="f7bea-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="f7bea-167">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f7bea-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f7bea-168">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-168">false</span></span>                                |

### <a name="-credential--pscredential"></a><span data-ttu-id="f7bea-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="f7bea-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="f7bea-170">Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att ändra regler för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="f7bea-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="f7bea-171">Om du inte lägga till den här parametern använder cmdlet: en för tillfället inloggade användarkontot.</span><span class="sxs-lookup"><span data-stu-id="f7bea-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="f7bea-172">Att hämta en **PSCredential** -objektet, vilket krävs för att lägga till auktoriseringsregler via fjärranslutning genom att köra den [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7bea-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="f7bea-173">Alias</span><span class="sxs-lookup"><span data-stu-id="f7bea-173">Aliases</span></span>                              | <span data-ttu-id="f7bea-174">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-174">none</span></span>                                 |
| <span data-ttu-id="f7bea-175">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="f7bea-175">Required?</span></span>                            | <span data-ttu-id="f7bea-176">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-176">false</span></span>                                |
| <span data-ttu-id="f7bea-177">Placering?</span><span class="sxs-lookup"><span data-stu-id="f7bea-177">Position?</span></span>                            | <span data-ttu-id="f7bea-178">med namnet</span><span class="sxs-lookup"><span data-stu-id="f7bea-178">named</span></span>                                |
| <span data-ttu-id="f7bea-179">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="f7bea-179">Default Value</span></span>                        | <span data-ttu-id="f7bea-180">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-180">none</span></span>                                 |
| <span data-ttu-id="f7bea-181">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="f7bea-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f7bea-182">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-182">false</span></span>                                |
| <span data-ttu-id="f7bea-183">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f7bea-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f7bea-184">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="f7bea-185">-Force</span><span class="sxs-lookup"><span data-stu-id="f7bea-185">-Force</span></span>

<span data-ttu-id="f7bea-186">Tvingar kommandot att köras utan att användaren ombeds bekräfta. \\</span><span class="sxs-lookup"><span data-stu-id="f7bea-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="f7bea-187">Dessutom kan uppmanas den också att bekräfta när du anger ett enkelt eller korta datornamn (till exempel ett namn som inte är ett domännamn eller inte är fullständigt kvalificerad).</span><span class="sxs-lookup"><span data-stu-id="f7bea-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="f7bea-188">Bekräftelse begärs av säkerhetsskäl så att du kan använda enkla namnet för att lägga till en dator endast om datorn är i en arbetsgrupp.</span><span class="sxs-lookup"><span data-stu-id="f7bea-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="f7bea-189">Alias</span><span class="sxs-lookup"><span data-stu-id="f7bea-189">Aliases</span></span>                              | <span data-ttu-id="f7bea-190">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-190">none</span></span>                                 |
| <span data-ttu-id="f7bea-191">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="f7bea-191">Required?</span></span>                            | <span data-ttu-id="f7bea-192">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-192">false</span></span>                                |
| <span data-ttu-id="f7bea-193">Placering?</span><span class="sxs-lookup"><span data-stu-id="f7bea-193">Position?</span></span>                            | <span data-ttu-id="f7bea-194">med namnet</span><span class="sxs-lookup"><span data-stu-id="f7bea-194">named</span></span>                                |
| <span data-ttu-id="f7bea-195">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="f7bea-195">Default Value</span></span>                        | <span data-ttu-id="f7bea-196">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-196">none</span></span>                                 |
| <span data-ttu-id="f7bea-197">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="f7bea-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f7bea-198">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-198">false</span></span>                                |
| <span data-ttu-id="f7bea-199">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f7bea-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f7bea-200">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="f7bea-201">-RuleName \<sträng\></span><span class="sxs-lookup"><span data-stu-id="f7bea-201">-RuleName \<String\></span></span>

<span data-ttu-id="f7bea-202">Anger det egna namnet för den här regeln.</span><span class="sxs-lookup"><span data-stu-id="f7bea-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="f7bea-203">Alias</span><span class="sxs-lookup"><span data-stu-id="f7bea-203">Aliases</span></span>                              | <span data-ttu-id="f7bea-204">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-204">none</span></span>                                 |
| <span data-ttu-id="f7bea-205">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="f7bea-205">Required?</span></span>                            | <span data-ttu-id="f7bea-206">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-206">false</span></span>                                |
| <span data-ttu-id="f7bea-207">Placering?</span><span class="sxs-lookup"><span data-stu-id="f7bea-207">Position?</span></span>                            | <span data-ttu-id="f7bea-208">med namnet</span><span class="sxs-lookup"><span data-stu-id="f7bea-208">named</span></span>                                |
| <span data-ttu-id="f7bea-209">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="f7bea-209">Default Value</span></span>                        | <span data-ttu-id="f7bea-210">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-210">none</span></span>                                 |
| <span data-ttu-id="f7bea-211">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="f7bea-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f7bea-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="f7bea-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="f7bea-213">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f7bea-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f7bea-214">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="f7bea-215">-UserGroupName \<sträng\[\]\></span><span class="sxs-lookup"><span data-stu-id="f7bea-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="f7bea-216">Anger namnet på en eller flera användargrupper i AD DS eller lokala grupper som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="f7bea-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="f7bea-217">Alias</span><span class="sxs-lookup"><span data-stu-id="f7bea-217">Aliases</span></span>                              | <span data-ttu-id="f7bea-218">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-218">none</span></span>                                 |
| <span data-ttu-id="f7bea-219">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="f7bea-219">Required?</span></span>                            | <span data-ttu-id="f7bea-220">SANT</span><span class="sxs-lookup"><span data-stu-id="f7bea-220">true</span></span>                                 |
| <span data-ttu-id="f7bea-221">Placering?</span><span class="sxs-lookup"><span data-stu-id="f7bea-221">Position?</span></span>                            | <span data-ttu-id="f7bea-222">med namnet</span><span class="sxs-lookup"><span data-stu-id="f7bea-222">named</span></span>                                |
| <span data-ttu-id="f7bea-223">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="f7bea-223">Default Value</span></span>                        | <span data-ttu-id="f7bea-224">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-224">none</span></span>                                 |
| <span data-ttu-id="f7bea-225">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="f7bea-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f7bea-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="f7bea-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="f7bea-227">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f7bea-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f7bea-228">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="f7bea-229">-UserName \<sträng\[\]\></span><span class="sxs-lookup"><span data-stu-id="f7bea-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="f7bea-230">Anger en eller flera användare som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="f7bea-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="f7bea-231">Användarnamnet kan vara ett lokalt användarkonto på gateway-datorn eller en användare i AD DS.</span><span class="sxs-lookup"><span data-stu-id="f7bea-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="f7bea-232">Formatet är `domain\user` eller `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="f7bea-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="f7bea-233">Alias</span><span class="sxs-lookup"><span data-stu-id="f7bea-233">Aliases</span></span>                              | <span data-ttu-id="f7bea-234">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-234">none</span></span>                                 |
| <span data-ttu-id="f7bea-235">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="f7bea-235">Required?</span></span>                            | <span data-ttu-id="f7bea-236">SANT</span><span class="sxs-lookup"><span data-stu-id="f7bea-236">true</span></span>                                 |
| <span data-ttu-id="f7bea-237">Placering?</span><span class="sxs-lookup"><span data-stu-id="f7bea-237">Position?</span></span>                            | <span data-ttu-id="f7bea-238">1</span><span class="sxs-lookup"><span data-stu-id="f7bea-238">1</span></span>                                    |
| <span data-ttu-id="f7bea-239">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="f7bea-239">Default Value</span></span>                        | <span data-ttu-id="f7bea-240">inget</span><span class="sxs-lookup"><span data-stu-id="f7bea-240">none</span></span>                                 |
| <span data-ttu-id="f7bea-241">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="f7bea-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f7bea-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="f7bea-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="f7bea-243">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f7bea-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f7bea-244">falskt</span><span class="sxs-lookup"><span data-stu-id="f7bea-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="f7bea-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="f7bea-245">\<CommonParameters\></span></span>

<span data-ttu-id="f7bea-246">Denna cmdlet har stöd för parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="f7bea-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="f7bea-247">Mer information finns i [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="f7bea-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="f7bea-248">INDATA</span><span class="sxs-lookup"><span data-stu-id="f7bea-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="f7bea-249">Sträng</span><span class="sxs-lookup"><span data-stu-id="f7bea-249">String</span></span>

<span data-ttu-id="f7bea-250">Denna cmdlet accepterar en sträng eller en matris med strängar som indata.</span><span class="sxs-lookup"><span data-stu-id="f7bea-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="f7bea-251">Sträng\[\]</span><span class="sxs-lookup"><span data-stu-id="f7bea-251">String\[\]</span></span>

<span data-ttu-id="f7bea-252">Denna cmdlet accepterar en sträng eller en matris med strängar som indata.</span><span class="sxs-lookup"><span data-stu-id="f7bea-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="f7bea-253">Utdata:</span><span class="sxs-lookup"><span data-stu-id="f7bea-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="f7bea-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f7bea-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="f7bea-255">Denna cmdlet returnerar den ett auktorisering regelobjekt.</span><span class="sxs-lookup"><span data-stu-id="f7bea-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="f7bea-256">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f7bea-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="f7bea-257">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="f7bea-257">EXAMPLE 1</span></span>

<span data-ttu-id="f7bea-258">Det här exemplet tilldelar åtkomst till sessionskonfigurationen _PSWAEndpoint_, ett begränsat körningsutrymme på _srv2_ för användare i den _SMAdmins_ grupp.</span><span class="sxs-lookup"><span data-stu-id="f7bea-258">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="f7bea-259">Datornamnet måste vara ett fullständigt kvalificerat domännamn (FQDN).</span><span class="sxs-lookup"><span data-stu-id="f7bea-259">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="f7bea-260">Administratörer definiera ett begränsat sessionskonfiguration eller körningsutrymmen, vilket är ett begränsat antal cmdletar och uppgifter som slutanvändarna kan köras.</span><span class="sxs-lookup"><span data-stu-id="f7bea-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="f7bea-261">Definiera ett begränsat körningsutrymme kan förhindra användare från att komma åt andra datorer som inte i den tillåtna Windows PowerShell® körningsutrymmen, vilket ger en säkrare anslutning.</span><span class="sxs-lookup"><span data-stu-id="f7bea-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="f7bea-262">Mer information om sessionskonfigurationer finns i [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) eller [installera och använda Windows PowerShell-webbåtkomst](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="f7bea-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="f7bea-263">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="f7bea-263">EXAMPLE 2</span></span>

<span data-ttu-id="f7bea-264">Det här exemplet tilldelar åtkomst till Windows PowerShell-session standardkonfigurationen `Microsoft.PowerShell`på *srv2* för användare i de användare som heter `contoso\user1`, `contoso\user2`, och `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="f7bea-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="f7bea-265">Denna cmdlet skapar tre regler (1 per person).</span><span class="sxs-lookup"><span data-stu-id="f7bea-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="f7bea-266">EXEMPEL 3</span><span class="sxs-lookup"><span data-stu-id="f7bea-266">EXAMPLE 3</span></span>

<span data-ttu-id="f7bea-267">Det här exemplet illustrerar hur du kan ange värden för användaren via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="f7bea-267">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="f7bea-268">EXEMPEL 4</span><span class="sxs-lookup"><span data-stu-id="f7bea-268">EXAMPLE 4</span></span>

<span data-ttu-id="f7bea-269">Det här exemplet illustrerar hur alla parametrar tar värden från pipeline efter egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="f7bea-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="f7bea-270">EXEMPEL 5</span><span class="sxs-lookup"><span data-stu-id="f7bea-270">EXAMPLE 5</span></span>

<span data-ttu-id="f7bea-271">Det här exemplet lägger till en regel som tillåter lokal användare med namnet `PswaServer\ChrisLocal` åtkomst till servern med namnet **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="f7bea-271">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="f7bea-272">Det här exemplet illustrerar ett scenario där gatewayen är i en arbetsgrupp och måldatorn finns i en domän.</span><span class="sxs-lookup"><span data-stu-id="f7bea-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="f7bea-273">Regeln gäller för lokala användare på gatewayen.</span><span class="sxs-lookup"><span data-stu-id="f7bea-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="f7bea-274">I Windows PowerShell-webbåtkomst på inloggningssidan, för att kunna autentisera användaren måste ange en annan uppsättning autentiseringsuppgifter i den **valfria anslutningsinställningar** området.</span><span class="sxs-lookup"><span data-stu-id="f7bea-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="f7bea-275">Gateway-servern använder denna ytterligare uppsättning autentiseringsuppgifter för att autentisera användaren på måldatorn, en server med namnet *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="f7bea-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="f7bea-276">EXEMPEL 6</span><span class="sxs-lookup"><span data-stu-id="f7bea-276">EXAMPLE 6</span></span>

<span data-ttu-id="f7bea-277">Det här exemplet tillåter alla användare åtkomst till alla slutpunkter på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="f7bea-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="f7bea-278">Detta inaktiverar i stort sett regler.</span><span class="sxs-lookup"><span data-stu-id="f7bea-278">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="f7bea-279">Användning av den `*` jokertecknet rekommenderas inte för distributioner av känsliga och bör endast för testmiljöer eller används i distributioner där säkerheten minskas.</span><span class="sxs-lookup"><span data-stu-id="f7bea-279">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="f7bea-280">Se även</span><span class="sxs-lookup"><span data-stu-id="f7bea-280">See Also</span></span>

<span data-ttu-id="f7bea-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="f7bea-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="f7bea-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="f7bea-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="f7bea-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="f7bea-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="f7bea-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="f7bea-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="f7bea-285">Lägg till medlem</span><span class="sxs-lookup"><span data-stu-id="f7bea-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="f7bea-286">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="f7bea-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="f7bea-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="f7bea-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)