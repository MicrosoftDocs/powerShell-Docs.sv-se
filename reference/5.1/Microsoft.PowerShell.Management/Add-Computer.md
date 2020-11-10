---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: e3d1c5c071a334bddbfbc547ef2cc07e9e5c90aa
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388356"
---
# <span data-ttu-id="dde7c-103">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="dde7c-103">Add-Computer</span></span>

## <span data-ttu-id="dde7c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dde7c-104">SYNOPSIS</span></span>
<span data-ttu-id="dde7c-105">Lägg till den lokala datorn i en domän eller arbets grupp.</span><span class="sxs-lookup"><span data-stu-id="dde7c-105">Add the local computer to a domain or workgroup.</span></span>

## <span data-ttu-id="dde7c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dde7c-106">SYNTAX</span></span>

### <span data-ttu-id="dde7c-107">Domän (standard)</span><span class="sxs-lookup"><span data-stu-id="dde7c-107">Domain (Default)</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dde7c-108">Arbetsgrupp</span><span class="sxs-lookup"><span data-stu-id="dde7c-108">Workgroup</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="dde7c-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dde7c-109">DESCRIPTION</span></span>

<span data-ttu-id="dde7c-110">`Add-Computer`Cmdleten lägger till den lokala datorn eller fjärrdatorerna i en domän eller arbets grupp, eller flyttar dem från en domän till en annan.</span><span class="sxs-lookup"><span data-stu-id="dde7c-110">The `Add-Computer` cmdlet adds the local computer or remote computers to a domain or workgroup, or moves them from one domain to another.</span></span> <span data-ttu-id="dde7c-111">Det skapar också ett domän konto om datorn läggs till i domänen utan ett konto.</span><span class="sxs-lookup"><span data-stu-id="dde7c-111">It also creates a domain account if the computer is added to the domain without an account.</span></span>

<span data-ttu-id="dde7c-112">Du kan använda parametrarna för denna cmdlet för att ange en organisationsenhet (OU) och domänkontrollant eller för att utföra en oskyddad anslutning.</span><span class="sxs-lookup"><span data-stu-id="dde7c-112">You can use the parameters of this cmdlet to specify an organizational unit (OU) and domain controller or to perform an unsecure join.</span></span>

<span data-ttu-id="dde7c-113">Om du vill hämta resultatet av kommandot använder du parametrarna **verbose** och **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="dde7c-113">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span>

## <span data-ttu-id="dde7c-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dde7c-114">EXAMPLES</span></span>

### <span data-ttu-id="dde7c-115">Exempel 1: Lägg till en lokal dator i en domän och starta sedan om datorn</span><span class="sxs-lookup"><span data-stu-id="dde7c-115">Example 1: Add a local computer to a domain then restart the computer</span></span>

```powershell
Add-Computer -DomainName Domain01 -Restart
```

<span data-ttu-id="dde7c-116">Detta kommando lägger till den lokala datorn i Domain01-domänen och startar sedan om datorn för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="dde7c-116">This command adds the local computer to the Domain01 domain and then restarts the computer to make the change effective.</span></span>

### <span data-ttu-id="dde7c-117">Exempel 2: lägga till en lokal dator i en arbets grupp</span><span class="sxs-lookup"><span data-stu-id="dde7c-117">Example 2: Add a local computer to a workgroup</span></span>

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

<span data-ttu-id="dde7c-118">Detta kommando lägger till den lokala datorn i arbets gruppen – en arbets grupp.</span><span class="sxs-lookup"><span data-stu-id="dde7c-118">This command adds the local computer to the Workgroup-A workgroup.</span></span>

### <span data-ttu-id="dde7c-119">Exempel 3: lägga till en lokal dator i en domän</span><span class="sxs-lookup"><span data-stu-id="dde7c-119">Example 3: Add a local computer to a domain</span></span>

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

