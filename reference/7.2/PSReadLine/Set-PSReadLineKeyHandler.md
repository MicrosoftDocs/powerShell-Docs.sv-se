---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 02/16/2021
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 86386cb8d97e16ebdd869e2ec554fc947d788f67
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563275"
---
# <span data-ttu-id="b5f1d-102">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="b5f1d-102">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="b5f1d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b5f1d-103">SYNOPSIS</span></span>
<span data-ttu-id="b5f1d-104">Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-104">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="b5f1d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b5f1d-105">SYNTAX</span></span>

### <span data-ttu-id="b5f1d-106">Script block</span><span class="sxs-lookup"><span data-stu-id="b5f1d-106">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="b5f1d-107">Funktion</span><span class="sxs-lookup"><span data-stu-id="b5f1d-107">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="b5f1d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b5f1d-108">DESCRIPTION</span></span>

<span data-ttu-id="b5f1d-109">`Set-PSReadLineKeyHandler`Cmdleten anpassar resultatet när en nyckel eller en sekvens av nycklar trycks ned.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-109">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="b5f1d-110">Med användardefinierade nyckel bindningar kan du göra nästan vad som möjligt i ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-110">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="b5f1d-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b5f1d-111">EXAMPLES</span></span>

### <span data-ttu-id="b5f1d-112">Exempel 1: bind piltangenten till en funktion</span><span class="sxs-lookup"><span data-stu-id="b5f1d-112">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="b5f1d-113">Det här kommandot binder upp piltangenten till funktionen **HistorySearchBackward** .</span><span class="sxs-lookup"><span data-stu-id="b5f1d-113">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="b5f1d-114">Den här funktionen söker igenom kommando historiken för kommando rader som börjar med det aktuella innehållet på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-114">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="b5f1d-115">Exempel 2: bind en nyckel till ett skript block</span><span class="sxs-lookup"><span data-stu-id="b5f1d-115">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="b5f1d-116">Det här exemplet visar hur du kan använda en enskild nyckel för att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-116">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="b5f1d-117">Kommandot binder nyckeln `Ctrl+B` till ett skript block som rensar raden, infogar ordet "Build" och accepterar sedan raden.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-117">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="b5f1d-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b5f1d-118">PARAMETERS</span></span>

### <span data-ttu-id="b5f1d-119">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="b5f1d-119">-BriefDescription</span></span>

<span data-ttu-id="b5f1d-120">En kort beskrivning av nyckel bindningen.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-120">A brief description of the key binding.</span></span> <span data-ttu-id="b5f1d-121">Den här beskrivningen visas av `Get-PSReadLineKeyHandler` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-121">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

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

### <span data-ttu-id="b5f1d-122">– Ackord</span><span class="sxs-lookup"><span data-stu-id="b5f1d-122">-Chord</span></span>

<span data-ttu-id="b5f1d-123">Nyckeln eller sekvensen av nycklar som ska bindas till en funktion eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-123">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="b5f1d-124">Använd en enkel sträng för att ange en enskild bindning.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-124">Use a single string to specify a single binding.</span></span> <span data-ttu-id="b5f1d-125">Om bindningen är en följd av nycklar separerar du nycklarna med kommatecken, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="b5f1d-125">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

> [!NOTE]
> <span data-ttu-id="b5f1d-126">Från och med PSReadLine-2.0.0  är parametern ackord **SKIFT** läges känslig.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-126">As of PSReadLine 2.0.0, the **Chord** parameter is **case-sensitive**.</span></span> <span data-ttu-id="b5f1d-127">Vilket innebär `Ctrl+X` `Ctrl+x` att olika bindningar skapas.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-127">Meaning, `Ctrl+X` and `Ctrl+x` will create different bindings.</span></span>

<span data-ttu-id="b5f1d-128">Den här parametern accepterar en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-128">This parameter accepts an array of strings.</span></span> <span data-ttu-id="b5f1d-129">Varje sträng är en separat bindning, inte en sekvens med nycklar för en enskild bindning.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-129">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

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

### <span data-ttu-id="b5f1d-130">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5f1d-130">-Description</span></span>

<span data-ttu-id="b5f1d-131">Anger en mer detaljerad beskrivning av den nyckel bindning som visas i utdata från `Get-PSReadLineKeyHandler` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-131">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

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

### <span data-ttu-id="b5f1d-132">– Funktion</span><span class="sxs-lookup"><span data-stu-id="b5f1d-132">-Function</span></span>

<span data-ttu-id="b5f1d-133">Anger namnet på en befintlig nyckel hanterare från PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-133">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="b5f1d-134">Med den här parametern kan du binda om befintliga nyckel bindningar eller binda en hanterare som för närvarande är obunden.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-134">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

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

### <span data-ttu-id="b5f1d-135">– Script block</span><span class="sxs-lookup"><span data-stu-id="b5f1d-135">-ScriptBlock</span></span>

<span data-ttu-id="b5f1d-136">Anger ett skript Blocks värde som ska köras när ackord anges.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-136">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="b5f1d-137">PSReadLine skickar en eller två parametrar till det här skript blocket.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-137">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="b5f1d-138">Den första parametern är ett **ConsoleKeyInfo** -objekt som representerar tangenten nedtryckt.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-138">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="b5f1d-139">Det andra argumentet kan vara vilket objekt som helst, beroende på kontexten.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-139">The second argument can be any object depending on the context.</span></span>

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

### <span data-ttu-id="b5f1d-140">-ViMode</span><span class="sxs-lookup"><span data-stu-id="b5f1d-140">-ViMode</span></span>

<span data-ttu-id="b5f1d-141">Ange vilket läge som bindningen gäller för.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-141">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="b5f1d-142">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="b5f1d-142">Valid values are:</span></span>

- <span data-ttu-id="b5f1d-143">Infogning</span><span class="sxs-lookup"><span data-stu-id="b5f1d-143">Insert</span></span>
- <span data-ttu-id="b5f1d-144">Kommando</span><span class="sxs-lookup"><span data-stu-id="b5f1d-144">Command</span></span>

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

### <span data-ttu-id="b5f1d-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5f1d-145">CommonParameters</span></span>

<span data-ttu-id="b5f1d-146">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5f1d-147">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b5f1d-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5f1d-148">INDATA</span><span class="sxs-lookup"><span data-stu-id="b5f1d-148">INPUTS</span></span>

### <span data-ttu-id="b5f1d-149">Inget</span><span class="sxs-lookup"><span data-stu-id="b5f1d-149">None</span></span>

<span data-ttu-id="b5f1d-150">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-150">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b5f1d-151">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b5f1d-151">OUTPUTS</span></span>

### <span data-ttu-id="b5f1d-152">Inget</span><span class="sxs-lookup"><span data-stu-id="b5f1d-152">None</span></span>

<span data-ttu-id="b5f1d-153">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b5f1d-153">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b5f1d-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b5f1d-154">NOTES</span></span>

## <span data-ttu-id="b5f1d-155">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b5f1d-155">RELATED LINKS</span></span>

[<span data-ttu-id="b5f1d-156">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="b5f1d-156">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="b5f1d-157">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="b5f1d-157">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="b5f1d-158">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="b5f1d-158">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="b5f1d-159">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="b5f1d-159">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

