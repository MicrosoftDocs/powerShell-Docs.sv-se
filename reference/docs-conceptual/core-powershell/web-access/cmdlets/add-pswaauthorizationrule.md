---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: "Lägg till pswaauthorizationrule"
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 18422f71b2a5f9af07af94e4324d3c7774f1d5ea
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="1ec28-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1ec28-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ec28-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1ec28-104">SYNOPSIS</span></span>

<span data-ttu-id="1ec28-105">Lägger till en ny auktoriseringsregel regeluppsättningen för auktorisering av Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="1ec28-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ec28-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ec28-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="1ec28-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="1ec28-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="1ec28-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="1ec28-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="1ec28-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="1ec28-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="1ec28-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="1ec28-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="1ec28-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1ec28-111">DESCRIPTION</span></span>

<span data-ttu-id="1ec28-112">Den **Add-PswaAuthorizationRule** cmdlet lägger till en ny auktoriseringsregel till Windows PowerShell® Web Access auktoriseringsregeluppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1ec28-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="1ec28-113">Du måste ange användare, datorer och Windows PowerShell-slutpunkter för den här regeln.</span><span class="sxs-lookup"><span data-stu-id="1ec28-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="1ec28-114">Du kan ange både användare och datorer genom enskilda användarkonton och datornamn eller genom att ange grupper.</span><span class="sxs-lookup"><span data-stu-id="1ec28-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="1ec28-115">För en dator som är ansluten till en Active Directory-domän, använder cmdlet säkerhetsidentifierare (SID) för datorn för att skapa regeln.</span><span class="sxs-lookup"><span data-stu-id="1ec28-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="1ec28-116">Detta gör att du kan använda ett kort namn, ett fullständigt kvalificerat domännamn (FQDN) eller en IP-adress för den **datornamn** på sidan logga in.</span><span class="sxs-lookup"><span data-stu-id="1ec28-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="1ec28-117">För en dator som inte är ansluten till en Active Directory-domän, skapar cmdleten regeln med hjälp av namnet på datorn som tillhandahålls av administratören.</span><span class="sxs-lookup"><span data-stu-id="1ec28-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="1ec28-118">Om du vill ansluta till den här datorn, måste användaren ange datornamnet exakt som det visas i regeln.</span><span class="sxs-lookup"><span data-stu-id="1ec28-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="1ec28-119">Om det finns flera datorer med samma namn i nätverket kan lösas kort namn till mer än en dator.</span><span class="sxs-lookup"><span data-stu-id="1ec28-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="1ec28-120">Detta kan leda till tvetydighet när en anslutning upprättas.</span><span class="sxs-lookup"><span data-stu-id="1ec28-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="1ec28-121">Till exempel om det finns en regel för arbetsgruppsdator med namnet ”*Server1*” och en ny dator med namnet *server1.contoso.com* är ansluten till nätverket med hjälp av auktoriseringsregler lyckas och Windows PowerShell Web Access försöker upprätta en anslutning till datorn med namnet ”*Server1*”.</span><span class="sxs-lookup"><span data-stu-id="1ec28-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="1ec28-122">Det är inte säkert att ansluta till den angivna arbetsgrupp-datorn. Försök kan göras på arbetsgruppen eller domän datorn med namnet ”*Server1*”.</span><span class="sxs-lookup"><span data-stu-id="1ec28-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="1ec28-123">Det rekommenderas att du använder det fullständiga Domännamnet för måldatorn när det är möjligt att skapa en auktoriseringsregel för att undvika tvetydighet.</span><span class="sxs-lookup"><span data-stu-id="1ec28-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="1ec28-124">Auktoriseringsregler utvärdera primära inloggning inloggningsuppgifterna för Windows PowerShell Web Access-användare, inte de alternativa autentiseringsuppgifterna (den andra uppsättningen av autentiseringsuppgifter finns i den **valfria anslutningsinställningar** avsnitt i den inloggningssidan).</span><span class="sxs-lookup"><span data-stu-id="1ec28-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="1ec28-125">Ett exempel på detta finns i exempel 6.</span><span class="sxs-lookup"><span data-stu-id="1ec28-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="1ec28-126">Parametrar</span><span class="sxs-lookup"><span data-stu-id="1ec28-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="1ec28-127">-ComputerGroupName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec28-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="1ec28-128">Anger namnet på en datorgrupp i Active Directory Domain Services (AD DS) eller lokala grupper som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="1ec28-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1ec28-129">Alias</span><span class="sxs-lookup"><span data-stu-id="1ec28-129">Aliases</span></span>                              | <span data-ttu-id="1ec28-130">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-130">none</span></span>                                 |
| <span data-ttu-id="1ec28-131">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="1ec28-131">Required?</span></span>                            | <span data-ttu-id="1ec28-132">SANT</span><span class="sxs-lookup"><span data-stu-id="1ec28-132">true</span></span>                                 |
| <span data-ttu-id="1ec28-133">Placering?</span><span class="sxs-lookup"><span data-stu-id="1ec28-133">Position?</span></span>                            | <span data-ttu-id="1ec28-134">Med namnet</span><span class="sxs-lookup"><span data-stu-id="1ec28-134">named</span></span>                                |
| <span data-ttu-id="1ec28-135">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="1ec28-135">Default Value</span></span>                        | <span data-ttu-id="1ec28-136">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-136">none</span></span>                                 |
| <span data-ttu-id="1ec28-137">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="1ec28-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ec28-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1ec28-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1ec28-139">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="1ec28-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ec28-140">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="1ec28-141">-ComputerName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec28-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="1ec28-142">Anger namnet på datorn som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="1ec28-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1ec28-143">Alias</span><span class="sxs-lookup"><span data-stu-id="1ec28-143">Aliases</span></span>                              | <span data-ttu-id="1ec28-144">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-144">none</span></span>                                 |
| <span data-ttu-id="1ec28-145">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="1ec28-145">Required?</span></span>                            | <span data-ttu-id="1ec28-146">SANT</span><span class="sxs-lookup"><span data-stu-id="1ec28-146">true</span></span>                                 |
| <span data-ttu-id="1ec28-147">Placering?</span><span class="sxs-lookup"><span data-stu-id="1ec28-147">Position?</span></span>                            | <span data-ttu-id="1ec28-148">Med namnet</span><span class="sxs-lookup"><span data-stu-id="1ec28-148">named</span></span>                                |
| <span data-ttu-id="1ec28-149">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="1ec28-149">Default Value</span></span>                        | <span data-ttu-id="1ec28-150">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-150">none</span></span>                                 |
| <span data-ttu-id="1ec28-151">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="1ec28-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ec28-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1ec28-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1ec28-153">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="1ec28-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ec28-154">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="1ec28-155">-ConfigurationName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec28-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="1ec28-156">Anger namnet på sessionskonfigurationen för Windows PowerShell, även kallat runspace, som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="1ec28-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1ec28-157">Alias</span><span class="sxs-lookup"><span data-stu-id="1ec28-157">Aliases</span></span>                              | <span data-ttu-id="1ec28-158">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-158">none</span></span>                                 |
| <span data-ttu-id="1ec28-159">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="1ec28-159">Required?</span></span>                            | <span data-ttu-id="1ec28-160">SANT</span><span class="sxs-lookup"><span data-stu-id="1ec28-160">true</span></span>                                 |
| <span data-ttu-id="1ec28-161">Placering?</span><span class="sxs-lookup"><span data-stu-id="1ec28-161">Position?</span></span>                            | <span data-ttu-id="1ec28-162">Med namnet</span><span class="sxs-lookup"><span data-stu-id="1ec28-162">named</span></span>                                |
| <span data-ttu-id="1ec28-163">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="1ec28-163">Default Value</span></span>                        | <span data-ttu-id="1ec28-164">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-164">none</span></span>                                 |
| <span data-ttu-id="1ec28-165">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="1ec28-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ec28-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1ec28-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1ec28-167">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="1ec28-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ec28-168">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="1ec28-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec28-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="1ec28-170">Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att ändra auktoriseringsregler för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="1ec28-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="1ec28-171">Om du inte lägga till den här parametern används cmdlet det inloggade användarkontot.</span><span class="sxs-lookup"><span data-stu-id="1ec28-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="1ec28-172">Få en **PSCredential** -objektet, vilket krävs för att lägga till auktoriseringsregler från en fjärrdator genom att köra den [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ec28-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="1ec28-173">Alias</span><span class="sxs-lookup"><span data-stu-id="1ec28-173">Aliases</span></span>                              | <span data-ttu-id="1ec28-174">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-174">none</span></span>                                 |
| <span data-ttu-id="1ec28-175">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="1ec28-175">Required?</span></span>                            | <span data-ttu-id="1ec28-176">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-176">false</span></span>                                |
| <span data-ttu-id="1ec28-177">Placering?</span><span class="sxs-lookup"><span data-stu-id="1ec28-177">Position?</span></span>                            | <span data-ttu-id="1ec28-178">Med namnet</span><span class="sxs-lookup"><span data-stu-id="1ec28-178">named</span></span>                                |
| <span data-ttu-id="1ec28-179">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="1ec28-179">Default Value</span></span>                        | <span data-ttu-id="1ec28-180">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-180">none</span></span>                                 |
| <span data-ttu-id="1ec28-181">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="1ec28-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ec28-182">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-182">false</span></span>                                |
| <span data-ttu-id="1ec28-183">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="1ec28-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ec28-184">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="1ec28-185">-Force</span><span class="sxs-lookup"><span data-stu-id="1ec28-185">-Force</span></span>