<span data-ttu-id="dde7c-120">Detta kommando lägger till den lokala datorn i Domain01-domänen med hjälp av Domain01\DC01-domänkontrollanten.</span><span class="sxs-lookup"><span data-stu-id="dde7c-120">This command adds the local computer to the Domain01 domain by using the Domain01\DC01 domain controller.</span></span>

<span data-ttu-id="dde7c-121">Kommandot använder parametrarna **Passthru** och **verbose** för att få detaljerad information om resultatet av kommandot.</span><span class="sxs-lookup"><span data-stu-id="dde7c-121">The command uses the **PassThru** and **Verbose** parameters to get detailed information about the results of the command.</span></span>

### <span data-ttu-id="dde7c-122">Exempel 4: Lägg till en lokal dator i en domän med parametern OUPath</span><span class="sxs-lookup"><span data-stu-id="dde7c-122">Example 4: Add a local computer to a domain using the OUPath parameter</span></span>

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

<span data-ttu-id="dde7c-123">Detta kommando lägger till den lokala datorn i Domain02-domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-123">This command adds the local computer to the Domain02 domain.</span></span>
<span data-ttu-id="dde7c-124">Den använder parametern OUPath för att ange organisationsenhet för de nya kontona.</span><span class="sxs-lookup"><span data-stu-id="dde7c-124">It uses the OUPath parameter to specify the organizational unit for the new accounts.</span></span>

### <span data-ttu-id="dde7c-125">Exempel 5: lägga till en lokal dator i en domän med hjälp av autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="dde7c-125">Example 5: Add a local computer to a domain using credentials</span></span>

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

<span data-ttu-id="dde7c-126">Detta kommando lägger till Server01-datorn till Domain02-domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-126">This command adds the Server01 computer to the Domain02 domain.</span></span> <span data-ttu-id="dde7c-127">Parametern **LocalCredential** används för att ange ett användar konto som har behörighet att ansluta till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="dde7c-127">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the Server01 computer.</span></span> <span data-ttu-id="dde7c-128">Den använder parametern **Credential** för att ange ett användar konto som har behörighet att ansluta datorer till domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-128">It uses the **Credential** parameter to specify a user account that has permission to join computers to the domain.</span></span> <span data-ttu-id="dde7c-129">Den använder parametern **restart** för att starta om datorn när anslutnings åtgärden har slutförts och **Force** -parametern för att utelämna användar bekräftelse meddelanden.</span><span class="sxs-lookup"><span data-stu-id="dde7c-129">It uses the **Restart** parameter to restart the computer after the join operation completes and the **Force** parameter to suppress user confirmation messages.</span></span>

### <span data-ttu-id="dde7c-130">Exempel 6: flytta en grupp med datorer till en ny domän</span><span class="sxs-lookup"><span data-stu-id="dde7c-130">Example 6: Move a group of computers to a new domain</span></span>

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="dde7c-131">Det här kommandot flyttar Server01-och Server02-datorer och den lokala datorn från Domain01 till Domain02.</span><span class="sxs-lookup"><span data-stu-id="dde7c-131">This command moves the Server01 and Server02 computers, and the local computer, from Domain01 to Domain02.</span></span>

<span data-ttu-id="dde7c-132">Parametern **LocalCredential** används för att ange ett användar konto som har behörighet att ansluta till de tre berörda datorerna.</span><span class="sxs-lookup"><span data-stu-id="dde7c-132">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the three affected computers.</span></span> <span data-ttu-id="dde7c-133">Parametern **UnjoinDomainCredential** används för att ange ett användar konto som har behörighet att koppla från datorerna från Domain01-domänen och parametern **Credential** för att ange ett användar konto som har behörighet att ansluta till datorerna till Domain02-domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-133">It uses the **UnjoinDomainCredential** parameter to specify a user account that has permission to unjoin the computers from the Domain01 domain and the **Credential** parameter to specify a user account that has permission to join the computers to the Domain02 domain.</span></span> <span data-ttu-id="dde7c-134">Den använder parametern **restart** för att starta om alla tre datorerna när flyttningen är klar.</span><span class="sxs-lookup"><span data-stu-id="dde7c-134">It uses the **Restart** parameter to restart all three computers after the move is complete.</span></span>

