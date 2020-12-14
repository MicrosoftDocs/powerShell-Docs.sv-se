---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: cd0e2b62464a4c34278d42b833a669c6c28e377f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710446"
---
# <span data-ttu-id="dbe67-102">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-102">Remove-PSSession</span></span>

## <span data-ttu-id="dbe67-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dbe67-103">SYNOPSIS</span></span>
<span data-ttu-id="dbe67-104">Stänger en eller flera PowerShell-sessioner (PSSessions).</span><span class="sxs-lookup"><span data-stu-id="dbe67-104">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="dbe67-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dbe67-105">SYNTAX</span></span>

### <span data-ttu-id="dbe67-106">ID (standard)</span><span class="sxs-lookup"><span data-stu-id="dbe67-106">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dbe67-107">Session</span><span class="sxs-lookup"><span data-stu-id="dbe67-107">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dbe67-108">Hålla</span><span class="sxs-lookup"><span data-stu-id="dbe67-108">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dbe67-109">VMId</span><span class="sxs-lookup"><span data-stu-id="dbe67-109">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dbe67-110">VMName</span><span class="sxs-lookup"><span data-stu-id="dbe67-110">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dbe67-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="dbe67-111">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dbe67-112">Namn</span><span class="sxs-lookup"><span data-stu-id="dbe67-112">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dbe67-113">ComputerName</span><span class="sxs-lookup"><span data-stu-id="dbe67-113">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dbe67-114">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dbe67-114">DESCRIPTION</span></span>

<span data-ttu-id="dbe67-115">Cmdlet **: en Remove-PSSession** stänger PowerShell-sessioner (**PSSessions**) i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-115">The **Remove-PSSession** cmdlet closes PowerShell sessions (**PSSessions**) in the current session.</span></span>
<span data-ttu-id="dbe67-116">Alla kommandon som körs i **PSSessions** avslutas, avslutar **PSSession** och frigör de resurser som **PSSession** använde.</span><span class="sxs-lookup"><span data-stu-id="dbe67-116">It stops any commands that are running in the **PSSessions**, ends the **PSSession**, and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="dbe67-117">Om **PSSession** är ansluten till en fjärrdator, stänger denna cmdlet också anslutningen mellan lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="dbe67-117">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="dbe67-118">Om du vill ta bort en **PSSession** anger du *namnet*, *computername*, *ID* eller *InstanceID* för sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-118">To remove a **PSSession**, enter the *Name*, *ComputerName*, *ID*, or *InstanceID* of the session.</span></span>

<span data-ttu-id="dbe67-119">Om du har sparat *PSSession* i en variabel finns objektet kvar i variabeln, men *PSSession* är stängt.</span><span class="sxs-lookup"><span data-stu-id="dbe67-119">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="dbe67-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dbe67-120">EXAMPLES</span></span>

### <span data-ttu-id="dbe67-121">Exempel 1: ta bort sessioner med ID: n</span><span class="sxs-lookup"><span data-stu-id="dbe67-121">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="dbe67-122">Det här kommandot tar bort **PSSessions** med ID 1 och 2.</span><span class="sxs-lookup"><span data-stu-id="dbe67-122">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="dbe67-123">Exempel 2: ta bort alla sessioner i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="dbe67-123">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="dbe67-124">De här kommandona tar bort alla **PSSessions** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-124">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="dbe67-125">Även om de tre kommando formaten ser olika ut, har de samma resultat.</span><span class="sxs-lookup"><span data-stu-id="dbe67-125">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="dbe67-126">Exempel 3: Stäng sessioner med hjälp av namn</span><span class="sxs-lookup"><span data-stu-id="dbe67-126">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="dbe67-127">Kommandona stänger **PSSessions** som är anslutna till datorer som har namn som börjar med serv.</span><span class="sxs-lookup"><span data-stu-id="dbe67-127">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="dbe67-128">Exempel 4: Stäng sessioner som är anslutna till en port</span><span class="sxs-lookup"><span data-stu-id="dbe67-128">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="dbe67-129">Detta kommando stänger de **PSSessions** som är anslutna till port 90.</span><span class="sxs-lookup"><span data-stu-id="dbe67-129">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="dbe67-130">Du kan använda det här kommando formatet för att identifiera **PSSessions** efter andra egenskaper än *computername*, *Name*, *InstanceID* och *ID*.</span><span class="sxs-lookup"><span data-stu-id="dbe67-130">You can use this command format to identify **PSSessions** by properties other than *ComputerName*, *Name*, *InstanceID*, and *ID*.</span></span>

### <span data-ttu-id="dbe67-131">Exempel 5: Stäng en session baserat på instans-ID</span><span class="sxs-lookup"><span data-stu-id="dbe67-131">Example 5: Close a session based on instance ID</span></span>

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

<span data-ttu-id="dbe67-132">Kommandona visar hur du stänger en **PSSession** baserat på dess instans-ID eller **RemoteRunspaceID**.</span><span class="sxs-lookup"><span data-stu-id="dbe67-132">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID**.</span></span>

