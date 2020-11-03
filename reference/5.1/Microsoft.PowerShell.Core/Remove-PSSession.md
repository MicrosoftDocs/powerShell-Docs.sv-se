---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: e613b8a0250b966adc832f4e61c637c41d63f19f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264177"
---
# <span data-ttu-id="71bc0-103">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-103">Remove-PSSession</span></span>

## <span data-ttu-id="71bc0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="71bc0-104">SYNOPSIS</span></span>
<span data-ttu-id="71bc0-105">Stänger en eller flera PowerShell-sessioner (PSSessions).</span><span class="sxs-lookup"><span data-stu-id="71bc0-105">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="71bc0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="71bc0-106">SYNTAX</span></span>

### <span data-ttu-id="71bc0-107">ID (standard)</span><span class="sxs-lookup"><span data-stu-id="71bc0-107">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71bc0-108">Session</span><span class="sxs-lookup"><span data-stu-id="71bc0-108">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71bc0-109">Hålla</span><span class="sxs-lookup"><span data-stu-id="71bc0-109">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71bc0-110">VMId</span><span class="sxs-lookup"><span data-stu-id="71bc0-110">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71bc0-111">VMName</span><span class="sxs-lookup"><span data-stu-id="71bc0-111">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71bc0-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="71bc0-112">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71bc0-113">Name</span><span class="sxs-lookup"><span data-stu-id="71bc0-113">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71bc0-114">ComputerName</span><span class="sxs-lookup"><span data-stu-id="71bc0-114">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="71bc0-115">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="71bc0-115">DESCRIPTION</span></span>

<span data-ttu-id="71bc0-116">Cmdlet **: en Remove-PSSession** stänger PowerShell-sessioner ( **PSSessions** ) i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-116">The **Remove-PSSession** cmdlet closes PowerShell sessions ( **PSSessions** ) in the current session.</span></span>
<span data-ttu-id="71bc0-117">Alla kommandon som körs i **PSSessions** avslutas, avslutar **PSSession** och frigör de resurser som **PSSession** använde.</span><span class="sxs-lookup"><span data-stu-id="71bc0-117">It stops any commands that are running in the **PSSessions** , ends the **PSSession** , and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="71bc0-118">Om **PSSession** är ansluten till en fjärrdator, stänger denna cmdlet också anslutningen mellan lokala och fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="71bc0-118">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="71bc0-119">Om du vill ta bort en **PSSession** anger du *namnet* , *computername* , *ID* eller *InstanceID* för sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-119">To remove a **PSSession** , enter the *Name* , *ComputerName* , *ID* , or *InstanceID* of the session.</span></span>

<span data-ttu-id="71bc0-120">Om du har sparat *PSSession* i en variabel finns objektet kvar i variabeln, men *PSSession* är stängt.</span><span class="sxs-lookup"><span data-stu-id="71bc0-120">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="71bc0-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="71bc0-121">EXAMPLES</span></span>

### <span data-ttu-id="71bc0-122">Exempel 1: ta bort sessioner med ID: n</span><span class="sxs-lookup"><span data-stu-id="71bc0-122">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="71bc0-123">Det här kommandot tar bort **PSSessions** med ID 1 och 2.</span><span class="sxs-lookup"><span data-stu-id="71bc0-123">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="71bc0-124">Exempel 2: ta bort alla sessioner i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="71bc0-124">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="71bc0-125">De här kommandona tar bort alla **PSSessions** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-125">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="71bc0-126">Även om de tre kommando formaten ser olika ut, har de samma resultat.</span><span class="sxs-lookup"><span data-stu-id="71bc0-126">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="71bc0-127">Exempel 3: Stäng sessioner med hjälp av namn</span><span class="sxs-lookup"><span data-stu-id="71bc0-127">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="71bc0-128">Kommandona stänger **PSSessions** som är anslutna till datorer som har namn som börjar med serv.</span><span class="sxs-lookup"><span data-stu-id="71bc0-128">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="71bc0-129">Exempel 4: Stäng sessioner som är anslutna till en port</span><span class="sxs-lookup"><span data-stu-id="71bc0-129">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="71bc0-130">Detta kommando stänger de **PSSessions** som är anslutna till port 90.</span><span class="sxs-lookup"><span data-stu-id="71bc0-130">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="71bc0-131">Du kan använda det här kommando formatet för att identifiera **PSSessions** efter andra egenskaper än *computername* , *Name* , *InstanceID* och *ID*.</span><span class="sxs-lookup"><span data-stu-id="71bc0-131">You can use this command format to identify **PSSessions** by properties other than *ComputerName* , *Name* , *InstanceID* , and *ID*.</span></span>