### <span data-ttu-id="dde7c-135">Exempel 7: flytta en dator till en ny domän och ändra namnet på datorn</span><span class="sxs-lookup"><span data-stu-id="dde7c-135">Example 7: Move a computer to a new domain and change the name of the computer</span></span>

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="dde7c-136">Det här kommandot flyttar Server01-datorn till Domain02 och ändrar dator namnet till Server044.</span><span class="sxs-lookup"><span data-stu-id="dde7c-136">This command moves the Server01 computer to the Domain02 and changes the machine name to Server044.</span></span>

<span data-ttu-id="dde7c-137">Kommandot använder den aktuella användarens autentiseringsuppgifter för att ansluta till Server01-datorn och ta bort anslutningen från den aktuella domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-137">The command uses the credential of the current user to connect to the Server01 computer and unjoin it from its current domain.</span></span> <span data-ttu-id="dde7c-138">Den använder parametern **Credential** för att ange ett användar konto som har behörighet att ansluta datorn till Domain02-domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-138">It uses the **Credential** parameter to specify a user account that has permission to join the computer to the Domain02 domain.</span></span>

### <span data-ttu-id="dde7c-139">Exempel 8: lägga till datorer som listas i en fil till en ny domän</span><span class="sxs-lookup"><span data-stu-id="dde7c-139">Example 8: Add computers listed in a file to a new domain</span></span>

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

<span data-ttu-id="dde7c-140">Detta kommando lägger till de datorer som listas i Servers.txt-filen till Domain02-domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-140">This command adds the computers that are listed in the Servers.txt file to the Domain02 domain.</span></span> <span data-ttu-id="dde7c-141">Parametern **Options** används för att ange alternativet **Win9xUpgrade** .</span><span class="sxs-lookup"><span data-stu-id="dde7c-141">It uses the **Options** parameter to specify the **Win9xUpgrade** option.</span></span> <span data-ttu-id="dde7c-142">Parametern **restart** startar om alla nyligen tillagda datorer när kopplingen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="dde7c-142">The **Restart** parameter restarts all of the newly added computers after the join operation completes.</span></span>

### <span data-ttu-id="dde7c-143">Exempel 9: lägga till en dator i en domän med fördefinierade autentiseringsuppgifter för datorn</span><span class="sxs-lookup"><span data-stu-id="dde7c-143">Example 9: Add a computer to a domain using predefined computer credentials</span></span>

<span data-ttu-id="dde7c-144">Det här första kommandot ska köras av en administratör från en dator som redan är ansluten till en domän `Domain03` :</span><span class="sxs-lookup"><span data-stu-id="dde7c-144">This first command should be run by an administrator from a computer that is already joined to domain `Domain03`:</span></span>

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

<span data-ttu-id="dde7c-145">Den här kombinationen av kommandon skapar ett nytt dator konto med ett fördefinierat namn och tillfälligt kopplings lösen ord i en domän med en befintlig domänansluten dator.</span><span class="sxs-lookup"><span data-stu-id="dde7c-145">This combination of commands creates a new computer account with a predefined name and temporary join password in a domain using an existing domain-joined computer.</span></span> <span data-ttu-id="dde7c-146">Sedan är en dator med det fördefinierade namnet ansluts domänen med endast dator namnet och det tillfälliga kopplings lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="dde7c-146">Then separately, a computer with the predefined name joins the domain using only the computer name and the temporary join password.</span></span>
<span data-ttu-id="dde7c-147">Det fördefinierade lösen ordet används bara för att stödja kopplings åtgärden och ersätts som en del av vanliga dator konto procedurer när datorn har slutfört anslutningen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-147">The predefined password is only used to support the join operation and is replaced as part of normal computer account procedures after the computer completes the join.</span></span>