<span data-ttu-id="dbe67-133">Det första kommandot använder **Get-PSSession** -cmdlet: en för att hämta **PSSessions** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-133">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="dbe67-134">Den använder en pipeline-operator (|) för att skicka **PSSessions** till Format-Table-cmdlet, som formaterar deras **computername** -och **InstanceID** -egenskaper i en tabell.</span><span class="sxs-lookup"><span data-stu-id="dbe67-134">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="dbe67-135">Parametern *AutoSize* komprimerar kolumnerna för visning.</span><span class="sxs-lookup"><span data-stu-id="dbe67-135">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="dbe67-136">Från den resulterande visningen kan du identifiera **PSSession** som ska stängas och kopiera och klistra in *InstanceID* för **PSSession** i det andra kommandot.</span><span class="sxs-lookup"><span data-stu-id="dbe67-136">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="dbe67-137">Det andra kommandot använder cmdleten **Remove-PSSession** för att ta bort *PSSession* med angivet instans-ID.</span><span class="sxs-lookup"><span data-stu-id="dbe67-137">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="dbe67-138">Exempel 6: skapa en funktion som tar bort alla sessioner i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="dbe67-138">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="dbe67-139">Den här funktionen tar bort alla **PSSessions** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-139">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="dbe67-140">När du har lagt till den här funktionen i din PowerShell-profil, för att ta bort alla sessioner, skriver du `EndPSS` .</span><span class="sxs-lookup"><span data-stu-id="dbe67-140">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="dbe67-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dbe67-141">PARAMETERS</span></span>

### <span data-ttu-id="dbe67-142">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="dbe67-142">-ComputerName</span></span>

<span data-ttu-id="dbe67-143">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="dbe67-143">Specifies an array of names of computers.</span></span>
<span data-ttu-id="dbe67-144">Denna cmdlet stänger de **PSSessions** som är anslutna till de angivna datorerna.</span><span class="sxs-lookup"><span data-stu-id="dbe67-144">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="dbe67-145">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="dbe67-145">Wildcard characters are permitted.</span></span>

<span data-ttu-id="dbe67-146">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="dbe67-146">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="dbe67-147">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="dbe67-147">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="dbe67-148">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="dbe67-148">-ContainerId</span></span>

