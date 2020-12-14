---
description: Förklarar hur du använder lokala och fjärrvariabler i fjärrkommandon.
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 1cd6d0c4562fcd63fc56f103ec41aa6f0bb4c01c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709679"
---
# <a name="about-remote-variables"></a><span data-ttu-id="f0fc4-103">Om fjärrvariabler</span><span class="sxs-lookup"><span data-stu-id="f0fc4-103">About Remote Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="f0fc4-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0fc4-104">Short description</span></span>

<span data-ttu-id="f0fc4-105">Förklarar hur du använder lokala och fjärrvariabler i fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-105">Explains how to use local and remote variables in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="f0fc4-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0fc4-106">Long description</span></span>

<span data-ttu-id="f0fc4-107">Du kan använda variabler i kommandon som du kör på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-107">You can use variables in commands that you run on remote computers.</span></span> <span data-ttu-id="f0fc4-108">Tilldela ett värde till variabeln och Använd sedan variabeln i stället för värdet.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-108">Assign a value to the variable and then use the variable in place of the value.</span></span>

<span data-ttu-id="f0fc4-109">Som standard antas variablerna i fjärrkommandona att definieras i sessionen som kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-109">By default, the variables in remote commands are assumed to be defined in the session that runs the command.</span></span> <span data-ttu-id="f0fc4-110">Variabler som definieras i en lokal session måste identifieras som lokala variabler i kommandot.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-110">Variables that are defined in a local session, must be identified as local variables in the command.</span></span>

## <a name="using-remote-variables"></a><span data-ttu-id="f0fc4-111">Använda fjärrvariabler</span><span class="sxs-lookup"><span data-stu-id="f0fc4-111">Using remote variables</span></span>

<span data-ttu-id="f0fc4-112">PowerShell förutsätter att variablerna som används i fjärrkommandon definieras i sessionen där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-112">PowerShell assumes that the variables used in remote commands are defined in the session in which the command runs.</span></span>

<span data-ttu-id="f0fc4-113">I det här exemplet `$ps` definieras variabeln i den tillfälliga sessionen där `Get-WinEvent` kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-113">In this example, the `$ps` variable is defined in the temporary session in which the `Get-WinEvent` command runs.</span></span>

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

<span data-ttu-id="f0fc4-114">När kommandot körs i en beständig session, **PSSession**, måste fjärrvariabeln definieras i den sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-114">When the command runs in a persistent session, **PSSession**, the remote variable must be defined in that session.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a><span data-ttu-id="f0fc4-115">Använda lokala variabler</span><span class="sxs-lookup"><span data-stu-id="f0fc4-115">Using local variables</span></span>

<span data-ttu-id="f0fc4-116">Du kan använda lokala variabler i fjärrkommandon, men variabeln måste definieras i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-116">You can use local variables in remote commands, but the variable must be defined in the local session.</span></span>

<span data-ttu-id="f0fc4-117">Från och med PowerShell 3,0 kan du använda `Using` omfångs modifieraren för att identifiera en lokal variabel i ett fjärran slutet kommando.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-117">Beginning in PowerShell 3.0, you can use the `Using` scope modifier to identify a local variable in a remote command.</span></span>

<span data-ttu-id="f0fc4-118">Syntaxen för `Using` är följande:</span><span class="sxs-lookup"><span data-stu-id="f0fc4-118">The syntax of `Using` is as follows:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="f0fc4-119">I följande exempel `$ps` skapas variabeln i den lokala sessionen, men används i den session där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-119">In the following example, the `$ps` variable is created in the local session, but is used in the session in which the command runs.</span></span> <span data-ttu-id="f0fc4-120">`Using`Omfångs modifieraren identifieras `$ps` som en lokal variabel.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-120">The `Using` scope modifier identifies `$ps` as a local variable.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

<span data-ttu-id="f0fc4-121">`Using`Omfångs modifieraren kan användas i en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-121">The `Using` scope modifier can be used in a **PSSession**.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

