---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 8eefd819b59cf8d0050484c6aad3058bc6e7753a
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273200"
---
# <span data-ttu-id="f0501-103">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="f0501-103">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="f0501-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f0501-104">SYNOPSIS</span></span>
<span data-ttu-id="f0501-105">Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.</span><span class="sxs-lookup"><span data-stu-id="f0501-105">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="f0501-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0501-106">SYNTAX</span></span>

### <span data-ttu-id="f0501-107">Script block</span><span class="sxs-lookup"><span data-stu-id="f0501-107">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="f0501-108">Funktion</span><span class="sxs-lookup"><span data-stu-id="f0501-108">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="f0501-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f0501-109">DESCRIPTION</span></span>

<span data-ttu-id="f0501-110">`Set-PSReadLineKeyHandler`Cmdleten anpassar resultatet när en nyckel eller en sekvens av nycklar trycks ned.</span><span class="sxs-lookup"><span data-stu-id="f0501-110">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="f0501-111">Med användardefinierade nyckel bindningar kan du göra nästan vad som möjligt i ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="f0501-111">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="f0501-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f0501-112">EXAMPLES</span></span>

### <span data-ttu-id="f0501-113">Exempel 1: bind piltangenten till en funktion</span><span class="sxs-lookup"><span data-stu-id="f0501-113">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="f0501-114">Det här kommandot binder upp piltangenten till funktionen **HistorySearchBackward** .</span><span class="sxs-lookup"><span data-stu-id="f0501-114">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="f0501-115">Den här funktionen söker igenom kommando historiken för kommando rader som börjar med det aktuella innehållet på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="f0501-115">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="f0501-116">Exempel 2: bind en nyckel till ett skript block</span><span class="sxs-lookup"><span data-stu-id="f0501-116">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="f0501-117">Det här exemplet visar hur du kan använda en enskild nyckel för att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="f0501-117">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="f0501-118">Kommandot binder nyckeln `Ctrl+B` till ett skript block som rensar raden, infogar ordet "Build" och accepterar sedan raden.</span><span class="sxs-lookup"><span data-stu-id="f0501-118">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="f0501-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f0501-119">PARAMETERS</span></span>

### <span data-ttu-id="f0501-120">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="f0501-120">-BriefDescription</span></span>

<span data-ttu-id="f0501-121">En kort beskrivning av nyckel bindningen.</span><span class="sxs-lookup"><span data-stu-id="f0501-121">A brief description of the key binding.</span></span> <span data-ttu-id="f0501-122">Den här beskrivningen visas av `Get-PSReadLineKeyHandler` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f0501-122">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

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

### <span data-ttu-id="f0501-123">– Ackord</span><span class="sxs-lookup"><span data-stu-id="f0501-123">-Chord</span></span>

<span data-ttu-id="f0501-124">Nyckeln eller sekvensen av nycklar som ska bindas till en funktion eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="f0501-124">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="f0501-125">Använd en enkel sträng för att ange en enskild bindning.</span><span class="sxs-lookup"><span data-stu-id="f0501-125">Use a single string to specify a single binding.</span></span> <span data-ttu-id="f0501-126">Om bindningen är en följd av nycklar separerar du nycklarna med kommatecken, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="f0501-126">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

<span data-ttu-id="f0501-127">Den här parametern accepterar en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="f0501-127">This parameter accepts an array of strings.</span></span> <span data-ttu-id="f0501-128">Varje sträng är en separat bindning, inte en sekvens med nycklar för en enskild bindning.</span><span class="sxs-lookup"><span data-stu-id="f0501-128">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

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

### <span data-ttu-id="f0501-129">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0501-129">-Description</span></span>

<span data-ttu-id="f0501-130">Anger en mer detaljerad beskrivning av den nyckel bindning som visas i utdata från `Get-PSReadLineKeyHandler` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f0501-130">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

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

### <span data-ttu-id="f0501-131">– Funktion</span><span class="sxs-lookup"><span data-stu-id="f0501-131">-Function</span></span>

<span data-ttu-id="f0501-132">Anger namnet på en befintlig nyckel hanterare från PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="f0501-132">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="f0501-133">Med den här parametern kan du binda om befintliga nyckel bindningar eller binda en hanterare som för närvarande är obunden.</span><span class="sxs-lookup"><span data-stu-id="f0501-133">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

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

### <span data-ttu-id="f0501-134">– Script block</span><span class="sxs-lookup"><span data-stu-id="f0501-134">-ScriptBlock</span></span>

<span data-ttu-id="f0501-135">Anger ett skript Blocks värde som ska köras när ackord anges.</span><span class="sxs-lookup"><span data-stu-id="f0501-135">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="f0501-136">PSReadLine skickar en eller två parametrar till det här skript blocket.</span><span class="sxs-lookup"><span data-stu-id="f0501-136">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="f0501-137">Den första parametern är ett **ConsoleKeyInfo** -objekt som representerar tangenten nedtryckt.</span><span class="sxs-lookup"><span data-stu-id="f0501-137">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="f0501-138">Det andra argumentet kan vara vilket objekt som helst, beroende på kontexten.</span><span class="sxs-lookup"><span data-stu-id="f0501-138">The second argument can be any object depending on the context.</span></span>

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

### <span data-ttu-id="f0501-139">-ViMode</span><span class="sxs-lookup"><span data-stu-id="f0501-139">-ViMode</span></span>

<span data-ttu-id="f0501-140">Ange vilket läge som bindningen gäller för.</span><span class="sxs-lookup"><span data-stu-id="f0501-140">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="f0501-141">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="f0501-141">Valid values are:</span></span>

- <span data-ttu-id="f0501-142">Infogning</span><span class="sxs-lookup"><span data-stu-id="f0501-142">Insert</span></span>
- <span data-ttu-id="f0501-143">Kommando</span><span class="sxs-lookup"><span data-stu-id="f0501-143">Command</span></span>

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

### <span data-ttu-id="f0501-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0501-144">CommonParameters</span></span>

<span data-ttu-id="f0501-145">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0501-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0501-146">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0501-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0501-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="f0501-147">INPUTS</span></span>

### <span data-ttu-id="f0501-148">Inget</span><span class="sxs-lookup"><span data-stu-id="f0501-148">None</span></span>

<span data-ttu-id="f0501-149">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0501-149">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="f0501-150">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f0501-150">OUTPUTS</span></span>

### <span data-ttu-id="f0501-151">Inget</span><span class="sxs-lookup"><span data-stu-id="f0501-151">None</span></span>

<span data-ttu-id="f0501-152">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f0501-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f0501-153">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f0501-153">NOTES</span></span>

## <span data-ttu-id="f0501-154">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f0501-154">RELATED LINKS</span></span>

[<span data-ttu-id="f0501-155">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="f0501-155">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="f0501-156">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="f0501-156">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="f0501-157">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="f0501-157">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="f0501-158">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="f0501-158">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
