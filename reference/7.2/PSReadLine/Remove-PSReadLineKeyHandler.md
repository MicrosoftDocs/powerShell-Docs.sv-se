---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: d280eba2e717ccfb0b896d62f42079390d1db848
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709031"
---
# <span data-ttu-id="36167-102">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="36167-102">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="36167-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="36167-103">SYNOPSIS</span></span>
<span data-ttu-id="36167-104">Tar bort en nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="36167-104">Removes a key binding.</span></span>

## <span data-ttu-id="36167-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36167-105">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="36167-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="36167-106">DESCRIPTION</span></span>

<span data-ttu-id="36167-107">`Remove-PSReadLineKeyHandler`Cmdleten tar bort en angiven nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="36167-107">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="36167-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="36167-108">EXAMPLES</span></span>

### <span data-ttu-id="36167-109">Exempel 1: ta bort en bindning</span><span class="sxs-lookup"><span data-stu-id="36167-109">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="36167-110">Det här kommandot tar bort bindningen från nyckel kombinationen eller ackord `Ctrl+B` .</span><span class="sxs-lookup"><span data-stu-id="36167-110">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="36167-111">`Ctrl+B`Ackord skapas i `Set-PSReadLineKeyHandler` artikeln.</span><span class="sxs-lookup"><span data-stu-id="36167-111">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="36167-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="36167-112">PARAMETERS</span></span>

### <span data-ttu-id="36167-113">– Ackord</span><span class="sxs-lookup"><span data-stu-id="36167-113">-Chord</span></span>

<span data-ttu-id="36167-114">Anger en matris med nycklar eller sekvenser med nycklar som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="36167-114">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="36167-115">En enda bindning anges genom att använda en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="36167-115">A single binding is specified by using a single string.</span></span> <span data-ttu-id="36167-116">Om bindningen är en följd av nycklar separerar du nycklarna med kommatecken, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="36167-116">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="36167-117">Den här parametern accepterar en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="36167-117">This parameter accepts an array of strings.</span></span> <span data-ttu-id="36167-118">Varje sträng är en separat bindning, inte en sekvens med nycklar för en enskild bindning.</span><span class="sxs-lookup"><span data-stu-id="36167-118">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

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

### <span data-ttu-id="36167-119">-ViMode</span><span class="sxs-lookup"><span data-stu-id="36167-119">-ViMode</span></span>

<span data-ttu-id="36167-120">Ange vilket läge som bindningen gäller för.</span><span class="sxs-lookup"><span data-stu-id="36167-120">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="36167-121">Möjliga värden är: INSERT, kommando.</span><span class="sxs-lookup"><span data-stu-id="36167-121">Possible values are: Insert, Command.</span></span>

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

### <span data-ttu-id="36167-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36167-122">CommonParameters</span></span>

<span data-ttu-id="36167-123">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36167-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36167-124">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="36167-124">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36167-125">INDATA</span><span class="sxs-lookup"><span data-stu-id="36167-125">INPUTS</span></span>

### <span data-ttu-id="36167-126">Inga</span><span class="sxs-lookup"><span data-stu-id="36167-126">None</span></span>

<span data-ttu-id="36167-127">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36167-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="36167-128">UTDATA</span><span class="sxs-lookup"><span data-stu-id="36167-128">OUTPUTS</span></span>

### <span data-ttu-id="36167-129">Inga</span><span class="sxs-lookup"><span data-stu-id="36167-129">None</span></span>

## <span data-ttu-id="36167-130">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="36167-130">NOTES</span></span>

## <span data-ttu-id="36167-131">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="36167-131">RELATED LINKS</span></span>

[<span data-ttu-id="36167-132">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="36167-132">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="36167-133">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="36167-133">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="36167-134">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="36167-134">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="36167-135">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="36167-135">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

