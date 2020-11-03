---
description: Förklarar hur du använder lokala och fjärrvariabler i fjärrkommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 2260e1a6ba4553cbdba0057972f491d17c61382d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272325"
---
# <a name="about-remote-variables"></a><span data-ttu-id="e933a-104">Om fjärrvariabler</span><span class="sxs-lookup"><span data-stu-id="e933a-104">About Remote Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="e933a-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="e933a-105">Short description</span></span>

<span data-ttu-id="e933a-106">Förklarar hur du använder lokala och fjärrvariabler i fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="e933a-106">Explains how to use local and remote variables in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="e933a-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="e933a-107">Long description</span></span>

<span data-ttu-id="e933a-108">Du kan använda variabler i kommandon som du kör på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="e933a-108">You can use variables in commands that you run on remote computers.</span></span> <span data-ttu-id="e933a-109">Tilldela ett värde till variabeln och Använd sedan variabeln i stället för värdet.</span><span class="sxs-lookup"><span data-stu-id="e933a-109">Assign a value to the variable and then use the variable in place of the value.</span></span>

<span data-ttu-id="e933a-110">Som standard antas variablerna i fjärrkommandona att definieras i sessionen som kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="e933a-110">By default, the variables in remote commands are assumed to be defined in the session that runs the command.</span></span> <span data-ttu-id="e933a-111">Variabler som definieras i en lokal session måste identifieras som lokala variabler i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e933a-111">Variables that are defined in a local session, must be identified as local variables in the command.</span></span>

## <a name="using-remote-variables"></a><span data-ttu-id="e933a-112">Använda fjärrvariabler</span><span class="sxs-lookup"><span data-stu-id="e933a-112">Using remote variables</span></span>

<span data-ttu-id="e933a-113">PowerShell förutsätter att variablerna som används i fjärrkommandon definieras i sessionen där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="e933a-113">PowerShell assumes that the variables used in remote commands are defined in the session in which the command runs.</span></span>

<span data-ttu-id="e933a-114">I det här exemplet `$ps` definieras variabeln i den tillfälliga sessionen där `Get-WinEvent` kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="e933a-114">In this example, the `$ps` variable is defined in the temporary session in which the `Get-WinEvent` command runs.</span></span>

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

<span data-ttu-id="e933a-115">När kommandot körs i en beständig session, **PSSession** , måste fjärrvariabeln definieras i den sessionen.</span><span class="sxs-lookup"><span data-stu-id="e933a-115">When the command runs in a persistent session, **PSSession** , the remote variable must be defined in that session.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a><span data-ttu-id="e933a-116">Använda lokala variabler</span><span class="sxs-lookup"><span data-stu-id="e933a-116">Using local variables</span></span>

<span data-ttu-id="e933a-117">Du kan använda lokala variabler i fjärrkommandon, men variabeln måste definieras i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="e933a-117">You can use local variables in remote commands, but the variable must be defined in the local session.</span></span>

<span data-ttu-id="e933a-118">Från och med PowerShell 3,0 kan du använda `Using` omfångs modifieraren för att identifiera en lokal variabel i ett fjärran slutet kommando.</span><span class="sxs-lookup"><span data-stu-id="e933a-118">Beginning in PowerShell 3.0, you can use the `Using` scope modifier to identify a local variable in a remote command.</span></span>

<span data-ttu-id="e933a-119">Syntaxen för `Using` är följande:</span><span class="sxs-lookup"><span data-stu-id="e933a-119">The syntax of `Using` is as follows:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="e933a-120">I följande exempel `$ps` skapas variabeln i den lokala sessionen, men används i den session där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="e933a-120">In the following example, the `$ps` variable is created in the local session, but is used in the session in which the command runs.</span></span> <span data-ttu-id="e933a-121">`Using`Omfångs modifieraren identifieras `$ps` som en lokal variabel.</span><span class="sxs-lookup"><span data-stu-id="e933a-121">The `Using` scope modifier identifies `$ps` as a local variable.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

<span data-ttu-id="e933a-122">`Using`Omfångs modifieraren kan användas i en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="e933a-122">The `Using` scope modifier can be used in a **PSSession**.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

