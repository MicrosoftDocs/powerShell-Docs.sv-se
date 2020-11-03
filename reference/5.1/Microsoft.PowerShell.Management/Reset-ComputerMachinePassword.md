---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Reset-ComputerMachinePassword
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265431"
---
# <span data-ttu-id="5e02e-103">Reset-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="5e02e-103">Reset-ComputerMachinePassword</span></span>

## <span data-ttu-id="5e02e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5e02e-104">SYNOPSIS</span></span>
<span data-ttu-id="5e02e-105">Återställer dator kontots lösen ord för datorn.</span><span class="sxs-lookup"><span data-stu-id="5e02e-105">Resets the machine account password for the computer.</span></span>

## <span data-ttu-id="5e02e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5e02e-106">SYNTAX</span></span>

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5e02e-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5e02e-107">DESCRIPTION</span></span>
<span data-ttu-id="5e02e-108">Cmdleten **Reset-ComputerMachinePassword** ändrar lösen ordet för det dator konto som datorerna använder för att autentisera till domän kontrol Lanterna i domänen.</span><span class="sxs-lookup"><span data-stu-id="5e02e-108">The **Reset-ComputerMachinePassword** cmdlet changes the computer account password that the computers use to authenticate to the domain controllers in the domain.</span></span>
<span data-ttu-id="5e02e-109">Du kan använda den för att återställa lösen ordet för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5e02e-109">You can use it to reset the password of the local computer.</span></span>

## <span data-ttu-id="5e02e-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5e02e-110">EXAMPLES</span></span>

### <span data-ttu-id="5e02e-111">Exempel 1: Återställ lösen ordet för den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="5e02e-111">Example 1: Reset the password for the local computer</span></span>

```
PS C:\> Reset-ComputerMachinePassword
```

<span data-ttu-id="5e02e-112">Det här kommandot återställer dator lösen ordet för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5e02e-112">This command resets the computer password for the local computer.</span></span>
<span data-ttu-id="5e02e-113">Kommandot körs med autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="5e02e-113">The command runs with the credentials of the current user.</span></span>

### <span data-ttu-id="5e02e-114">Exempel 2: återställa lösen ordet för den lokala datorn med hjälp av en angiven domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="5e02e-114">Example 2: Reset the password for the local computer by using a specified domain controller</span></span>

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

<span data-ttu-id="5e02e-115">Det här kommandot återställer dator lösen ordet för den lokala datorn med hjälp av DC01-domänkontrollanten.</span><span class="sxs-lookup"><span data-stu-id="5e02e-115">This command resets the computer password of the local computer by using the DC01 domain controller.</span></span>
<span data-ttu-id="5e02e-116">Den använder parametern *Credential* för att ange ett användar konto som har behörighet att återställa ett dator lösen ord i domänen.</span><span class="sxs-lookup"><span data-stu-id="5e02e-116">It uses the *Credential* parameter to specify a user account that has permission to reset a computer password in the domain.</span></span>

### <span data-ttu-id="5e02e-117">Exempel 3: återställa lösen ordet på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="5e02e-117">Example 3: Reset the password on a remote computer</span></span>

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

<span data-ttu-id="5e02e-118">Det här kommandot använder cmdleten Invoke-Command för att köra ett **Reset-ComputerMachinePassword-** kommando på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="5e02e-118">This command uses the Invoke-Command cmdlet to run a **Reset-ComputerMachinePassword** command on the Server01 remote computer.</span></span>

<span data-ttu-id="5e02e-119">Mer information om fjärrkommandon i Windows PowerShell finns about_Remote och **Invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="5e02e-119">For more information about remote commands in Windows PowerShell, see about_Remote and **Invoke-Command**.</span></span>

## <span data-ttu-id="5e02e-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5e02e-120">PARAMETERS</span></span>

### <span data-ttu-id="5e02e-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="5e02e-121">-Credential</span></span>
<span data-ttu-id="5e02e-122">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5e02e-122">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="5e02e-123">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="5e02e-123">The default is the current user.</span></span>

<span data-ttu-id="5e02e-124">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett som genereras av Get-Credential cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e02e-124">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="5e02e-125">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e02e-125">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="5e02e-126">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5e02e-126">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5e02e-127">-Server</span><span class="sxs-lookup"><span data-stu-id="5e02e-127">-Server</span></span>
<span data-ttu-id="5e02e-128">Anger namnet på en domänkontrollant som ska användas när denna cmdlet anger lösen ordet för dator kontot.</span><span class="sxs-lookup"><span data-stu-id="5e02e-128">Specifies the name of a domain controller to use when this cmdlet sets the computer account password.</span></span>

<span data-ttu-id="5e02e-129">Den här parametern är valfri.</span><span class="sxs-lookup"><span data-stu-id="5e02e-129">This parameter is optional.</span></span>
<span data-ttu-id="5e02e-130">Om du utelämnar den här parametern väljs en domänkontrollant för att betjäna kommandot.</span><span class="sxs-lookup"><span data-stu-id="5e02e-130">If you omit this parameter, a domain controller is chosen to service the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e02e-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5e02e-131">-Confirm</span></span>
<span data-ttu-id="5e02e-132">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e02e-132">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5e02e-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5e02e-133">-WhatIf</span></span>
<span data-ttu-id="5e02e-134">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5e02e-134">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5e02e-135">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5e02e-135">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5e02e-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e02e-136">CommonParameters</span></span>
<span data-ttu-id="5e02e-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5e02e-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e02e-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5e02e-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e02e-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="5e02e-139">INPUTS</span></span>

### <span data-ttu-id="5e02e-140">Inget</span><span class="sxs-lookup"><span data-stu-id="5e02e-140">None</span></span>
<span data-ttu-id="5e02e-141">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e02e-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5e02e-142">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5e02e-142">OUTPUTS</span></span>

### <span data-ttu-id="5e02e-143">Inget</span><span class="sxs-lookup"><span data-stu-id="5e02e-143">None</span></span>
<span data-ttu-id="5e02e-144">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5e02e-144">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5e02e-145">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5e02e-145">NOTES</span></span>

## <span data-ttu-id="5e02e-146">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5e02e-146">RELATED LINKS</span></span>

## <span data-ttu-id="5e02e-147">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5e02e-147">RELATED LINKS</span></span>