<span data-ttu-id="f0fc4-122">En variabel referens, till exempel `$using:var` expanderar värdet variabeln `$var` från anroparens kontext.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-122">A variable reference such as `$using:var` expands to the value of variable `$var` from the caller's context.</span></span> <span data-ttu-id="f0fc4-123">Du får inte åtkomst till anroparens variabel objekt.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-123">You do not get access to the caller's variable object.</span></span>
<span data-ttu-id="f0fc4-124">`Using`Omfångs modifieraren kan inte användas för att ändra en lokal variabel i **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-124">The `Using` scope modifier cannot be used to modify a local variable within the **PSSession**.</span></span> <span data-ttu-id="f0fc4-125">Följande kod fungerar exempelvis inte:</span><span class="sxs-lookup"><span data-stu-id="f0fc4-125">For example, the following code does not work:</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

<span data-ttu-id="f0fc4-126">Mer information om `Using` finns i [about_Scopes](./about_Scopes.md)</span><span class="sxs-lookup"><span data-stu-id="f0fc4-126">For more information about `Using`, see [about_Scopes](./about_Scopes.md)</span></span>

### <a name="using-splatting"></a><span data-ttu-id="f0fc4-127">Använda ihopbuntning</span><span class="sxs-lookup"><span data-stu-id="f0fc4-127">Using splatting</span></span>

<span data-ttu-id="f0fc4-128">PowerShell-ihopbuntning skickar en samling parameter namn och värden till ett kommando.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-128">PowerShell splatting passes a collection of parameter names and values to a command.</span></span> <span data-ttu-id="f0fc4-129">Mer information finns i [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="f0fc4-129">For more information, see [about_Splatting](about_Splatting.md).</span></span>

<span data-ttu-id="f0fc4-130">I det här exemplet är ihopbuntning-variabeln `$Splat` en hash-tabell som har kon figurer ATS på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-130">In this example, the splatting variable, `$Splat` is a hash table that is set up on the local computer.</span></span> <span data-ttu-id="f0fc4-131">`Invoke-Command`Ansluter till en fjärrdator-session.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-131">The `Invoke-Command` connects to a remote computer session.</span></span> <span data-ttu-id="f0fc4-132">**Script block** använder `Using` omfångs modifieraren med symbolen at ( `@` ) för att representera splatted-variabeln.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-132">The **ScriptBlock** uses the `Using` scope modifier with the At (`@`) symbol to represent the splatted variable.</span></span>

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a><span data-ttu-id="f0fc4-133">Andra situationer där omfångs modifieraren "använder" krävs</span><span class="sxs-lookup"><span data-stu-id="f0fc4-133">Other situations where the 'Using' scope modifier is needed</span></span>

<span data-ttu-id="f0fc4-134">För alla skript eller kommandon som körs utanför sessionen behöver du `Using` omfångs modifieraren för att bädda in variabel värden från scopet för den anropande sessionen, så att det går att komma åt dem.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-134">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="f0fc4-135">`Using`Omfångs modifieraren stöds i följande kontexter:</span><span class="sxs-lookup"><span data-stu-id="f0fc4-135">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="f0fc4-136">Fjärrkörning av kommandon, startade med `Invoke-Command` användning **av ComputerName**, **hostname**, **SSHConnection** eller **sessionstillstånd** (fjärrsession)</span><span class="sxs-lookup"><span data-stu-id="f0fc4-136">Remotely executed commands, started with `Invoke-Command` using the **ComputerName**, **HostName**, **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="f0fc4-137">Bakgrunds jobb, startade med `Start-Job` (out-of-process-session)</span><span class="sxs-lookup"><span data-stu-id="f0fc4-137">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="f0fc4-138">Tråd jobb, startade via `Start-ThreadJob` eller `ForEach-Object -Parallel` (separat trådpool)</span><span class="sxs-lookup"><span data-stu-id="f0fc4-138">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="f0fc4-139">Beroende på sammanhanget är inbäddade variabel värden antingen oberoende kopior av data i anroparens omfång eller referenser till den.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-139">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="f0fc4-140">I fjärranslutna och inaktiva sessioner är de alltid oberoende kopior.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-140">In remote and out-of-process sessions, they are always independent copies.</span></span> <span data-ttu-id="f0fc4-141">De skickas som referens i Thread-sessioner.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-141">In thread sessions, they are passed by reference.</span></span>

## <a name="serialization-of-variable-values"></a><span data-ttu-id="f0fc4-142">Serialisering av variabel värden</span><span class="sxs-lookup"><span data-stu-id="f0fc4-142">Serialization of variable values</span></span>