<span data-ttu-id="e933a-123">En variabel referens, till exempel `$using:var` expanderar värdet variabeln `$var` från anroparens kontext.</span><span class="sxs-lookup"><span data-stu-id="e933a-123">A variable reference such as `$using:var` expands to the value of variable `$var` from the caller's context.</span></span> <span data-ttu-id="e933a-124">Du får inte åtkomst till anroparens variabel objekt.</span><span class="sxs-lookup"><span data-stu-id="e933a-124">You do not get access to the caller's variable object.</span></span>
<span data-ttu-id="e933a-125">`Using`Omfångs modifieraren kan inte användas för att ändra en lokal variabel i **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="e933a-125">The `Using` scope modifier cannot be used to modify a local variable within the **PSSession**.</span></span> <span data-ttu-id="e933a-126">Följande kod fungerar exempelvis inte:</span><span class="sxs-lookup"><span data-stu-id="e933a-126">For example, the following code does not work:</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

<span data-ttu-id="e933a-127">Mer information om `Using` finns i [about_Scopes](./about_Scopes.md)</span><span class="sxs-lookup"><span data-stu-id="e933a-127">For more information about `Using`, see [about_Scopes](./about_Scopes.md)</span></span>

### <a name="using-splatting"></a><span data-ttu-id="e933a-128">Använda ihopbuntning</span><span class="sxs-lookup"><span data-stu-id="e933a-128">Using splatting</span></span>

