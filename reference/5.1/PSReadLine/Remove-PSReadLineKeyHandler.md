---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: e0cdd2358cfd4819285947b1f703963691088e2b
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273026"
---
# <span data-ttu-id="5b7bc-103">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5b7bc-103">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="5b7bc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5b7bc-104">SYNOPSIS</span></span>
<span data-ttu-id="5b7bc-105">Tar bort en nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-105">Removes a key binding.</span></span>

## <span data-ttu-id="5b7bc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b7bc-106">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="5b7bc-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5b7bc-107">DESCRIPTION</span></span>

<span data-ttu-id="5b7bc-108">`Remove-PSReadLineKeyHandler`Cmdleten tar bort en angiven nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-108">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="5b7bc-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5b7bc-109">EXAMPLES</span></span>

### <span data-ttu-id="5b7bc-110">Exempel 1: ta bort en bindning</span><span class="sxs-lookup"><span data-stu-id="5b7bc-110">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="5b7bc-111">Det här kommandot tar bort bindningen från nyckel kombinationen eller ackord `Ctrl+B` .</span><span class="sxs-lookup"><span data-stu-id="5b7bc-111">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="5b7bc-112">`Ctrl+B`Ackord skapas i `Set-PSReadLineKeyHandler` artikeln.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-112">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="5b7bc-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5b7bc-113">PARAMETERS</span></span>

### <span data-ttu-id="5b7bc-114">– Ackord</span><span class="sxs-lookup"><span data-stu-id="5b7bc-114">-Chord</span></span>

<span data-ttu-id="5b7bc-115">Anger en matris med nycklar eller sekvenser med nycklar som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-115">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="5b7bc-116">En enda bindning anges genom att använda en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-116">A single binding is specified by using a single string.</span></span> <span data-ttu-id="5b7bc-117">Om bindningen är en följd av nycklar separerar du nycklarna med kommatecken, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="5b7bc-117">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="5b7bc-118">Den här parametern accepterar en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-118">This parameter accepts an array of strings.</span></span> <span data-ttu-id="5b7bc-119">Varje sträng är en separat bindning, inte en sekvens med nycklar för en enskild bindning.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-119">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

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

### <span data-ttu-id="5b7bc-120">-ViMode</span><span class="sxs-lookup"><span data-stu-id="5b7bc-120">-ViMode</span></span>

<span data-ttu-id="5b7bc-121">Ange vilket läge som bindningen gäller för.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-121">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="5b7bc-122">Möjliga värden är: INSERT, kommando.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-122">Possible values are: Insert, Command.</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b7bc-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b7bc-123">CommonParameters</span></span>

<span data-ttu-id="5b7bc-124">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b7bc-125">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5b7bc-125">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5b7bc-126">INDATA</span><span class="sxs-lookup"><span data-stu-id="5b7bc-126">INPUTS</span></span>

### <span data-ttu-id="5b7bc-127">Inget</span><span class="sxs-lookup"><span data-stu-id="5b7bc-127">None</span></span>

<span data-ttu-id="5b7bc-128">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5b7bc-128">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="5b7bc-129">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5b7bc-129">OUTPUTS</span></span>

### <span data-ttu-id="5b7bc-130">Inget</span><span class="sxs-lookup"><span data-stu-id="5b7bc-130">None</span></span>

## <span data-ttu-id="5b7bc-131">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5b7bc-131">NOTES</span></span>

## <span data-ttu-id="5b7bc-132">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5b7bc-132">RELATED LINKS</span></span>

[<span data-ttu-id="5b7bc-133">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5b7bc-133">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="5b7bc-134">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="5b7bc-134">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="5b7bc-135">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="5b7bc-135">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="5b7bc-136">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="5b7bc-136">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
