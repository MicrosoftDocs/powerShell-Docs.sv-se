---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: 1e0c8413a37a9b8877b6af9089ac311459ada20d
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975115"
---
# <span data-ttu-id="fd23a-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="fd23a-103">Exit-PSSession</span></span>

## <span data-ttu-id="fd23a-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="fd23a-104">Synopsis</span></span>
<span data-ttu-id="fd23a-105">Avslutar en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="fd23a-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="fd23a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fd23a-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="fd23a-107">Description</span><span class="sxs-lookup"><span data-stu-id="fd23a-107">Description</span></span>

<span data-ttu-id="fd23a-108">`Exit-PSSession`Cmdleten avslutar interaktiva sessioner som du startade med `Enter-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fd23a-108">The `Exit-PSSession` cmdlet ends interactive sessions that you started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="fd23a-109">Du kan också använda `exit` nyckelordet för att avsluta en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="fd23a-109">You can also use the `exit` keyword to end an interactive session.</span></span> <span data-ttu-id="fd23a-110">Detta är detsamma som att använda `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="fd23a-110">The effect is the same as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="fd23a-111">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd23a-111">Examples</span></span>

### <span data-ttu-id="fd23a-112">Exempel 1: starta och stoppa en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="fd23a-112">Example 1: Start and stop an interactive session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS C:\>
```

<span data-ttu-id="fd23a-113">Kommandona startar och stoppar sedan en interaktiv session med Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="fd23a-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="fd23a-114">Exempel 2: starta och stoppa en interaktiv session med hjälp av ett PSSession-objekt</span><span class="sxs-lookup"><span data-stu-id="fd23a-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS C:\> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="fd23a-115">Kommandona startar och stoppar en interaktiv session med Server01-datorn som använder en Windows PowerShell-session (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="fd23a-115">These commands start and stop an interactive session with the Server01 computer that uses a Windows PowerShell session (**PSSession**).</span></span>

<span data-ttu-id="fd23a-116">Eftersom den interaktiva sessionen startades med hjälp av en Windows PowerShell-session är **PSSession** fortfarande tillgängligt när den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="fd23a-116">Because the interactive session was started by using a Windows PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span> <span data-ttu-id="fd23a-117">Om du använder parametern _computername_ `Enter-PSSession` skapas en tillfällig session som stängs när den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="fd23a-117">If you use the _ComputerName_ parameter, `Enter-PSSession` creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="fd23a-118">Det första kommandot använder `New-PSSession` cmdleten för att skapa en **PSSession** på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="fd23a-118">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="fd23a-119">Kommandot sparar **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fd23a-119">The command saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="fd23a-120">Det andra kommandot använder `Enter-PSSession` för att starta en interaktiv session med hjälp av **PSSession** i `$s` .</span><span class="sxs-lookup"><span data-stu-id="fd23a-120">The second command uses `Enter-PSSession` to start an interactive session using the **PSSession** in `$s`.</span></span>

<span data-ttu-id="fd23a-121">Det tredje kommandot använder `Exit-PSSession` för att stoppa den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="fd23a-121">The third command uses `Exit-PSSession` to stop the interactive session.</span></span>

<span data-ttu-id="fd23a-122">Det sista kommandot visar **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fd23a-122">The final command displays the **PSSession** in the `$s` variable.</span></span> <span data-ttu-id="fd23a-123">Egenskapen **State** visar att **PSSession** fortfarande är öppen och tillgänglig för användning.</span><span class="sxs-lookup"><span data-stu-id="fd23a-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="fd23a-124">Exempel 3: Använd nyckelordet Exit för att stoppa en session</span><span class="sxs-lookup"><span data-stu-id="fd23a-124">Example 3: Use the Exit keyword to stop a session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS C:\>
```

<span data-ttu-id="fd23a-125">I det här exemplet används `exit` nyckelordet för att stoppa en interaktiv session som har startats med hjälp av `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="fd23a-125">This example uses the `exit` keyword to stop an interactive session started by using `Enter-PSSession`.</span></span> <span data-ttu-id="fd23a-126">`exit`Nyckelordet har samma resultat som när du använder `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="fd23a-126">The `exit` keyword has the same effect as using `Exit-PSSession`.</span></span>

## <span data-ttu-id="fd23a-127">Parametrar</span><span class="sxs-lookup"><span data-stu-id="fd23a-127">Parameters</span></span>

### <span data-ttu-id="fd23a-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fd23a-128">CommonParameters</span></span>

<span data-ttu-id="fd23a-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fd23a-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fd23a-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fd23a-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fd23a-131">Indata</span><span class="sxs-lookup"><span data-stu-id="fd23a-131">Inputs</span></span>

### <span data-ttu-id="fd23a-132">Inget</span><span class="sxs-lookup"><span data-stu-id="fd23a-132">None</span></span>

<span data-ttu-id="fd23a-133">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd23a-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="fd23a-134">Utdata</span><span class="sxs-lookup"><span data-stu-id="fd23a-134">Outputs</span></span>

### <span data-ttu-id="fd23a-135">Inget</span><span class="sxs-lookup"><span data-stu-id="fd23a-135">None</span></span>

<span data-ttu-id="fd23a-136">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="fd23a-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="fd23a-137">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="fd23a-137">Notes</span></span>

<span data-ttu-id="fd23a-138">Denna cmdlet tar bara med de gemensamma parametrarna.</span><span class="sxs-lookup"><span data-stu-id="fd23a-138">This cmdlet takes only the common parameters.</span></span>

## <span data-ttu-id="fd23a-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fd23a-139">RELATED LINKS</span></span>

[<span data-ttu-id="fd23a-140">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="fd23a-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="fd23a-141">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="fd23a-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="fd23a-142">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="fd23a-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="fd23a-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="fd23a-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="fd23a-144">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="fd23a-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="fd23a-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="fd23a-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="fd23a-146">Ta emot – PSSession</span><span class="sxs-lookup"><span data-stu-id="fd23a-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="fd23a-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="fd23a-147">Remove-PSSession</span></span>](Remove-PSSession.md)