### <span data-ttu-id="71bc0-132">Exempel 5: Stäng en session baserat på instans-ID</span><span class="sxs-lookup"><span data-stu-id="71bc0-132">Example 5: Close a session based on instance ID</span></span>

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

<span data-ttu-id="71bc0-133">Kommandona visar hur du stänger en **PSSession** baserat på dess instans-ID eller **RemoteRunspaceID**.</span><span class="sxs-lookup"><span data-stu-id="71bc0-133">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID**.</span></span>

<span data-ttu-id="71bc0-134">Det första kommandot använder **Get-PSSession** -cmdlet: en för att hämta **PSSessions** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-134">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="71bc0-135">Den använder en pipeline-operator (|) för att skicka **PSSessions** till Format-Table-cmdlet, som formaterar deras **computername** -och **InstanceID** -egenskaper i en tabell.</span><span class="sxs-lookup"><span data-stu-id="71bc0-135">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="71bc0-136">Parametern *AutoSize* komprimerar kolumnerna för visning.</span><span class="sxs-lookup"><span data-stu-id="71bc0-136">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="71bc0-137">Från den resulterande visningen kan du identifiera **PSSession** som ska stängas och kopiera och klistra in *InstanceID* för **PSSession** i det andra kommandot.</span><span class="sxs-lookup"><span data-stu-id="71bc0-137">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="71bc0-138">Det andra kommandot använder cmdleten **Remove-PSSession** för att ta bort *PSSession* med angivet instans-ID.</span><span class="sxs-lookup"><span data-stu-id="71bc0-138">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="71bc0-139">Exempel 6: skapa en funktion som tar bort alla sessioner i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="71bc0-139">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="71bc0-140">Den här funktionen tar bort alla **PSSessions** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-140">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="71bc0-141">När du har lagt till den här funktionen i din PowerShell-profil, för att ta bort alla sessioner, skriver du `EndPSS` .</span><span class="sxs-lookup"><span data-stu-id="71bc0-141">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="71bc0-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="71bc0-142">PARAMETERS</span></span>

### <span data-ttu-id="71bc0-143">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="71bc0-143">-ComputerName</span></span>

<span data-ttu-id="71bc0-144">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="71bc0-144">Specifies an array of names of computers.</span></span>
<span data-ttu-id="71bc0-145">Denna cmdlet stänger de **PSSessions** som är anslutna till de angivna datorerna.</span><span class="sxs-lookup"><span data-stu-id="71bc0-145">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="71bc0-146">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="71bc0-146">Wildcard characters are permitted.</span></span>

<span data-ttu-id="71bc0-147">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="71bc0-147">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="71bc0-148">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="71bc0-148">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

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

### <span data-ttu-id="71bc0-149">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="71bc0-149">-ContainerId</span></span>

<span data-ttu-id="71bc0-150">Anger en matris med ID: n för behållare.</span><span class="sxs-lookup"><span data-stu-id="71bc0-150">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="71bc0-151">Den här cmdleten tar bort sessioner för var och en av de angivna behållarna.</span><span class="sxs-lookup"><span data-stu-id="71bc0-151">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="71bc0-152">Använd `docker ps` kommandot för att hämta en lista över behållar-ID: n.</span><span class="sxs-lookup"><span data-stu-id="71bc0-152">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="71bc0-153">Mer information finns i hjälpen för kommandot [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/) .</span><span class="sxs-lookup"><span data-stu-id="71bc0-153">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

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