## <span data-ttu-id="dde7c-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dde7c-148">PARAMETERS</span></span>

### <span data-ttu-id="dde7c-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="dde7c-149">-ComputerName</span></span>

<span data-ttu-id="dde7c-150">Anger de datorer som ska läggas till i en domän eller arbets grupp.</span><span class="sxs-lookup"><span data-stu-id="dde7c-150">Specifies the computers to add to a domain or workgroup.</span></span>
<span data-ttu-id="dde7c-151">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dde7c-151">The default is the local computer.</span></span>

<span data-ttu-id="dde7c-152">Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn för var och en av de fjärranslutna datorerna.</span><span class="sxs-lookup"><span data-stu-id="dde7c-152">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of each of the remote computers.</span></span> <span data-ttu-id="dde7c-153">Om du vill ange den lokala datorn skriver du datorns namn, en punkt ( `.` ) eller "localhost".</span><span class="sxs-lookup"><span data-stu-id="dde7c-153">To specify the local computer, type the computer name, a dot (`.`), or "localhost".</span></span>

<span data-ttu-id="dde7c-154">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="dde7c-154">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="dde7c-155">Du kan använda parametern **computername** för `Add-Computer` även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="dde7c-155">You can use the **ComputerName** parameter of `Add-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="dde7c-156">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dde7c-156">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="dde7c-157">-Credential</span></span>

<span data-ttu-id="dde7c-158">Anger ett användar konto som har behörighet att ansluta datorer till en ny domän.</span><span class="sxs-lookup"><span data-stu-id="dde7c-158">Specifies a user account that has permission to join the computers to a new domain.</span></span>
<span data-ttu-id="dde7c-159">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="dde7c-159">The default is the current user.</span></span>

<span data-ttu-id="dde7c-160">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dde7c-160">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="dde7c-161">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="dde7c-161">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="dde7c-162">Använd parametern **UnjoinDomainCredential** om du vill ange ett användar konto som har behörighet att ta bort datorn från den aktuella domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-162">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span> <span data-ttu-id="dde7c-163">Om du vill ange ett användar konto som har behörighet att ansluta till en fjärrdator använder du parametern **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="dde7c-163">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-164">-DomainName</span><span class="sxs-lookup"><span data-stu-id="dde7c-164">-DomainName</span></span>

<span data-ttu-id="dde7c-165">Anger den domän som datorerna ska läggas till i.</span><span class="sxs-lookup"><span data-stu-id="dde7c-165">Specifies the domain to which the computers are added.</span></span> <span data-ttu-id="dde7c-166">Den här parametern krävs när du lägger till datorerna i en domän.</span><span class="sxs-lookup"><span data-stu-id="dde7c-166">This parameter is required when adding the computers to a domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-167">-Force</span><span class="sxs-lookup"><span data-stu-id="dde7c-167">-Force</span></span>

<span data-ttu-id="dde7c-168">Förhindrar att användaren bekräftar frågan.</span><span class="sxs-lookup"><span data-stu-id="dde7c-168">Suppresses the user confirmation prompt.</span></span> <span data-ttu-id="dde7c-169">Utan den här parametern måste `Add-Computer` du bekräfta att varje dator ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="dde7c-169">Without this parameter, `Add-Computer` requires you to confirm the addition of each computer.</span></span>

<span data-ttu-id="dde7c-170">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dde7c-170">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-171">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="dde7c-171">-LocalCredential</span></span>

<span data-ttu-id="dde7c-172">Anger ett användar konto som har behörighet att ansluta till de datorer som anges av parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="dde7c-172">Specifies a user account that has permission to connect to the computers that are specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="dde7c-173">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="dde7c-173">The default is the current user.</span></span>

<span data-ttu-id="dde7c-174">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dde7c-174">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="dde7c-175">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="dde7c-175">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="dde7c-176">Om du vill ange ett användar konto som har behörighet att lägga till datorer i en ny domän, använder du parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="dde7c-176">To specify a user account that has permission to add the computers to a new domain, use the **Credential** parameter.</span></span> <span data-ttu-id="dde7c-177">Om du vill ange ett användar konto som har behörighet att ta bort datorerna från den aktuella domänen använder du parametern **UnjoinDomainCredential** .</span><span class="sxs-lookup"><span data-stu-id="dde7c-177">To specify a user account that has permission to remove the computers from their current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="dde7c-178">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dde7c-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-179">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="dde7c-179">-NewName</span></span>

<span data-ttu-id="dde7c-180">Anger ett nytt namn för datorn i den nya domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-180">Specifies a new name for the computer in the new domain.</span></span> <span data-ttu-id="dde7c-181">Den här parametern är endast giltig när en dator läggs till eller flyttas.</span><span class="sxs-lookup"><span data-stu-id="dde7c-181">This parameter is valid only when one computer is being added or moved.</span></span>

<span data-ttu-id="dde7c-182">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dde7c-182">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-183">– Alternativ</span><span class="sxs-lookup"><span data-stu-id="dde7c-183">-Options</span></span>

<span data-ttu-id="dde7c-184">Anger avancerade alternativ för åtgärden **Lägg till dator** anslutning.</span><span class="sxs-lookup"><span data-stu-id="dde7c-184">Specifies advanced options for the **Add-Computer** join operation.</span></span> <span data-ttu-id="dde7c-185">Ange ett eller flera värden i en kommaavgränsad sträng.</span><span class="sxs-lookup"><span data-stu-id="dde7c-185">Enter one or more values in a comma-separated string.</span></span>

<span data-ttu-id="dde7c-186">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="dde7c-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dde7c-187">**AccountCreate** : skapar ett domän konto.</span><span class="sxs-lookup"><span data-stu-id="dde7c-187">**AccountCreate** : Creates a domain account.</span></span> <span data-ttu-id="dde7c-188">Cmdleten **Add-Computer** skapar automatiskt ett domän konto när den lägger till en dator i en domän.</span><span class="sxs-lookup"><span data-stu-id="dde7c-188">The **Add-Computer** cmdlet automatically creates a domain account when it adds a computer to a domain.</span></span> <span data-ttu-id="dde7c-189">Det här alternativet ingår för fullständighet.</span><span class="sxs-lookup"><span data-stu-id="dde7c-189">This option is included for completeness.</span></span>

- <span data-ttu-id="dde7c-190">**Win9XUpgrade** : anger att anslutnings åtgärden ingår i en uppgradering av Windows-operativsystemet.</span><span class="sxs-lookup"><span data-stu-id="dde7c-190">**Win9XUpgrade** : Indicates that the join operation is part of a Windows operating system upgrade.</span></span>

- <span data-ttu-id="dde7c-191">**UnsecuredJoin** : utför en oskyddad anslutning.</span><span class="sxs-lookup"><span data-stu-id="dde7c-191">**UnsecuredJoin** : Performs an unsecured join.</span></span> <span data-ttu-id="dde7c-192">Om du vill begära en oskyddad anslutning använder du den *oskyddade* parametern eller det här alternativet.</span><span class="sxs-lookup"><span data-stu-id="dde7c-192">To request an unsecured join, use the *Unsecure* parameter or this option.</span></span> <span data-ttu-id="dde7c-193">Om du vill skicka ett dator lösen ord måste du använda det här alternativet i kombination med `PasswordPass` alternativ.</span><span class="sxs-lookup"><span data-stu-id="dde7c-193">If you want to pass a machine password, then you must use this option in combination with `PasswordPass` option.</span></span>

- <span data-ttu-id="dde7c-194">**PasswordPass** : anger datorns lösen ord till värdet för *Credential* -parametern (DomainCredential) när en oskyddad anslutning har utförts.</span><span class="sxs-lookup"><span data-stu-id="dde7c-194">**PasswordPass** : Sets the machine password to the value of the *Credential* (DomainCredential) parameter after performing an unsecured join.</span></span> <span data-ttu-id="dde7c-195">Det här alternativet anger också att värdet för parametern *Credential* (DomainCredential) är ett dator lösen ord, inte ett användar lösen ord.</span><span class="sxs-lookup"><span data-stu-id="dde7c-195">This option also indicates that the value of the *Credential* (DomainCredential) parameter is a machine password, not a user password.</span></span> <span data-ttu-id="dde7c-196">Det här alternativet är endast giltigt när `UnsecuredJoin` alternativet har angetts.</span><span class="sxs-lookup"><span data-stu-id="dde7c-196">This option is valid only when the `UnsecuredJoin` option is specified.</span></span> <span data-ttu-id="dde7c-197">När du använder det här alternativet måste autentiseringsuppgiften som anges `-Credential` för *must* parametern ha ett null-användarnamn.</span><span class="sxs-lookup"><span data-stu-id="dde7c-197">When using this option, the credential provided to the `-Credential` parameter *must* have a null username.</span></span>

- <span data-ttu-id="dde7c-198">**JoinWithNewName** : byter namn på dator namnet i den nya domänen till det namn som anges av parametern *Nyttnamn* .</span><span class="sxs-lookup"><span data-stu-id="dde7c-198">**JoinWithNewName** : Renames the computer name in the new domain to the name specified by the *NewName* parameter.</span></span> <span data-ttu-id="dde7c-199">När du använder parametern *Nyttnamn* anges det här alternativet automatiskt.</span><span class="sxs-lookup"><span data-stu-id="dde7c-199">When you use the *NewName* parameter, this option is set automatically.</span></span> <span data-ttu-id="dde7c-200">Det här alternativet är avsett att användas med Rename-Computer-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dde7c-200">This option is designed to be used with the Rename-Computer cmdlet.</span></span> <span data-ttu-id="dde7c-201">Om du använder cmdleten **rename-Computer** för att byta namn på datorn, men inte startar om datorn för att göra ändringen gällande, kan du använda den här parametern för att ansluta datorn till en domän med det nya namnet.</span><span class="sxs-lookup"><span data-stu-id="dde7c-201">If you use the **Rename-Computer** cmdlet to rename the computer, but do not restart the computer to make the change effective, you can use this parameter to join the computer to a domain with its new name.</span></span>

- <span data-ttu-id="dde7c-202">**JoinReadOnly** : använder ett befintligt dator konto för att ansluta datorn till en skrivskyddad domänkontrollant.</span><span class="sxs-lookup"><span data-stu-id="dde7c-202">**JoinReadOnly** : Uses an existing machine account to join the computer to a read-only domain controller.</span></span> <span data-ttu-id="dde7c-203">Dator kontot måste läggas till i listan över tillåtna för lösenordsreplikeringsprincipen och konto lösen ordet måste replikeras till den skrivskyddade domänkontrollanten före kopplings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="dde7c-203">The machine account must be added to the allowed list for password replication policy and the account password must be replicated to the read-only domain controller prior to the join operation.</span></span>

- <span data-ttu-id="dde7c-204">**InstallInvoke** : anger flaggorna Create (0x2) och Delete (0x4) för parametern **FJoinOptions** för **JoinDomainOrWorkgroup** -metoden.</span><span class="sxs-lookup"><span data-stu-id="dde7c-204">**InstallInvoke** : Sets the create (0x2) and delete (0x4) flags of the **FJoinOptions** parameter of the **JoinDomainOrWorkgroup** method.</span></span> <span data-ttu-id="dde7c-205">Mer information om **JoinDomainOrWorkgroup** -metoden finns i [JoinDomainOrWorkgroup-metoden i Win32_ComputerSystem-klassen](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem).</span><span class="sxs-lookup"><span data-stu-id="dde7c-205">For more information about the **JoinDomainOrWorkgroup** method, see [JoinDomainOrWorkgroup method of the Win32_ComputerSystem class](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem).</span></span>
  <span data-ttu-id="dde7c-206">Mer information om de här alternativen finns i [NetJoinDomain-funktionen](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain).</span><span class="sxs-lookup"><span data-stu-id="dde7c-206">For more information about these options, see [NetJoinDomain function](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain).</span></span>

<span data-ttu-id="dde7c-207">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dde7c-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-208">-OUPath</span><span class="sxs-lookup"><span data-stu-id="dde7c-208">-OUPath</span></span>

<span data-ttu-id="dde7c-209">Anger en organisationsenhet (OU) för domän kontot.</span><span class="sxs-lookup"><span data-stu-id="dde7c-209">Specifies an organizational unit (OU) for the domain account.</span></span> <span data-ttu-id="dde7c-210">Ange det fullständiga unika namnet på ORGANISATIONSENHETen inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="dde7c-210">Enter the full distinguished name of the OU in quotation marks.</span></span> <span data-ttu-id="dde7c-211">Standardvärdet är standard ORGANISATIONSENHETen för dator objekt i domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-211">The default value is the default OU for machine objects in the domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-212">– PassThru</span><span class="sxs-lookup"><span data-stu-id="dde7c-212">-PassThru</span></span>

<span data-ttu-id="dde7c-213">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="dde7c-213">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="dde7c-214">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="dde7c-214">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="dde7c-215">-Restart</span><span class="sxs-lookup"><span data-stu-id="dde7c-215">-Restart</span></span>

<span data-ttu-id="dde7c-216">Startar om datorerna som har lagts till i domänen eller arbets gruppen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-216">Restarts the computers that were added to the domain or workgroup.</span></span> <span data-ttu-id="dde7c-217">En omstart krävs ofta för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="dde7c-217">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="dde7c-218">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dde7c-218">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-219">-Server</span><span class="sxs-lookup"><span data-stu-id="dde7c-219">-Server</span></span>

<span data-ttu-id="dde7c-220">Anger namnet på en domänkontrollant som lägger till datorn i domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-220">Specifies the name of a domain controller that adds the computer to the domain.</span></span> <span data-ttu-id="dde7c-221">Ange namnet i DomainName\ComputerName-format.</span><span class="sxs-lookup"><span data-stu-id="dde7c-221">Enter the name in DomainName\ComputerName format.</span></span> <span data-ttu-id="dde7c-222">Ingen domänkontrollant har angetts som standard.</span><span class="sxs-lookup"><span data-stu-id="dde7c-222">By default, no domain controller is specified.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-223">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="dde7c-223">-UnjoinDomainCredential</span></span>

<span data-ttu-id="dde7c-224">Anger ett användar konto som har behörighet att ta bort datorerna från deras aktuella domäner.</span><span class="sxs-lookup"><span data-stu-id="dde7c-224">Specifies a user account that has permission to remove the computers from their current domains.</span></span> <span data-ttu-id="dde7c-225">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="dde7c-225">The default is the current user.</span></span>

<span data-ttu-id="dde7c-226">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dde7c-226">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="dde7c-227">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="dde7c-227">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="dde7c-228">Använd den här parametern när du flyttar datorer till en annan domän.</span><span class="sxs-lookup"><span data-stu-id="dde7c-228">Use this parameter when you are moving computers to a different domain.</span></span> <span data-ttu-id="dde7c-229">Om du vill ange ett användar konto som har behörighet att ansluta till den nya domänen använder du parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="dde7c-229">To specify a user account that has permission to join the new domain, use the **Credential** parameter.</span></span> <span data-ttu-id="dde7c-230">Om du vill ange ett användar konto som har behörighet att ansluta till en fjärrdator använder du parametern **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="dde7c-230">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="dde7c-231">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dde7c-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-232">-Osäkra</span><span class="sxs-lookup"><span data-stu-id="dde7c-232">-Unsecure</span></span>

<span data-ttu-id="dde7c-233">Utför en oskyddad anslutning till den angivna domänen.</span><span class="sxs-lookup"><span data-stu-id="dde7c-233">Performs an unsecure join to the specified domain.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-234">-WorkgroupName</span><span class="sxs-lookup"><span data-stu-id="dde7c-234">-WorkgroupName</span></span>

<span data-ttu-id="dde7c-235">Anger namnet på en arbets grupp som datorerna läggs till i.</span><span class="sxs-lookup"><span data-stu-id="dde7c-235">Specifies the name of a workgroup to which the computers are added.</span></span> <span data-ttu-id="dde7c-236">Standardvärdet är "WORKGROUP".</span><span class="sxs-lookup"><span data-stu-id="dde7c-236">The default value is "WORKGROUP".</span></span>

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-237">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dde7c-237">-Confirm</span></span>

<span data-ttu-id="dde7c-238">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dde7c-238">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-239">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dde7c-239">-WhatIf</span></span>

<span data-ttu-id="dde7c-240">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="dde7c-240">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="dde7c-241">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="dde7c-241">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dde7c-242">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dde7c-242">CommonParameters</span></span>

<span data-ttu-id="dde7c-243">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dde7c-243">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dde7c-244">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="dde7c-244">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="dde7c-245">INDATA</span><span class="sxs-lookup"><span data-stu-id="dde7c-245">INPUTS</span></span>

### <span data-ttu-id="dde7c-246">System. String</span><span class="sxs-lookup"><span data-stu-id="dde7c-246">System.String</span></span>

<span data-ttu-id="dde7c-247">Du kan skicka vidare dator namn och nya namn till- `Add-Computer` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dde7c-247">You can pipe computer names and new names to the `Add-Computer` Cmdlet.</span></span>

## <span data-ttu-id="dde7c-248">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dde7c-248">OUTPUTS</span></span>

### <span data-ttu-id="dde7c-249">Microsoft. PowerShell. commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="dde7c-249">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="dde7c-250">När du använder parametern **Passthru** `Add-Computer` returnerar ett **ComputerChangeInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="dde7c-250">When you use the **PassThru** parameter, `Add-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="dde7c-251">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="dde7c-251">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="dde7c-252">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dde7c-252">NOTES</span></span>

