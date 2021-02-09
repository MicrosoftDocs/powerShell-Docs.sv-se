---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b1827929c53560cb261cd7b3ba1e5bd407c25700
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975098"
---
# <span data-ttu-id="97a9d-102">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="97a9d-102">Exit-PSSession</span></span>

## <span data-ttu-id="97a9d-103">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="97a9d-103">Synopsis</span></span>
<span data-ttu-id="97a9d-104">Avslutar en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="97a9d-104">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="97a9d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="97a9d-105">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="97a9d-106">Description</span><span class="sxs-lookup"><span data-stu-id="97a9d-106">Description</span></span>

<span data-ttu-id="97a9d-107">`Exit-PSSession`Cmdleten avslutar interaktiva sessioner som du startade med `Enter-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="97a9d-107">The `Exit-PSSession` cmdlet ends interactive sessions that you started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="97a9d-108">Du kan också använda `exit` nyckelordet för att avsluta en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="97a9d-108">You can also use the `exit` keyword to end an interactive session.</span></span> <span data-ttu-id="97a9d-109">Detta är detsamma som att använda `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="97a9d-109">The effect is the same as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="97a9d-110">Exempel</span><span class="sxs-lookup"><span data-stu-id="97a9d-110">Examples</span></span>

### <span data-ttu-id="97a9d-111">Exempel 1: starta och stoppa en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="97a9d-111">Example 1: Start and stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="97a9d-112">Kommandona startar och stoppar sedan en interaktiv session med Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="97a9d-112">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="97a9d-113">Exempel 2: starta och stoppa en interaktiv session med hjälp av ett PSSession-objekt</span><span class="sxs-lookup"><span data-stu-id="97a9d-113">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="97a9d-114">Kommandona startar och stoppar en interaktiv session med Server01-datorn som använder en PowerShell-session (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="97a9d-114">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="97a9d-115">Eftersom den interaktiva sessionen startades med hjälp av en PowerShell-session är **PSSession** fortfarande tillgängligt när den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="97a9d-115">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span> <span data-ttu-id="97a9d-116">Om du använder parametern _computername_ `Enter-PSSession` skapas en tillfällig session som stängs när den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="97a9d-116">If you use the _ComputerName_ parameter, `Enter-PSSession` creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="97a9d-117">Det första kommandot använder `New-PSSession` cmdleten för att skapa en **PSSession** på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="97a9d-117">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="97a9d-118">Kommandot sparar **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="97a9d-118">The command saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="97a9d-119">Det andra kommandot använder `Enter-PSSession` för att starta en interaktiv session med hjälp av **PSSession** i `$s` .</span><span class="sxs-lookup"><span data-stu-id="97a9d-119">The second command uses `Enter-PSSession` to start an interactive session using the **PSSession** in `$s`.</span></span>

<span data-ttu-id="97a9d-120">Det tredje kommandot använder `Exit-PSSession` för att stoppa den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="97a9d-120">The third command uses `Exit-PSSession` to stop the interactive session.</span></span>

<span data-ttu-id="97a9d-121">Det sista kommandot visar **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="97a9d-121">The final command displays the **PSSession** in the `$s` variable.</span></span> <span data-ttu-id="97a9d-122">Egenskapen **State** visar att **PSSession** fortfarande är öppen och tillgänglig för användning.</span><span class="sxs-lookup"><span data-stu-id="97a9d-122">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="97a9d-123">Exempel 3: Använd nyckelordet Exit för att stoppa en session</span><span class="sxs-lookup"><span data-stu-id="97a9d-123">Example 3: Use the Exit keyword to stop a session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="97a9d-124">I det här exemplet används `exit` nyckelordet för att stoppa en interaktiv session som har startats med hjälp av `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="97a9d-124">This example uses the `exit` keyword to stop an interactive session started by using `Enter-PSSession`.</span></span> <span data-ttu-id="97a9d-125">`exit`Nyckelordet har samma resultat som när du använder `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="97a9d-125">The `exit` keyword has the same effect as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="97a9d-126">Parametrar</span><span class="sxs-lookup"><span data-stu-id="97a9d-126">Parameters</span></span>

### <span data-ttu-id="97a9d-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="97a9d-127">CommonParameters</span></span>

<span data-ttu-id="97a9d-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="97a9d-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="97a9d-129">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="97a9d-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="97a9d-130">Indata</span><span class="sxs-lookup"><span data-stu-id="97a9d-130">Inputs</span></span>

### <span data-ttu-id="97a9d-131">Inget</span><span class="sxs-lookup"><span data-stu-id="97a9d-131">None</span></span>

<span data-ttu-id="97a9d-132">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="97a9d-132">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="97a9d-133">Utdata</span><span class="sxs-lookup"><span data-stu-id="97a9d-133">Outputs</span></span>

### <span data-ttu-id="97a9d-134">Inget</span><span class="sxs-lookup"><span data-stu-id="97a9d-134">None</span></span>

<span data-ttu-id="97a9d-135">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="97a9d-135">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="97a9d-136">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="97a9d-136">Notes</span></span>

<span data-ttu-id="97a9d-137">Denna cmdlet tar bara med de gemensamma parametrarna.</span><span class="sxs-lookup"><span data-stu-id="97a9d-137">This cmdlet takes only the common parameters.</span></span>

## <span data-ttu-id="97a9d-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="97a9d-138">RELATED LINKS</span></span>

[<span data-ttu-id="97a9d-139">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="97a9d-139">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="97a9d-140">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="97a9d-140">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="97a9d-141">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="97a9d-141">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="97a9d-142">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="97a9d-142">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="97a9d-143">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="97a9d-143">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="97a9d-144">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="97a9d-144">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="97a9d-145">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="97a9d-145">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="97a9d-146">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="97a9d-146">Remove-PSSession</span></span>](Remove-PSSession.md)