<span data-ttu-id="1ec28-186">Tvingar kommandot att köras utan bekräftelse från användaren. \\</span><span class="sxs-lookup"><span data-stu-id="1ec28-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="1ec28-187">Dessutom kan uppmanas den också att bekräfta när du anger ett enkelt eller kort datornamn (till exempel ett namn som inte är ett domännamn eller är inte fullständigt kvalificerad).</span><span class="sxs-lookup"><span data-stu-id="1ec28-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="1ec28-188">Bekräftelse har begärts av säkerhetsskäl så att du kan använda enkla namn till bara lägga till en dator om datorn är i en arbetsgrupp.</span><span class="sxs-lookup"><span data-stu-id="1ec28-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="1ec28-189">Alias</span><span class="sxs-lookup"><span data-stu-id="1ec28-189">Aliases</span></span>                              | <span data-ttu-id="1ec28-190">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-190">none</span></span>                                 |
| <span data-ttu-id="1ec28-191">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="1ec28-191">Required?</span></span>                            | <span data-ttu-id="1ec28-192">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-192">false</span></span>                                |
| <span data-ttu-id="1ec28-193">Placering?</span><span class="sxs-lookup"><span data-stu-id="1ec28-193">Position?</span></span>                            | <span data-ttu-id="1ec28-194">Med namnet</span><span class="sxs-lookup"><span data-stu-id="1ec28-194">named</span></span>                                |
| <span data-ttu-id="1ec28-195">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="1ec28-195">Default Value</span></span>                        | <span data-ttu-id="1ec28-196">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-196">none</span></span>                                 |
| <span data-ttu-id="1ec28-197">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="1ec28-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ec28-198">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-198">false</span></span>                                |
| <span data-ttu-id="1ec28-199">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="1ec28-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ec28-200">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="1ec28-201">-RuleName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec28-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="1ec28-202">Anger det egna namnet för den här regeln.</span><span class="sxs-lookup"><span data-stu-id="1ec28-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="1ec28-203">Alias</span><span class="sxs-lookup"><span data-stu-id="1ec28-203">Aliases</span></span>                              | <span data-ttu-id="1ec28-204">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-204">none</span></span>                                 |
| <span data-ttu-id="1ec28-205">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="1ec28-205">Required?</span></span>                            | <span data-ttu-id="1ec28-206">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-206">false</span></span>                                |
| <span data-ttu-id="1ec28-207">Placering?</span><span class="sxs-lookup"><span data-stu-id="1ec28-207">Position?</span></span>                            | <span data-ttu-id="1ec28-208">Med namnet</span><span class="sxs-lookup"><span data-stu-id="1ec28-208">named</span></span>                                |
| <span data-ttu-id="1ec28-209">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="1ec28-209">Default Value</span></span>                        | <span data-ttu-id="1ec28-210">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-210">none</span></span>                                 |
| <span data-ttu-id="1ec28-211">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="1ec28-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ec28-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1ec28-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1ec28-213">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="1ec28-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ec28-214">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="1ec28-215">-UserGroupName&lt;sträng\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec28-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="1ec28-216">Anger namnet på en eller flera användargrupper i AD DS eller grupper som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="1ec28-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1ec28-217">Alias</span><span class="sxs-lookup"><span data-stu-id="1ec28-217">Aliases</span></span>                              | <span data-ttu-id="1ec28-218">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-218">none</span></span>                                 |
| <span data-ttu-id="1ec28-219">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="1ec28-219">Required?</span></span>                            | <span data-ttu-id="1ec28-220">SANT</span><span class="sxs-lookup"><span data-stu-id="1ec28-220">true</span></span>                                 |
| <span data-ttu-id="1ec28-221">Placering?</span><span class="sxs-lookup"><span data-stu-id="1ec28-221">Position?</span></span>                            | <span data-ttu-id="1ec28-222">Med namnet</span><span class="sxs-lookup"><span data-stu-id="1ec28-222">named</span></span>                                |
| <span data-ttu-id="1ec28-223">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="1ec28-223">Default Value</span></span>                        | <span data-ttu-id="1ec28-224">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-224">none</span></span>                                 |
| <span data-ttu-id="1ec28-225">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="1ec28-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ec28-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1ec28-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="1ec28-227">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="1ec28-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ec28-228">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="1ec28-229">-UserName&lt;sträng\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec28-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="1ec28-230">Anger en eller flera användare som den här regeln beviljar åtkomst.</span><span class="sxs-lookup"><span data-stu-id="1ec28-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="1ec28-231">Användarnamnet kan vara ett lokalt användarkonto på gateway-datorn eller en användare i AD DS.</span><span class="sxs-lookup"><span data-stu-id="1ec28-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="1ec28-232">Formatet är `domain\user` eller `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="1ec28-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="1ec28-233">Alias</span><span class="sxs-lookup"><span data-stu-id="1ec28-233">Aliases</span></span>                              | <span data-ttu-id="1ec28-234">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-234">none</span></span>                                 |
| <span data-ttu-id="1ec28-235">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="1ec28-235">Required?</span></span>                            | <span data-ttu-id="1ec28-236">SANT</span><span class="sxs-lookup"><span data-stu-id="1ec28-236">true</span></span>                                 |
| <span data-ttu-id="1ec28-237">Placering?</span><span class="sxs-lookup"><span data-stu-id="1ec28-237">Position?</span></span>                            | <span data-ttu-id="1ec28-238">1</span><span class="sxs-lookup"><span data-stu-id="1ec28-238">1</span></span>                                    |
| <span data-ttu-id="1ec28-239">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="1ec28-239">Default Value</span></span>                        | <span data-ttu-id="1ec28-240">inget</span><span class="sxs-lookup"><span data-stu-id="1ec28-240">none</span></span>                                 |
| <span data-ttu-id="1ec28-241">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="1ec28-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ec28-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1ec28-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="1ec28-243">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="1ec28-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ec28-244">falskt</span><span class="sxs-lookup"><span data-stu-id="1ec28-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="1ec28-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec28-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="1ec28-246">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="1ec28-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="1ec28-247">Mer information finns i [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="1ec28-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="1ec28-248">INDATA</span><span class="sxs-lookup"><span data-stu-id="1ec28-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="1ec28-249">Sträng</span><span class="sxs-lookup"><span data-stu-id="1ec28-249">String</span></span>

<span data-ttu-id="1ec28-250">Denna cmdlet accepterar en sträng eller en matris med strängar som indata.</span><span class="sxs-lookup"><span data-stu-id="1ec28-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="1ec28-251">Sträng\[\]</span><span class="sxs-lookup"><span data-stu-id="1ec28-251">String\[\]</span></span>

<span data-ttu-id="1ec28-252">Denna cmdlet accepterar en sträng eller en matris med strängar som indata.</span><span class="sxs-lookup"><span data-stu-id="1ec28-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="1ec28-253">Utdata:</span><span class="sxs-lookup"><span data-stu-id="1ec28-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="1ec28-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1ec28-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="1ec28-255">Denna cmdlet returnerar den ett authorization-regelobjekt.</span><span class="sxs-lookup"><span data-stu-id="1ec28-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="1ec28-256">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1ec28-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="1ec28-257">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="1ec28-257">EXAMPLE 1</span></span>

<span data-ttu-id="1ec28-258">Det här exemplet ger åtkomst till sessionskonfigurationen *PSWAEndpoint*, ett begränsat körningsutrymme på *srv2* för användare i den *SMAdmins* grupp. \\</span><span class="sxs-lookup"><span data-stu-id="1ec28-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="1ec28-259">**Obs**: datornamnet måste vara ett fullständigt kvalificerat domännamn (FQDN).</span><span class="sxs-lookup"><span data-stu-id="1ec28-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="1ec28-260">Administratörer definiera en begränsad sessionskonfiguration eller körningsutrymmen, vilket är ett begränsat antal cmdletar och uppgifter som slutanvändarna kan köras.</span><span class="sxs-lookup"><span data-stu-id="1ec28-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="1ec28-261">Definiera ett begränsat körningsutrymme kan hindra användare från att komma åt andra datorer som inte i det tillåtna Windows PowerShell® runspace, vilket ger en säker anslutning.</span><span class="sxs-lookup"><span data-stu-id="1ec28-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="1ec28-262">Mer information om sessionskonfigurationer finns [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) eller [installera och använda Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="1ec28-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="1ec28-263">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="1ec28-263">EXAMPLE 2</span></span>

<span data-ttu-id="1ec28-264">Det här exemplet ger åtkomst till Windows PowerShell-session standardkonfigurationen `Microsoft.PowerShell`på *srv2* för användare i användare med namnet contoso\\Användare1, contoso\\användare2, och contoso\\user3.</span><span class="sxs-lookup"><span data-stu-id="1ec28-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="1ec28-265">Denna cmdlet skapar tre regler (1 per person).</span><span class="sxs-lookup"><span data-stu-id="1ec28-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="1ec28-266">EXEMPEL 3</span><span class="sxs-lookup"><span data-stu-id="1ec28-266">EXAMPLE 3</span></span>

<span data-ttu-id="1ec28-267">Det här exemplet illustrerar hur du indatavärden user name via pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ec28-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="1ec28-268">EXEMPEL 4</span><span class="sxs-lookup"><span data-stu-id="1ec28-268">EXAMPLE 4</span></span>

<span data-ttu-id="1ec28-269">Det här exemplet illustrerar hur alla parametrar tar värden från pipeline genom egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="1ec28-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="1ec28-270">EXEMPEL 5</span><span class="sxs-lookup"><span data-stu-id="1ec28-270">EXAMPLE 5</span></span>

<span data-ttu-id="1ec28-271">Det här exemplet lägger till en regel för att tillåta lokala användare med namnet *PswaServer\\ChrisLocal* åtkomst till servern med namnet *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="1ec28-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="1ec28-272">Det här exemplet illustrerar ett scenario där gatewayen är i en arbetsgrupp och måldatorn finns i en domän.</span><span class="sxs-lookup"><span data-stu-id="1ec28-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="1ec28-273">Regeln gäller för lokala användare på gateway.</span><span class="sxs-lookup"><span data-stu-id="1ec28-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="1ec28-274">På sidan Windows PowerShell Web Access-inloggning för att kunna autentisera användaren måste ange en annan uppsättning autentiseringsuppgifter i den **valfria anslutningsinställningar** område.</span><span class="sxs-lookup"><span data-stu-id="1ec28-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="1ec28-275">Gateway-servern använder denna ytterligare uppsättning autentiseringsuppgifter för att autentisera användaren på måldatorn, en server med namnet *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="1ec28-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="1ec28-276">EXEMPEL 6</span><span class="sxs-lookup"><span data-stu-id="1ec28-276">EXAMPLE 6</span></span>

<span data-ttu-id="1ec28-277">Det här exemplet tillåter alla användare åtkomst till alla slutpunkter på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="1ec28-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="1ec28-278">Detta i praktiken inaktiverar auktoriseringsregler. \\</span><span class="sxs-lookup"><span data-stu-id="1ec28-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="1ec28-279">**Obs**: användning av den `*` jokertecken rekommenderas inte för känsliga distributioner och bör endast för testmiljöer eller användas i distributioner där säkerhet kan mjukas upp.</span><span class="sxs-lookup"><span data-stu-id="1ec28-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="1ec28-280">Se även</span><span class="sxs-lookup"><span data-stu-id="1ec28-280">See Also</span></span>

- <span data-ttu-id="1ec28-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="1ec28-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="1ec28-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="1ec28-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="1ec28-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="1ec28-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="1ec28-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="1ec28-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="1ec28-285">Lägg till medlem</span><span class="sxs-lookup"><span data-stu-id="1ec28-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="1ec28-286">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="1ec28-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="1ec28-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="1ec28-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