<span data-ttu-id="f0fc4-143">Fjärrkörning av kommandon och bakgrunds jobb körs utanför processen.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-143">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="f0fc4-144">Sessioner utanför processen använder XML-baserad serialisering och deserialisering för att göra värdena för variabler tillgängliga över process gränserna.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-144">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="f0fc4-145">Serialiserings processen konverterar objekt till en **PSObject** som innehåller de ursprungliga objekt egenskaperna, men inte dess metoder.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-145">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="f0fc4-146">För en begränsad uppsättning typer, deserialiserar objekt tillbaka till den ursprungliga typen.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-146">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="f0fc4-147">Det dehydratiserade objektet är en kopia av den ursprungliga objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-147">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="f0fc4-148">Den har typ egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-148">It has the type properties and methods.</span></span> <span data-ttu-id="f0fc4-149">För enkla typer, till exempel **system. version**, är kopian exakt.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-149">For simple types, such as **System.Version**, the copy is exact.</span></span> <span data-ttu-id="f0fc4-150">För komplexa typer är kopian perfekt.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-150">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="f0fc4-151">Till exempel innehåller inte rehydratiserade certifikat objekt den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-151">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="f0fc4-152">Instanser av alla andra typer är **PSObject** -instanser.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-152">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="f0fc4-153">Egenskapen **PSTypeNames** innehåller det ursprungliga typ namnet som föregås av **deserialiserad**, till exempel **Deserialized.System. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="f0fc4-153">The **PSTypeNames** property contains the original type name prefixed with **Deserialized**, for example, **Deserialized.System.Data.DataTable**</span></span>

## <a name="using-local-variables-with-argumentlist-parameter"></a><span data-ttu-id="f0fc4-154">Använda lokala variabler med **argument List** -parametern</span><span class="sxs-lookup"><span data-stu-id="f0fc4-154">Using local variables with **ArgumentList** parameter</span></span>

<span data-ttu-id="f0fc4-155">Du kan använda lokala variabler i ett fjärran slutet kommando genom att definiera parametrar för fjärrkommandot och använda parametern **argument List** för `Invoke-Command` cmdleten för att ange den lokala variabeln som parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-155">You can use local variables in a remote command by defining parameters for the remote command and using the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

- <span data-ttu-id="f0fc4-156">Använd `param` nyckelordet för att definiera parametrar för fjärrkommandot.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-156">Use the `param` keyword to define parameters for the remote command.</span></span> <span data-ttu-id="f0fc4-157">Parameter namnen är plats hållare som inte behöver matcha den lokala variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-157">The parameter names are placeholders that don't need to match the local variable's name.</span></span>

- <span data-ttu-id="f0fc4-158">Använd de parametrar som definieras av `param` nyckelordet i kommandot.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-158">Use the parameters defined by the `param` keyword in the command.</span></span>

- <span data-ttu-id="f0fc4-159">Använd parametern **argument List** för `Invoke-Command` cmdleten för att ange den lokala variabeln som parameter värde.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-159">Use the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

<span data-ttu-id="f0fc4-160">Följande kommandon definierar till exempel `$ps` variabeln i den lokala sessionen och använder den sedan i ett fjärrkommando.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-160">For example, the following commands define the `$ps` variable in the local session and then use it in a remote command.</span></span> <span data-ttu-id="f0fc4-161">Kommandot använder `$log` som parameter namn och den lokala variabeln, `$ps` som värde.</span><span class="sxs-lookup"><span data-stu-id="f0fc4-161">The command uses `$log` as the parameter name and the local variable, `$ps`, as its value.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a><span data-ttu-id="f0fc4-162">Se även</span><span class="sxs-lookup"><span data-stu-id="f0fc4-162">See also</span></span>

[<span data-ttu-id="f0fc4-163">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="f0fc4-163">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="f0fc4-164">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f0fc4-164">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="f0fc4-165">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f0fc4-165">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="f0fc4-166">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="f0fc4-166">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="f0fc4-167">about_Variables</span><span class="sxs-lookup"><span data-stu-id="f0fc4-167">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="f0fc4-168">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="f0fc4-168">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="f0fc4-169">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="f0fc4-169">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="f0fc4-170">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f0fc4-170">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="f0fc4-171">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="f0fc4-171">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)

@Microsoft.PowerShell.Core.ForEach-Object