### <span data-ttu-id="71bc0-154">-ID</span><span class="sxs-lookup"><span data-stu-id="71bc0-154">-Id</span></span>

<span data-ttu-id="71bc0-155">Anger en matris med ID: n för sessioner.</span><span class="sxs-lookup"><span data-stu-id="71bc0-155">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="71bc0-156">Denna cmdlet stänger *PSSessions* med de angivna ID: na.</span><span class="sxs-lookup"><span data-stu-id="71bc0-156">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="71bc0-157">Skriv ett eller flera ID: n, avgränsade med kommatecken eller Använd intervall operatorn (..) för att ange ett intervall med ID: n.</span><span class="sxs-lookup"><span data-stu-id="71bc0-157">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="71bc0-158">Ett ID är ett heltal som unikt identifierar **PSSession** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-158">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="71bc0-159">Det är enklare att komma ihåg och skriva än *InstanceID* , men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-159">It is easier to remember and type than the *InstanceId* , but it is unique only in the current session.</span></span>
<span data-ttu-id="71bc0-160">Om du vill hitta ID: t för en **PSSession** kör du cmdleten Get-PSSession utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="71bc0-160">To find the ID of a **PSSession** , run the Get-PSSession cmdlet without parameters.</span></span>

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

### <span data-ttu-id="71bc0-161">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="71bc0-161">-InstanceId</span></span>

