---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 02/16/2021
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 22ad8a33f80ad5f4d75fe23c0c8f6c845a40d748
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563247"
---
# <span data-ttu-id="ff3b1-103">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="ff3b1-103">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="ff3b1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ff3b1-104">SYNOPSIS</span></span>
<span data-ttu-id="ff3b1-105">Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-105">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="ff3b1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ff3b1-106">SYNTAX</span></span>

### <span data-ttu-id="ff3b1-107">Script block</span><span class="sxs-lookup"><span data-stu-id="ff3b1-107">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="ff3b1-108">Funktion</span><span class="sxs-lookup"><span data-stu-id="ff3b1-108">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="ff3b1-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ff3b1-109">DESCRIPTION</span></span>

<span data-ttu-id="ff3b1-110">`Set-PSReadLineKeyHandler`Cmdleten anpassar resultatet när en nyckel eller en sekvens av nycklar trycks ned.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-110">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="ff3b1-111">Med användardefinierade nyckel bindningar kan du göra nästan vad som möjligt i ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-111">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="ff3b1-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ff3b1-112">EXAMPLES</span></span>

### <span data-ttu-id="ff3b1-113">Exempel 1: bind piltangenten till en funktion</span><span class="sxs-lookup"><span data-stu-id="ff3b1-113">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="ff3b1-114">Det här kommandot binder upp piltangenten till funktionen **HistorySearchBackward** .</span><span class="sxs-lookup"><span data-stu-id="ff3b1-114">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="ff3b1-115">Den här funktionen söker igenom kommando historiken för kommando rader som börjar med det aktuella innehållet på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-115">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="ff3b1-116">Exempel 2: bind en nyckel till ett skript block</span><span class="sxs-lookup"><span data-stu-id="ff3b1-116">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="ff3b1-117">Det här exemplet visar hur du kan använda en enskild nyckel för att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-117">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="ff3b1-118">Kommandot binder nyckeln `Ctrl+B` till ett skript block som rensar raden, infogar ordet "Build" och accepterar sedan raden.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-118">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="ff3b1-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ff3b1-119">PARAMETERS</span></span>

### <span data-ttu-id="ff3b1-120">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="ff3b1-120">-BriefDescription</span></span>

<span data-ttu-id="ff3b1-121">En kort beskrivning av nyckel bindningen.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-121">A brief description of the key binding.</span></span> <span data-ttu-id="ff3b1-122">Den här beskrivningen visas av `Get-PSReadLineKeyHandler` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-122">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff3b1-123">– Ackord</span><span class="sxs-lookup"><span data-stu-id="ff3b1-123">-Chord</span></span>

<span data-ttu-id="ff3b1-124">Nyckeln eller sekvensen av nycklar som ska bindas till en funktion eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-124">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="ff3b1-125">Använd en enkel sträng för att ange en enskild bindning.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-125">Use a single string to specify a single binding.</span></span> <span data-ttu-id="ff3b1-126">Om bindningen är en följd av nycklar separerar du nycklarna med kommatecken, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-126">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

> [!NOTE]
> <span data-ttu-id="ff3b1-127">Från och med PSReadLine-2.0.0  är parametern ackord **SKIFT** läges känslig.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-127">As of PSReadLine 2.0.0, the **Chord** parameter is **case-sensitive**.</span></span> <span data-ttu-id="ff3b1-128">Vilket innebär `Ctrl+X` `Ctrl+x` att olika bindningar skapas.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-128">Meaning, `Ctrl+X` and `Ctrl+x` will create different bindings.</span></span>

<span data-ttu-id="ff3b1-129">Den här parametern accepterar en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-129">This parameter accepts an array of strings.</span></span> <span data-ttu-id="ff3b1-130">Varje sträng är en separat bindning, inte en sekvens med nycklar för en enskild bindning.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-130">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff3b1-131">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ff3b1-131">-Description</span></span>

<span data-ttu-id="ff3b1-132">Anger en mer detaljerad beskrivning av den nyckel bindning som visas i utdata från `Get-PSReadLineKeyHandler` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-132">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff3b1-133">– Funktion</span><span class="sxs-lookup"><span data-stu-id="ff3b1-133">-Function</span></span>

<span data-ttu-id="ff3b1-134">Anger namnet på en befintlig nyckel hanterare från PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-134">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="ff3b1-135">Med den här parametern kan du binda om befintliga nyckel bindningar eller binda en hanterare som för närvarande är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-135">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff3b1-136">– Script block</span><span class="sxs-lookup"><span data-stu-id="ff3b1-136">-ScriptBlock</span></span>

<span data-ttu-id="ff3b1-137">Anger ett skript Blocks värde som ska köras när ackord anges.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-137">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="ff3b1-138">PSReadLine skickar en eller två parametrar till det här skript blocket.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-138">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="ff3b1-139">Den första parametern är ett **ConsoleKeyInfo** -objekt som representerar tangenten nedtryckt.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-139">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="ff3b1-140">Det andra argumentet kan vara vilket objekt som helst, beroende på kontexten.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-140">The second argument can be any object depending on the context.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff3b1-141">-ViMode</span><span class="sxs-lookup"><span data-stu-id="ff3b1-141">-ViMode</span></span>

<span data-ttu-id="ff3b1-142">Ange vilket läge som bindningen gäller för.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-142">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="ff3b1-143">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-143">Valid values are:</span></span>

- <span data-ttu-id="ff3b1-144">Infogning</span><span class="sxs-lookup"><span data-stu-id="ff3b1-144">Insert</span></span>
- <span data-ttu-id="ff3b1-145">Kommando</span><span class="sxs-lookup"><span data-stu-id="ff3b1-145">Command</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff3b1-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff3b1-146">CommonParameters</span></span>

<span data-ttu-id="ff3b1-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ff3b1-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ff3b1-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ff3b1-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="ff3b1-149">INPUTS</span></span>

### <span data-ttu-id="ff3b1-150">Inget</span><span class="sxs-lookup"><span data-stu-id="ff3b1-150">None</span></span>

<span data-ttu-id="ff3b1-151">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-151">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="ff3b1-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ff3b1-152">OUTPUTS</span></span>

### <span data-ttu-id="ff3b1-153">Inget</span><span class="sxs-lookup"><span data-stu-id="ff3b1-153">None</span></span>

<span data-ttu-id="ff3b1-154">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ff3b1-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ff3b1-155">NOTES</span></span>

## <span data-ttu-id="ff3b1-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ff3b1-156">RELATED LINKS</span></span>

[<span data-ttu-id="ff3b1-157">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="ff3b1-157">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="ff3b1-158">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="ff3b1-158">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="ff3b1-159">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="ff3b1-159">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="ff3b1-160">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="ff3b1-160">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
