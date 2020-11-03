---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: f6123bca498d753de1fe284d48f29407c3f8a465
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261639"
---
# <span data-ttu-id="7c50c-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="7c50c-103">Exit-PSSession</span></span>

## <span data-ttu-id="7c50c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7c50c-104">SYNOPSIS</span></span>
<span data-ttu-id="7c50c-105">Avslutar en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="7c50c-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="7c50c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7c50c-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="7c50c-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7c50c-107">DESCRIPTION</span></span>

<span data-ttu-id="7c50c-108">Cmdleten **exit-PSSession** avslutar interaktiva sessioner som du startade med hjälp av Enter-PSSession-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7c50c-108">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="7c50c-109">Du kan också använda nyckelordet **exit** för att avsluta en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="7c50c-109">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="7c50c-110">Resultatet är detsamma som att använda **exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="7c50c-110">The effect is the same as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="7c50c-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7c50c-111">EXAMPLES</span></span>

### <span data-ttu-id="7c50c-112">Exempel 1: starta och stoppa en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="7c50c-112">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="7c50c-113">Kommandona startar och stoppar sedan en interaktiv session med Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="7c50c-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="7c50c-114">Exempel 2: starta och stoppa en interaktiv session med hjälp av ett PSSession-objekt</span><span class="sxs-lookup"><span data-stu-id="7c50c-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="7c50c-115">Kommandona startar och stoppar en interaktiv session med Server01-datorn som använder en PowerShell-session ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="7c50c-115">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session ( **PSSession** ).</span></span>

<span data-ttu-id="7c50c-116">Eftersom den interaktiva sessionen startades med hjälp av en PowerShell-session är **PSSession** fortfarande tillgängligt när den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="7c50c-116">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="7c50c-117">Om du använder parametern *computername* kan du **Ange-PSSession** för att skapa en tillfällig session som stängs när den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="7c50c-117">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="7c50c-118">Det första kommandot använder cmdleten New-PSSession för att skapa en **PSSession** på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="7c50c-118">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="7c50c-119">Kommandot sparar **PSSession** i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="7c50c-119">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="7c50c-120">Det andra kommandot använder **RETUR-PSSession** för att starta en interaktiv session med hjälp av **PSSession** i $s.</span><span class="sxs-lookup"><span data-stu-id="7c50c-120">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="7c50c-121">Det tredje kommandot använder **exit-PSSession** för att stoppa den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="7c50c-121">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="7c50c-122">Det sista kommandot visar **PSSession** i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="7c50c-122">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="7c50c-123">Egenskapen **State** visar att **PSSession** fortfarande är öppen och tillgänglig för användning.</span><span class="sxs-lookup"><span data-stu-id="7c50c-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="7c50c-124">Exempel 3: Använd nyckelordet Exit för att stoppa en session</span><span class="sxs-lookup"><span data-stu-id="7c50c-124">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="7c50c-125">I det här exemplet används nyckelordet **exit** för att stoppa en interaktiv session som har startats med hjälp av **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="7c50c-125">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession**.</span></span>
<span data-ttu-id="7c50c-126">Nyckelordet **exit** har samma resultat som när du använder **exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="7c50c-126">The **Exit** keyword has the same effect as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="7c50c-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7c50c-127">PARAMETERS</span></span>

### <span data-ttu-id="7c50c-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c50c-128">CommonParameters</span></span>

<span data-ttu-id="7c50c-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c50c-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c50c-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7c50c-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c50c-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="7c50c-131">INPUTS</span></span>

### <span data-ttu-id="7c50c-132">Inget</span><span class="sxs-lookup"><span data-stu-id="7c50c-132">None</span></span>

<span data-ttu-id="7c50c-133">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c50c-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="7c50c-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7c50c-134">OUTPUTS</span></span>

### <span data-ttu-id="7c50c-135">Inget</span><span class="sxs-lookup"><span data-stu-id="7c50c-135">None</span></span>

<span data-ttu-id="7c50c-136">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7c50c-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="7c50c-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7c50c-137">NOTES</span></span>

* <span data-ttu-id="7c50c-138">Denna cmdlet tar bara med de gemensamma parametrarna.</span><span class="sxs-lookup"><span data-stu-id="7c50c-138">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="7c50c-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7c50c-139">RELATED LINKS</span></span>

[<span data-ttu-id="7c50c-140">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="7c50c-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="7c50c-141">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="7c50c-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="7c50c-142">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="7c50c-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="7c50c-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="7c50c-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="7c50c-144">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="7c50c-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="7c50c-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7c50c-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="7c50c-146">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="7c50c-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="7c50c-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="7c50c-147">Remove-PSSession</span></span>](Remove-PSSession.md)

