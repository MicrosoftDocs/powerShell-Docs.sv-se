---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: "Lägg till pswaauthorizationrule"
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 196797215a678e6f674592dc6b289816aced3c01
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="7d9d2-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="7d9d2-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="7d9d2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="7d9d2-104">SYNOPSIS</span></span>

<span data-ttu-id="7d9d2-105">Lägger till en ny auktoriseringsregel regeluppsättningen för auktorisering av Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d9d2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d9d2-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="7d9d2-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="7d9d2-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="7d9d2-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="7d9d2-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="7d9d2-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="7d9d2-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="7d9d2-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="7d9d2-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="7d9d2-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7d9d2-111">DESCRIPTION</span></span>

<span data-ttu-id="7d9d2-112">Den **Add-PswaAuthorizationRule** cmdlet lägger till en ny auktoriseringsregel till Windows PowerShell® Web Access auktoriseringsregeluppsättningen.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="7d9d2-113">Du måste ange användare, datorer och Windows PowerShell-slutpunkter för den här regeln.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="7d9d2-114">Du kan ange både användare och datorer genom enskilda användarkonton och datornamn eller genom att ange grupper.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="7d9d2-115">För en dator som är ansluten till en Active Directory-domän, använder cmdlet säkerhetsidentifierare (SID) för datorn för att skapa regeln.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="7d9d2-116">Detta gör att du kan använda ett kort namn, ett fullständigt kvalificerat domännamn (FQDN) eller en IP-adress för den **datornamn** på sidan logga in.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="7d9d2-117">För en dator som inte är ansluten till en Active Directory-domän, skapar cmdleten regeln med hjälp av namnet på datorn som tillhandahålls av administratören.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="7d9d2-118">Om du vill ansluta till den här datorn, måste användaren ange datornamnet exakt som det visas i regeln.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="7d9d2-119">Om det finns flera datorer med samma namn i nätverket kan lösas kort namn till mer än en dator.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="7d9d2-120">Detta kan leda till tvetydighet när en anslutning upprättas.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="7d9d2-121">Till exempel om det finns en regel för arbetsgruppsdator med namnet ”*Server1*” och en ny dator med namnet *server1.contoso.com* är ansluten till nätverket med hjälp av auktoriseringsregler lyckas och Windows PowerShell Web Access försöker upprätta en anslutning till datorn med namnet ”*Server1*”.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="7d9d2-122">Det är inte säkert att ansluta till den angivna arbetsgrupp-datorn. Försök kan göras på arbetsgruppen eller domän datorn med namnet ”*Server1*”.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="7d9d2-123">Det rekommenderas att du använder det fullständiga Domännamnet för måldatorn när det är möjligt att skapa en auktoriseringsregel för att undvika tvetydighet.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="7d9d2-124">Auktoriseringsregler utvärdera primära inloggning inloggningsuppgifterna för Windows PowerShell Web Access-användare, inte de alternativa autentiseringsuppgifterna (den andra uppsättningen av autentiseringsuppgifter finns i den **valfria anslutningsinställningar** avsnitt i den inloggningssidan).</span><span class="sxs-lookup"><span data-stu-id="7d9d2-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="7d9d2-125">Ett exempel på detta finns i exempel 6.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="7d9d2-126">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7d9d2-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="7d9d2-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9d2-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="7d9d2-128">Anger namnet på en datorgrupp i Active Directory Domain Services (AD DS) eller lokala grupper som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="7d9d2-129">Alias</span><span class="sxs-lookup"><span data-stu-id="7d9d2-129">Aliases</span></span>                              | <span data-ttu-id="7d9d2-130">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-130">none</span></span>                                 |
| <span data-ttu-id="7d9d2-131">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-131">Required?</span></span>                            | <span data-ttu-id="7d9d2-132">true</span><span class="sxs-lookup"><span data-stu-id="7d9d2-132">true</span></span>                                 |
| <span data-ttu-id="7d9d2-133">Placering?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-133">Position?</span></span>                            | <span data-ttu-id="7d9d2-134">Med namnet</span><span class="sxs-lookup"><span data-stu-id="7d9d2-134">named</span></span>                                |
| <span data-ttu-id="7d9d2-135">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7d9d2-135">Default Value</span></span>                        | <span data-ttu-id="7d9d2-136">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-136">none</span></span>                                 |
| <span data-ttu-id="7d9d2-137">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="7d9d2-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="7d9d2-139">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="7d9d2-140">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="7d9d2-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9d2-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="7d9d2-142">Anger namnet på datorn som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="7d9d2-143">Alias</span><span class="sxs-lookup"><span data-stu-id="7d9d2-143">Aliases</span></span>                              | <span data-ttu-id="7d9d2-144">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-144">none</span></span>                                 |
| <span data-ttu-id="7d9d2-145">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-145">Required?</span></span>                            | <span data-ttu-id="7d9d2-146">true</span><span class="sxs-lookup"><span data-stu-id="7d9d2-146">true</span></span>                                 |
| <span data-ttu-id="7d9d2-147">Placering?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-147">Position?</span></span>                            | <span data-ttu-id="7d9d2-148">Med namnet</span><span class="sxs-lookup"><span data-stu-id="7d9d2-148">named</span></span>                                |
| <span data-ttu-id="7d9d2-149">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7d9d2-149">Default Value</span></span>                        | <span data-ttu-id="7d9d2-150">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-150">none</span></span>                                 |
| <span data-ttu-id="7d9d2-151">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="7d9d2-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="7d9d2-153">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="7d9d2-154">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="7d9d2-155">-ConfigurationName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9d2-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="7d9d2-156">Anger namnet på sessionskonfigurationen för Windows PowerShell, även kallat runspace, som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="7d9d2-157">Alias</span><span class="sxs-lookup"><span data-stu-id="7d9d2-157">Aliases</span></span>                              | <span data-ttu-id="7d9d2-158">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-158">none</span></span>                                 |
| <span data-ttu-id="7d9d2-159">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-159">Required?</span></span>                            | <span data-ttu-id="7d9d2-160">true</span><span class="sxs-lookup"><span data-stu-id="7d9d2-160">true</span></span>                                 |
| <span data-ttu-id="7d9d2-161">Placering?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-161">Position?</span></span>                            | <span data-ttu-id="7d9d2-162">Med namnet</span><span class="sxs-lookup"><span data-stu-id="7d9d2-162">named</span></span>                                |
| <span data-ttu-id="7d9d2-163">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7d9d2-163">Default Value</span></span>                        | <span data-ttu-id="7d9d2-164">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-164">none</span></span>                                 |
| <span data-ttu-id="7d9d2-165">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="7d9d2-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="7d9d2-167">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="7d9d2-168">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="7d9d2-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9d2-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="7d9d2-170">Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att ändra auktoriseringsregler för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="7d9d2-171">Om du inte lägga till den här parametern används cmdlet det inloggade användarkontot.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="7d9d2-172">Få en **PSCredential** -objektet, vilket krävs för att lägga till auktoriseringsregler från en fjärrdator genom att köra den [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="7d9d2-173">Alias</span><span class="sxs-lookup"><span data-stu-id="7d9d2-173">Aliases</span></span>                              | <span data-ttu-id="7d9d2-174">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-174">none</span></span>                                 |
| <span data-ttu-id="7d9d2-175">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-175">Required?</span></span>                            | <span data-ttu-id="7d9d2-176">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-176">false</span></span>                                |
| <span data-ttu-id="7d9d2-177">Placering?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-177">Position?</span></span>                            | <span data-ttu-id="7d9d2-178">Med namnet</span><span class="sxs-lookup"><span data-stu-id="7d9d2-178">named</span></span>                                |
| <span data-ttu-id="7d9d2-179">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7d9d2-179">Default Value</span></span>                        | <span data-ttu-id="7d9d2-180">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-180">none</span></span>                                 |
| <span data-ttu-id="7d9d2-181">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="7d9d2-182">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-182">false</span></span>                                |
| <span data-ttu-id="7d9d2-183">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="7d9d2-184">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="7d9d2-185">-Force</span><span class="sxs-lookup"><span data-stu-id="7d9d2-185">-Force</span></span>

<span data-ttu-id="7d9d2-186">Tvingar kommandot att köras utan bekräftelse från användaren. \\</span><span class="sxs-lookup"><span data-stu-id="7d9d2-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="7d9d2-187">Dessutom kan uppmanas den också att bekräfta när du anger ett enkelt eller kort datornamn (till exempel ett namn som inte är ett domännamn eller är inte fullständigt kvalificerad).</span><span class="sxs-lookup"><span data-stu-id="7d9d2-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="7d9d2-188">Bekräftelse har begärts av säkerhetsskäl så att du kan använda enkla namn till bara lägga till en dator om datorn är i en arbetsgrupp.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="7d9d2-189">Alias</span><span class="sxs-lookup"><span data-stu-id="7d9d2-189">Aliases</span></span>                              | <span data-ttu-id="7d9d2-190">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-190">none</span></span>                                 |
| <span data-ttu-id="7d9d2-191">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-191">Required?</span></span>                            | <span data-ttu-id="7d9d2-192">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-192">false</span></span>                                |
| <span data-ttu-id="7d9d2-193">Placering?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-193">Position?</span></span>                            | <span data-ttu-id="7d9d2-194">Med namnet</span><span class="sxs-lookup"><span data-stu-id="7d9d2-194">named</span></span>                                |
| <span data-ttu-id="7d9d2-195">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7d9d2-195">Default Value</span></span>                        | <span data-ttu-id="7d9d2-196">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-196">none</span></span>                                 |
| <span data-ttu-id="7d9d2-197">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="7d9d2-198">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-198">false</span></span>                                |
| <span data-ttu-id="7d9d2-199">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="7d9d2-200">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="7d9d2-201">-RuleName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9d2-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="7d9d2-202">Anger det egna namnet för den här regeln.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="7d9d2-203">Alias</span><span class="sxs-lookup"><span data-stu-id="7d9d2-203">Aliases</span></span>                              | <span data-ttu-id="7d9d2-204">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-204">none</span></span>                                 |
| <span data-ttu-id="7d9d2-205">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-205">Required?</span></span>                            | <span data-ttu-id="7d9d2-206">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-206">false</span></span>                                |
| <span data-ttu-id="7d9d2-207">Placering?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-207">Position?</span></span>                            | <span data-ttu-id="7d9d2-208">Med namnet</span><span class="sxs-lookup"><span data-stu-id="7d9d2-208">named</span></span>                                |
| <span data-ttu-id="7d9d2-209">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7d9d2-209">Default Value</span></span>                        | <span data-ttu-id="7d9d2-210">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-210">none</span></span>                                 |
| <span data-ttu-id="7d9d2-211">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="7d9d2-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="7d9d2-213">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="7d9d2-214">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="7d9d2-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9d2-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="7d9d2-216">Anger namnet på en eller flera användargrupper i AD DS eller grupper som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="7d9d2-217">Alias</span><span class="sxs-lookup"><span data-stu-id="7d9d2-217">Aliases</span></span>                              | <span data-ttu-id="7d9d2-218">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-218">none</span></span>                                 |
| <span data-ttu-id="7d9d2-219">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-219">Required?</span></span>                            | <span data-ttu-id="7d9d2-220">true</span><span class="sxs-lookup"><span data-stu-id="7d9d2-220">true</span></span>                                 |
| <span data-ttu-id="7d9d2-221">Placering?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-221">Position?</span></span>                            | <span data-ttu-id="7d9d2-222">Med namnet</span><span class="sxs-lookup"><span data-stu-id="7d9d2-222">named</span></span>                                |
| <span data-ttu-id="7d9d2-223">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7d9d2-223">Default Value</span></span>                        | <span data-ttu-id="7d9d2-224">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-224">none</span></span>                                 |
| <span data-ttu-id="7d9d2-225">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="7d9d2-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="7d9d2-227">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="7d9d2-228">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="7d9d2-229">-UserName&lt;sträng\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9d2-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="7d9d2-230">Anger en eller flera användare som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="7d9d2-231">Användarnamnet kan vara ett lokalt användarkonto på gateway-datorn eller en användare i AD DS.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="7d9d2-232">Formatet är `domain\user` eller `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="7d9d2-233">Alias</span><span class="sxs-lookup"><span data-stu-id="7d9d2-233">Aliases</span></span>                              | <span data-ttu-id="7d9d2-234">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-234">none</span></span>                                 |
| <span data-ttu-id="7d9d2-235">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-235">Required?</span></span>                            | <span data-ttu-id="7d9d2-236">true</span><span class="sxs-lookup"><span data-stu-id="7d9d2-236">true</span></span>                                 |
| <span data-ttu-id="7d9d2-237">Placering?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-237">Position?</span></span>                            | <span data-ttu-id="7d9d2-238">1</span><span class="sxs-lookup"><span data-stu-id="7d9d2-238">1</span></span>                                    |
| <span data-ttu-id="7d9d2-239">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7d9d2-239">Default Value</span></span>                        | <span data-ttu-id="7d9d2-240">inget</span><span class="sxs-lookup"><span data-stu-id="7d9d2-240">none</span></span>                                 |
| <span data-ttu-id="7d9d2-241">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="7d9d2-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="7d9d2-243">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="7d9d2-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="7d9d2-244">falskt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="7d9d2-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="7d9d2-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="7d9d2-246">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="7d9d2-247">Mer information finns i [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="7d9d2-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="7d9d2-248">INDATA</span><span class="sxs-lookup"><span data-stu-id="7d9d2-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="7d9d2-249">Sträng</span><span class="sxs-lookup"><span data-stu-id="7d9d2-249">String</span></span>

<span data-ttu-id="7d9d2-250">Denna cmdlet accepterar en sträng eller en matris med strängar som indata.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="7d9d2-251">Sträng\[\]</span><span class="sxs-lookup"><span data-stu-id="7d9d2-251">String\[\]</span></span>

<span data-ttu-id="7d9d2-252">Denna cmdlet accepterar en sträng eller en matris med strängar som indata.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="7d9d2-253">Utdata:</span><span class="sxs-lookup"><span data-stu-id="7d9d2-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="7d9d2-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="7d9d2-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="7d9d2-255">Denna cmdlet returnerar den ett authorization-regelobjekt.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="7d9d2-256">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7d9d2-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="7d9d2-257">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="7d9d2-257">EXAMPLE 1</span></span>

<span data-ttu-id="7d9d2-258">Det här exemplet ger åtkomst till sessionskonfigurationen *PSWAEndpoint*, ett begränsat körningsutrymme på *srv2* för användare i den *SMAdmins* grupp. \\</span><span class="sxs-lookup"><span data-stu-id="7d9d2-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="7d9d2-259">**Obs**: datornamnet måste vara ett fullständigt kvalificerat domännamn (FQDN).</span><span class="sxs-lookup"><span data-stu-id="7d9d2-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="7d9d2-260">Administratörer definiera en begränsad sessionskonfiguration eller körningsutrymmen, vilket är ett begränsat antal cmdletar och uppgifter som slutanvändarna kan köras.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="7d9d2-261">Definiera ett begränsat körningsutrymme kan hindra användare från att komma åt andra datorer som inte i det tillåtna Windows PowerShell® runspace, vilket ger en säker anslutning.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="7d9d2-262">Mer information om sessionskonfigurationer finns [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) eller [installera och använda Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="7d9d2-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="7d9d2-263">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="7d9d2-263">EXAMPLE 2</span></span>

<span data-ttu-id="7d9d2-264">Det här exemplet ger åtkomst till Windows PowerShell-session standardkonfigurationen `Microsoft.PowerShell`på *srv2* för användare i användare med namnet contoso\\Användare1, contoso\\användare2, och contoso\\user3.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="7d9d2-265">Denna cmdlet skapar tre regler (1 per person).</span><span class="sxs-lookup"><span data-stu-id="7d9d2-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="7d9d2-266">EXEMPEL 3</span><span class="sxs-lookup"><span data-stu-id="7d9d2-266">EXAMPLE 3</span></span>

<span data-ttu-id="7d9d2-267">Det här exemplet illustrerar hur du indatavärden user name via pipeline.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="7d9d2-268">EXEMPEL 4</span><span class="sxs-lookup"><span data-stu-id="7d9d2-268">EXAMPLE 4</span></span>

<span data-ttu-id="7d9d2-269">Det här exemplet illustrerar hur alla parametrar tar värden från pipeline genom egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="7d9d2-270">EXEMPEL 5</span><span class="sxs-lookup"><span data-stu-id="7d9d2-270">EXAMPLE 5</span></span>

<span data-ttu-id="7d9d2-271">Det här exemplet lägger till en regel för att tillåta lokala användare med namnet *PswaServer\\ChrisLocal* åtkomst till servern med namnet *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="7d9d2-272">Det här exemplet illustrerar ett scenario där gatewayen är i en arbetsgrupp och måldatorn finns i en domän.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="7d9d2-273">Regeln gäller för lokala användare på gateway.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="7d9d2-274">På sidan Windows PowerShell Web Access-inloggning för att kunna autentisera användaren måste ange en annan uppsättning autentiseringsuppgifter i den **valfria anslutningsinställningar** område.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="7d9d2-275">Gateway-servern använder denna ytterligare uppsättning autentiseringsuppgifter för att autentisera användaren på måldatorn, en server med namnet *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="7d9d2-276">EXEMPEL 6</span><span class="sxs-lookup"><span data-stu-id="7d9d2-276">EXAMPLE 6</span></span>

<span data-ttu-id="7d9d2-277">Det här exemplet tillåter alla användare åtkomst till alla slutpunkter på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="7d9d2-278">Detta i praktiken inaktiverar auktoriseringsregler. \\</span><span class="sxs-lookup"><span data-stu-id="7d9d2-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="7d9d2-279">**Obs**: användning av den `*` jokertecken rekommenderas inte för känsliga distributioner och bör endast för testmiljöer eller användas i distributioner där säkerhet kan mjukas upp.</span><span class="sxs-lookup"><span data-stu-id="7d9d2-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="7d9d2-280">Se även</span><span class="sxs-lookup"><span data-stu-id="7d9d2-280">See Also</span></span>

- <span data-ttu-id="7d9d2-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="7d9d2-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="7d9d2-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="7d9d2-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d9d2-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="7d9d2-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="7d9d2-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="7d9d2-286">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="7d9d2-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="7d9d2-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="7d9d2-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
