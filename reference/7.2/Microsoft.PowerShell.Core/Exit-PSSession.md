---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b76f7dc87105318285c930b6cd2ae4ae10c2b0e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709228"
---
# <span data-ttu-id="27a5e-102">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="27a5e-102">Exit-PSSession</span></span>

## <span data-ttu-id="27a5e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="27a5e-103">SYNOPSIS</span></span>
<span data-ttu-id="27a5e-104">Avslutar en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="27a5e-104">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="27a5e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="27a5e-105">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="27a5e-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="27a5e-106">DESCRIPTION</span></span>

<span data-ttu-id="27a5e-107">Cmdleten **exit-PSSession** avslutar interaktiva sessioner som du startade med hjälp av Enter-PSSession-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="27a5e-107">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="27a5e-108">Du kan också använda nyckelordet **exit** för att avsluta en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="27a5e-108">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="27a5e-109">Resultatet är detsamma som att använda **exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="27a5e-109">The effect is the same as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="27a5e-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="27a5e-110">EXAMPLES</span></span>

### <span data-ttu-id="27a5e-111">Exempel 1: starta och stoppa en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="27a5e-111">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="27a5e-112">Kommandona startar och stoppar sedan en interaktiv session med Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="27a5e-112">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="27a5e-113">Exempel 2: starta och stoppa en interaktiv session med hjälp av ett PSSession-objekt</span><span class="sxs-lookup"><span data-stu-id="27a5e-113">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="27a5e-114">Kommandona startar och stoppar en interaktiv session med Server01-datorn som använder en PowerShell-session (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="27a5e-114">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="27a5e-115">Eftersom den interaktiva sessionen startades med hjälp av en PowerShell-session är **PSSession** fortfarande tillgängligt när den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="27a5e-115">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="27a5e-116">Om du använder parametern *computername* kan du **Ange-PSSession** för att skapa en tillfällig session som stängs när den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="27a5e-116">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="27a5e-117">Det första kommandot använder cmdleten New-PSSession för att skapa en **PSSession** på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="27a5e-117">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="27a5e-118">Kommandot sparar **PSSession** i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="27a5e-118">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="27a5e-119">Det andra kommandot använder **RETUR-PSSession** för att starta en interaktiv session med hjälp av **PSSession** i $s.</span><span class="sxs-lookup"><span data-stu-id="27a5e-119">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="27a5e-120">Det tredje kommandot använder **exit-PSSession** för att stoppa den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="27a5e-120">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="27a5e-121">Det sista kommandot visar **PSSession** i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="27a5e-121">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="27a5e-122">Egenskapen **State** visar att **PSSession** fortfarande är öppen och tillgänglig för användning.</span><span class="sxs-lookup"><span data-stu-id="27a5e-122">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="27a5e-123">Exempel 3: Använd nyckelordet Exit för att stoppa en session</span><span class="sxs-lookup"><span data-stu-id="27a5e-123">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="27a5e-124">I det här exemplet används nyckelordet **exit** för att stoppa en interaktiv session som har startats med hjälp av **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="27a5e-124">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession**.</span></span>
<span data-ttu-id="27a5e-125">Nyckelordet **exit** har samma resultat som när du använder **exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="27a5e-125">The **Exit** keyword has the same effect as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="27a5e-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="27a5e-126">PARAMETERS</span></span>

### <span data-ttu-id="27a5e-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27a5e-127">CommonParameters</span></span>

<span data-ttu-id="27a5e-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27a5e-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27a5e-129">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="27a5e-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27a5e-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="27a5e-130">INPUTS</span></span>

### <span data-ttu-id="27a5e-131">Inga</span><span class="sxs-lookup"><span data-stu-id="27a5e-131">None</span></span>

<span data-ttu-id="27a5e-132">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27a5e-132">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="27a5e-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="27a5e-133">OUTPUTS</span></span>

### <span data-ttu-id="27a5e-134">Inga</span><span class="sxs-lookup"><span data-stu-id="27a5e-134">None</span></span>

<span data-ttu-id="27a5e-135">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="27a5e-135">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="27a5e-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="27a5e-136">NOTES</span></span>

* <span data-ttu-id="27a5e-137">Denna cmdlet tar bara med de gemensamma parametrarna.</span><span class="sxs-lookup"><span data-stu-id="27a5e-137">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="27a5e-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="27a5e-138">RELATED LINKS</span></span>

[<span data-ttu-id="27a5e-139">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="27a5e-139">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="27a5e-140">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="27a5e-140">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="27a5e-141">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="27a5e-141">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="27a5e-142">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="27a5e-142">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="27a5e-143">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="27a5e-143">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="27a5e-144">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="27a5e-144">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="27a5e-145">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="27a5e-145">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="27a5e-146">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="27a5e-146">Remove-PSSession</span></span>](Remove-PSSession.md)