<span data-ttu-id="71bc0-162">Anger en matris med instans-ID: n.</span><span class="sxs-lookup"><span data-stu-id="71bc0-162">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="71bc0-163">Denna cmdlet stänger den **PSSessions** som har de angivna instans-ID: na.</span><span class="sxs-lookup"><span data-stu-id="71bc0-163">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="71bc0-164">Instans-ID är ett GUID som unikt identifierar en **PSSession** i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-164">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="71bc0-165">Instans-ID är unikt, även om du har flera sessioner som körs på en enda dator.</span><span class="sxs-lookup"><span data-stu-id="71bc0-165">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="71bc0-166">Instans-ID: t lagras i egenskapen **InstanceID** för objektet som representerar en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="71bc0-166">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession**.</span></span>
<span data-ttu-id="71bc0-167">Om du vill hitta **InstanceID** för **PSSessions** i den aktuella sessionen skriver du `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="71bc0-167">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

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

### <span data-ttu-id="71bc0-168">-Name</span><span class="sxs-lookup"><span data-stu-id="71bc0-168">-Name</span></span>

<span data-ttu-id="71bc0-169">Anger en matris med användarvänliga namn på sessioner.</span><span class="sxs-lookup"><span data-stu-id="71bc0-169">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="71bc0-170">Denna cmdlet stänger den **PSSessions** som har angivna egna namn.</span><span class="sxs-lookup"><span data-stu-id="71bc0-170">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="71bc0-171">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="71bc0-171">Wildcard characters are permitted.</span></span>

<span data-ttu-id="71bc0-172">Eftersom det egna namnet på en **PSSession** kanske inte är unikt, när du använder parametern *Name* , bör du även överväga att använda parametern *whatIf* eller *Confirm* i kommandot **Remove-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="71bc0-172">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

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

### <span data-ttu-id="71bc0-173">– Session</span><span class="sxs-lookup"><span data-stu-id="71bc0-173">-Session</span></span>

<span data-ttu-id="71bc0-174">Anger session-objekten för den **PSSessions** som ska stängas.</span><span class="sxs-lookup"><span data-stu-id="71bc0-174">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="71bc0-175">Ange en variabel som innehåller **PSSessions** eller ett kommando som skapar eller hämtar **PSSessions** , till exempel ett New-PSSession-eller **Get-PSSession-** kommando.</span><span class="sxs-lookup"><span data-stu-id="71bc0-175">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions** , such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="71bc0-176">Du kan också skicka ett eller flera sessionsobjekt till **Remove-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="71bc0-176">You can also pipe one or more session objects to **Remove-PSSession**.</span></span>

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

### <span data-ttu-id="71bc0-177">-VMId</span><span class="sxs-lookup"><span data-stu-id="71bc0-177">-VMId</span></span>

<span data-ttu-id="71bc0-178">Anger en matris med ID för virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="71bc0-178">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="71bc0-179">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="71bc0-179">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="71bc0-180">Använd följande kommando för att se de virtuella datorer som är tillgängliga för dig:</span><span class="sxs-lookup"><span data-stu-id="71bc0-180">To see the virtual machines that are available to you, use the following command:</span></span>

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

### <span data-ttu-id="71bc0-181">– VMName</span><span class="sxs-lookup"><span data-stu-id="71bc0-181">-VMName</span></span>

<span data-ttu-id="71bc0-182">Anger en matris med namn på virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="71bc0-182">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="71bc0-183">Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="71bc0-183">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="71bc0-184">Använd cmdleten **Get-VM** för att se de virtuella datorer som är tillgängliga för dig.</span><span class="sxs-lookup"><span data-stu-id="71bc0-184">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

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

### <span data-ttu-id="71bc0-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="71bc0-185">-Confirm</span></span>

<span data-ttu-id="71bc0-186">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="71bc0-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="71bc0-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="71bc0-187">-WhatIf</span></span>

<span data-ttu-id="71bc0-188">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="71bc0-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="71bc0-189">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="71bc0-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="71bc0-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71bc0-190">CommonParameters</span></span>

<span data-ttu-id="71bc0-191">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="71bc0-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71bc0-192">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="71bc0-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71bc0-193">INDATA</span><span class="sxs-lookup"><span data-stu-id="71bc0-193">INPUTS</span></span>

### <span data-ttu-id="71bc0-194">System. Management. Automation. körnings utrymmen. PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-194">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="71bc0-195">Du kan skicka vidare ett sessionsobjekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="71bc0-195">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="71bc0-196">UTDATA</span><span class="sxs-lookup"><span data-stu-id="71bc0-196">OUTPUTS</span></span>

### <span data-ttu-id="71bc0-197">Inget</span><span class="sxs-lookup"><span data-stu-id="71bc0-197">None</span></span>

<span data-ttu-id="71bc0-198">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="71bc0-198">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="71bc0-199">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="71bc0-199">NOTES</span></span>

* <span data-ttu-id="71bc0-200">Parametern *ID* är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="71bc0-200">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="71bc0-201">Om du vill ta bort alla **PSSessions** i den aktuella sessionen skriver du `Get-PSSession | Remove-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="71bc0-201">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="71bc0-202">En **PSSession** använder en permanent anslutning till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="71bc0-202">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="71bc0-203">Skapa en **PSSession** för att köra en serie kommandon som delar data.</span><span class="sxs-lookup"><span data-stu-id="71bc0-203">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="71bc0-204">För mer information ange `Get-Help about_PSSessions`.</span><span class="sxs-lookup"><span data-stu-id="71bc0-204">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="71bc0-205">**PSSessions** är bara aktuella för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="71bc0-205">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="71bc0-206">När du avslutar en session tvingas **PSSessions** som du skapade i sessionen att avslutas.</span><span class="sxs-lookup"><span data-stu-id="71bc0-206">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="71bc0-207">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="71bc0-207">RELATED LINKS</span></span>

[<span data-ttu-id="71bc0-208">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-208">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="71bc0-209">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-209">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="71bc0-210">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-210">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="71bc0-211">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-211">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="71bc0-212">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-212">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="71bc0-213">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="71bc0-213">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="71bc0-214">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-214">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="71bc0-215">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="71bc0-215">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="71bc0-216">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="71bc0-216">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="71bc0-217">about_Remote</span><span class="sxs-lookup"><span data-stu-id="71bc0-217">about_Remote</span></span>](About/about_Remote.md)