<span data-ttu-id="dbe67-149">Anger en matris med ID: n för behållare.</span><span class="sxs-lookup"><span data-stu-id="dbe67-149">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="dbe67-150">Den här cmdleten tar bort sessioner för var och en av de angivna behållarna.</span><span class="sxs-lookup"><span data-stu-id="dbe67-150">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="dbe67-151">Använd `docker ps` kommandot för att hämta en lista över behållar-ID: n.</span><span class="sxs-lookup"><span data-stu-id="dbe67-151">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="dbe67-152">Mer information finns i hjälpen för kommandot [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="dbe67-152">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dbe67-153">-ID</span><span class="sxs-lookup"><span data-stu-id="dbe67-153">-Id</span></span>

<span data-ttu-id="dbe67-154">Anger en matris med ID: n för sessioner.</span><span class="sxs-lookup"><span data-stu-id="dbe67-154">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="dbe67-155">Denna cmdlet stänger *PSSessions* med de angivna ID: na.</span><span class="sxs-lookup"><span data-stu-id="dbe67-155">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="dbe67-156">Skriv ett eller flera ID: n, avgränsade med kommatecken eller Använd intervall operatorn (..) för att ange ett intervall med ID: n.</span><span class="sxs-lookup"><span data-stu-id="dbe67-156">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="dbe67-157">Ett ID är ett heltal som unikt identifierar **PSSession** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-157">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="dbe67-158">Det är enklare att komma ihåg och skriva än *InstanceID*, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-158">It is easier to remember and type than the *InstanceId*, but it is unique only in the current session.</span></span>
<span data-ttu-id="dbe67-159">Om du vill hitta ID: t för en **PSSession** kör du cmdleten Get-PSSession utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="dbe67-159">To find the ID of a **PSSession**, run the Get-PSSession cmdlet without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dbe67-160">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="dbe67-160">-InstanceId</span></span>

<span data-ttu-id="dbe67-161">Anger en matris med instans-ID: n.</span><span class="sxs-lookup"><span data-stu-id="dbe67-161">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="dbe67-162">Denna cmdlet stänger den **PSSessions** som har de angivna instans-ID: na.</span><span class="sxs-lookup"><span data-stu-id="dbe67-162">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="dbe67-163">Instans-ID är ett GUID som unikt identifierar en **PSSession** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-163">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="dbe67-164">Instans-ID är unikt, även om du har flera sessioner som körs på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="dbe67-164">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="dbe67-165">Instans-ID: t lagras i egenskapen **InstanceID** för objektet som representerar en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="dbe67-165">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession**.</span></span>
<span data-ttu-id="dbe67-166">Om du vill hitta **InstanceID** för **PSSessions** i den aktuella sessionen skriver du `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="dbe67-166">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dbe67-167">-Name</span><span class="sxs-lookup"><span data-stu-id="dbe67-167">-Name</span></span>

<span data-ttu-id="dbe67-168">Anger en matris med användarvänliga namn på sessioner.</span><span class="sxs-lookup"><span data-stu-id="dbe67-168">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="dbe67-169">Denna cmdlet stänger den **PSSessions** som har angivna egna namn.</span><span class="sxs-lookup"><span data-stu-id="dbe67-169">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="dbe67-170">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="dbe67-170">Wildcard characters are permitted.</span></span>

<span data-ttu-id="dbe67-171">Eftersom det egna namnet på en **PSSession** kanske inte är unikt, när du använder parametern *Name* , bör du även överväga att använda parametern *whatIf* eller *Confirm* i kommandot **Remove-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="dbe67-171">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="dbe67-172">– Session</span><span class="sxs-lookup"><span data-stu-id="dbe67-172">-Session</span></span>

<span data-ttu-id="dbe67-173">Anger session-objekten för den **PSSessions** som ska stängas.</span><span class="sxs-lookup"><span data-stu-id="dbe67-173">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="dbe67-174">Ange en variabel som innehåller **PSSessions** eller ett kommando som skapar eller hämtar **PSSessions**, till exempel ett New-PSSession-eller **Get-PSSession-** kommando.</span><span class="sxs-lookup"><span data-stu-id="dbe67-174">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions**, such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="dbe67-175">Du kan också skicka ett eller flera sessionsobjekt till **Remove-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="dbe67-175">You can also pipe one or more session objects to **Remove-PSSession**.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dbe67-176">-VMId</span><span class="sxs-lookup"><span data-stu-id="dbe67-176">-VMId</span></span>

<span data-ttu-id="dbe67-177">Anger en matris med ID för virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="dbe67-177">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="dbe67-178">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="dbe67-178">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="dbe67-179">Använd följande kommando för att se de virtuella datorer som är tillgängliga för dig:</span><span class="sxs-lookup"><span data-stu-id="dbe67-179">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dbe67-180">– VMName</span><span class="sxs-lookup"><span data-stu-id="dbe67-180">-VMName</span></span>

<span data-ttu-id="dbe67-181">Anger en matris med namn på virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="dbe67-181">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="dbe67-182">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="dbe67-182">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="dbe67-183">Använd cmdleten **Get-VM** för att se de virtuella datorer som är tillgängliga för dig.</span><span class="sxs-lookup"><span data-stu-id="dbe67-183">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dbe67-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dbe67-184">-Confirm</span></span>

<span data-ttu-id="dbe67-185">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dbe67-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dbe67-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dbe67-186">-WhatIf</span></span>

<span data-ttu-id="dbe67-187">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="dbe67-187">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="dbe67-188">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="dbe67-188">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dbe67-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dbe67-189">CommonParameters</span></span>

<span data-ttu-id="dbe67-190">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dbe67-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dbe67-191">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dbe67-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dbe67-192">INDATA</span><span class="sxs-lookup"><span data-stu-id="dbe67-192">INPUTS</span></span>

### <span data-ttu-id="dbe67-193">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-193">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="dbe67-194">Du kan skicka vidare ett sessionsobjekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbe67-194">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="dbe67-195">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dbe67-195">OUTPUTS</span></span>

### <span data-ttu-id="dbe67-196">Inga</span><span class="sxs-lookup"><span data-stu-id="dbe67-196">None</span></span>

<span data-ttu-id="dbe67-197">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="dbe67-197">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="dbe67-198">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dbe67-198">NOTES</span></span>

* <span data-ttu-id="dbe67-199">Parametern *ID* är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="dbe67-199">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="dbe67-200">Om du vill ta bort alla **PSSessions** i den aktuella sessionen skriver du `Get-PSSession | Remove-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="dbe67-200">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="dbe67-201">En **PSSession** använder en permanent anslutning till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="dbe67-201">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="dbe67-202">Skapa en **PSSession** för att köra en serie kommandon som delar data.</span><span class="sxs-lookup"><span data-stu-id="dbe67-202">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="dbe67-203">För mer information ange `Get-Help about_PSSessions`.</span><span class="sxs-lookup"><span data-stu-id="dbe67-203">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="dbe67-204">**PSSessions** är bara aktuella för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dbe67-204">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="dbe67-205">När du avslutar en session tvingas **PSSessions** som du skapade i sessionen att avslutas.</span><span class="sxs-lookup"><span data-stu-id="dbe67-205">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="dbe67-206">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dbe67-206">RELATED LINKS</span></span>

[<span data-ttu-id="dbe67-207">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-207">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="dbe67-208">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-208">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="dbe67-209">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-209">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="dbe67-210">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-210">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="dbe67-211">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-211">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="dbe67-212">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="dbe67-212">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="dbe67-213">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-213">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="dbe67-214">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="dbe67-214">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="dbe67-215">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="dbe67-215">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="dbe67-216">about_Remote</span><span class="sxs-lookup"><span data-stu-id="dbe67-216">about_Remote</span></span>](About/about_Remote.md)