<span data-ttu-id="e933a-129">PowerShell-ihopbuntning skickar en samling parameter namn och värden till ett kommando.</span><span class="sxs-lookup"><span data-stu-id="e933a-129">PowerShell splatting passes a collection of parameter names and values to a command.</span></span> <span data-ttu-id="e933a-130">Mer information finns i [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="e933a-130">For more information, see [about_Splatting](about_Splatting.md).</span></span>

<span data-ttu-id="e933a-131">I det här exemplet är ihopbuntning-variabeln `$Splat` en hash-tabell som har kon figurer ATS på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e933a-131">In this example, the splatting variable, `$Splat` is a hash table that is set up on the local computer.</span></span> <span data-ttu-id="e933a-132">`Invoke-Command`Ansluter till en fjärrdator-session.</span><span class="sxs-lookup"><span data-stu-id="e933a-132">The `Invoke-Command` connects to a remote computer session.</span></span> <span data-ttu-id="e933a-133">**Script block** använder `Using` omfångs modifieraren med symbolen at ( `@` ) för att representera splatted-variabeln.</span><span class="sxs-lookup"><span data-stu-id="e933a-133">The **ScriptBlock** uses the `Using` scope modifier with the At (`@`) symbol to represent the splatted variable.</span></span>

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a><span data-ttu-id="e933a-134">Andra situationer där omfångs modifieraren "använder" krävs</span><span class="sxs-lookup"><span data-stu-id="e933a-134">Other situations where the 'Using' scope modifier is needed</span></span>

<span data-ttu-id="e933a-135">För alla skript eller kommandon som körs utanför sessionen behöver du `Using` omfångs modifieraren för att bädda in variabel värden från scopet för den anropande sessionen, så att det går att komma åt dem.</span><span class="sxs-lookup"><span data-stu-id="e933a-135">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="e933a-136">`Using`Omfångs modifieraren stöds i följande kontexter:</span><span class="sxs-lookup"><span data-stu-id="e933a-136">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="e933a-137">Fjärrkörning av kommandon, startade med `Invoke-Command` användning **av ComputerName** , **hostname** , **SSHConnection** eller **sessionstillstånd** (fjärrsession)</span><span class="sxs-lookup"><span data-stu-id="e933a-137">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** , **HostName** , **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="e933a-138">Bakgrunds jobb, startade med `Start-Job` (out-of-process-session)</span><span class="sxs-lookup"><span data-stu-id="e933a-138">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="e933a-139">Tråd jobb, startade via `Start-ThreadJob` eller `ForEach-Object -Parallel` (separat trådpool)</span><span class="sxs-lookup"><span data-stu-id="e933a-139">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="e933a-140">Beroende på sammanhanget är inbäddade variabel värden antingen oberoende kopior av data i anroparens omfång eller referenser till den.</span><span class="sxs-lookup"><span data-stu-id="e933a-140">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="e933a-141">I fjärranslutna och inaktiva sessioner är de alltid oberoende kopior.</span><span class="sxs-lookup"><span data-stu-id="e933a-141">In remote and out-of-process sessions, they are always independent copies.</span></span> <span data-ttu-id="e933a-142">De skickas som referens i Thread-sessioner.</span><span class="sxs-lookup"><span data-stu-id="e933a-142">In thread sessions, they are passed by reference.</span></span>

## <a name="serialization-of-variable-values"></a><span data-ttu-id="e933a-143">Serialisering av variabel värden</span><span class="sxs-lookup"><span data-stu-id="e933a-143">Serialization of variable values</span></span>

<span data-ttu-id="e933a-144">Fjärrkörning av kommandon och bakgrunds jobb körs utanför processen.</span><span class="sxs-lookup"><span data-stu-id="e933a-144">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="e933a-145">Sessioner utanför processen använder XML-baserad serialisering och deserialisering för att göra värdena för variabler tillgängliga över process gränserna.</span><span class="sxs-lookup"><span data-stu-id="e933a-145">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="e933a-146">Serialiserings processen konverterar objekt till en **PSObject** som innehåller de ursprungliga objekt egenskaperna, men inte dess metoder.</span><span class="sxs-lookup"><span data-stu-id="e933a-146">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="e933a-147">För en begränsad uppsättning typer, deserialiserar objekt tillbaka till den ursprungliga typen.</span><span class="sxs-lookup"><span data-stu-id="e933a-147">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="e933a-148">Det dehydratiserade objektet är en kopia av den ursprungliga objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="e933a-148">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="e933a-149">Den har typ egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="e933a-149">It has the type properties and methods.</span></span> <span data-ttu-id="e933a-150">För enkla typer, till exempel **system. version** , är kopian exakt.</span><span class="sxs-lookup"><span data-stu-id="e933a-150">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="e933a-151">För komplexa typer är kopian perfekt.</span><span class="sxs-lookup"><span data-stu-id="e933a-151">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="e933a-152">Till exempel innehåller inte rehydratiserade certifikat objekt den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="e933a-152">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="e933a-153">Instanser av alla andra typer är **PSObject** -instanser.</span><span class="sxs-lookup"><span data-stu-id="e933a-153">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="e933a-154">Egenskapen **PSTypeNames** innehåller det ursprungliga typ namnet som föregås av **deserialiserad** , till exempel **Deserialized.System. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="e933a-154">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

## <a name="using-local-variables-with-argumentlist-parameter"></a><span data-ttu-id="e933a-155">Använda lokala variabler med **argument List** -parametern</span><span class="sxs-lookup"><span data-stu-id="e933a-155">Using local variables with **ArgumentList** parameter</span></span>

<span data-ttu-id="e933a-156">Du kan använda lokala variabler i ett fjärran slutet kommando genom att definiera parametrar för fjärrkommandot och använda parametern **argument List** för `Invoke-Command` cmdleten för att ange den lokala variabeln som parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="e933a-156">You can use local variables in a remote command by defining parameters for the remote command and using the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

- <span data-ttu-id="e933a-157">Använd `param` nyckelordet för att definiera parametrar för fjärrkommandot.</span><span class="sxs-lookup"><span data-stu-id="e933a-157">Use the `param` keyword to define parameters for the remote command.</span></span> <span data-ttu-id="e933a-158">Parameter namnen är plats hållare som inte behöver matcha den lokala variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="e933a-158">The parameter names are placeholders that don't need to match the local variable's name.</span></span>

- <span data-ttu-id="e933a-159">Använd de parametrar som definieras av `param` nyckelordet i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e933a-159">Use the parameters defined by the `param` keyword in the command.</span></span>

- <span data-ttu-id="e933a-160">Använd parametern **argument List** för `Invoke-Command` cmdleten för att ange den lokala variabeln som parameter värde.</span><span class="sxs-lookup"><span data-stu-id="e933a-160">Use the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

<span data-ttu-id="e933a-161">Följande kommandon definierar till exempel `$ps` variabeln i den lokala sessionen och använder den sedan i ett fjärrkommando.</span><span class="sxs-lookup"><span data-stu-id="e933a-161">For example, the following commands define the `$ps` variable in the local session and then use it in a remote command.</span></span> <span data-ttu-id="e933a-162">Kommandot använder `$log` som parameter namn och den lokala variabeln, `$ps` som värde.</span><span class="sxs-lookup"><span data-stu-id="e933a-162">The command uses `$log` as the parameter name and the local variable, `$ps`, as its value.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a><span data-ttu-id="e933a-163">Se även</span><span class="sxs-lookup"><span data-stu-id="e933a-163">See also</span></span>

[<span data-ttu-id="e933a-164">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e933a-164">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="e933a-165">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e933a-165">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="e933a-166">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="e933a-166">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="e933a-167">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="e933a-167">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="e933a-168">about_Variables</span><span class="sxs-lookup"><span data-stu-id="e933a-168">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="e933a-169">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="e933a-169">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="e933a-170">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="e933a-170">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="e933a-171">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e933a-171">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="e933a-172">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="e933a-172">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)

[<span data-ttu-id="e933a-173">-Objekt</span><span class="sxs-lookup"><span data-stu-id="e933a-173">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