- <span data-ttu-id="dde7c-253">I Windows PowerShell 2,0 Miss lyckas **Server** parametern för `Add-Computer` trots att servern finns.</span><span class="sxs-lookup"><span data-stu-id="dde7c-253">In Windows PowerShell 2.0, the **Server** parameter of `Add-Computer` fails even when the server is present.</span></span> <span data-ttu-id="dde7c-254">I Windows PowerShell 3,0 ändras implementeringen av **Server** parametern så att den fungerar på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="dde7c-254">In Windows PowerShell 3.0, the implementation of the **Server** parameter is changed so that it works reliably.</span></span>

## <span data-ttu-id="dde7c-255">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dde7c-255">RELATED LINKS</span></span>

[<span data-ttu-id="dde7c-256">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="dde7c-256">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="dde7c-257">Ta bort dator</span><span class="sxs-lookup"><span data-stu-id="dde7c-257">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="dde7c-258">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="dde7c-258">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="dde7c-259">Byt namn – dator</span><span class="sxs-lookup"><span data-stu-id="dde7c-259">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="dde7c-260">Återställa-dator</span><span class="sxs-lookup"><span data-stu-id="dde7c-260">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="dde7c-261">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="dde7c-261">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="dde7c-262">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="dde7c-262">Test-Connection</span></span>](Test-Connection.md)
