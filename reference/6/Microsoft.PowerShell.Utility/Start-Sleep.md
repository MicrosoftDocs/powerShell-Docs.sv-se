---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: 1a107b2e4c7414250154d576d6dc9554cb9d800b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266721"
---
# <span data-ttu-id="38a15-103">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="38a15-103">Start-Sleep</span></span>

## <span data-ttu-id="38a15-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="38a15-104">SYNOPSIS</span></span>
<span data-ttu-id="38a15-105">Pausar aktiviteten i ett skript eller en session under den angivna tids perioden.</span><span class="sxs-lookup"><span data-stu-id="38a15-105">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="38a15-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="38a15-106">SYNTAX</span></span>

### <span data-ttu-id="38a15-107">Sekunder (standard)</span><span class="sxs-lookup"><span data-stu-id="38a15-107">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="38a15-108">Millisekunder</span><span class="sxs-lookup"><span data-stu-id="38a15-108">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="38a15-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="38a15-109">DESCRIPTION</span></span>

<span data-ttu-id="38a15-110">`Start-Sleep`Cmdleten pausar aktiviteten i ett skript eller en session under den angivna tids perioden.</span><span class="sxs-lookup"><span data-stu-id="38a15-110">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="38a15-111">Du kan använda det för många aktiviteter, till exempel vänta på att en åtgärd ska slutföras eller pausas innan en åtgärd upprepas.</span><span class="sxs-lookup"><span data-stu-id="38a15-111">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="38a15-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="38a15-112">EXAMPLES</span></span>

### <span data-ttu-id="38a15-113">Exempel 1: vila alla kommandon i 15 sekunder</span><span class="sxs-lookup"><span data-stu-id="38a15-113">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="38a15-114">Exempel 2: vila alla kommandon i 1,5 sekunder</span><span class="sxs-lookup"><span data-stu-id="38a15-114">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="38a15-115">Det här exemplet gör alla kommandon i sessionen i vilo läge för en och en halv på en sekund.</span><span class="sxs-lookup"><span data-stu-id="38a15-115">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="38a15-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="38a15-116">PARAMETERS</span></span>

### <span data-ttu-id="38a15-117">– Millisekunder</span><span class="sxs-lookup"><span data-stu-id="38a15-117">-Milliseconds</span></span>

<span data-ttu-id="38a15-118">Anger hur länge resursen är i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="38a15-118">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="38a15-119">Parametern kan vara förkortad som **m**.</span><span class="sxs-lookup"><span data-stu-id="38a15-119">The parameter can be abbreviated as **m**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="38a15-120">– Sekunder</span><span class="sxs-lookup"><span data-stu-id="38a15-120">-Seconds</span></span>

<span data-ttu-id="38a15-121">Anger hur länge resursen är i sekunder.</span><span class="sxs-lookup"><span data-stu-id="38a15-121">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="38a15-122">Du kan utelämna parameter namnet eller så kan du förkorta det som **s**.</span><span class="sxs-lookup"><span data-stu-id="38a15-122">You can omit the parameter name or you can abbreviate it as **s**.</span></span> <span data-ttu-id="38a15-123">Från och med PowerShell-6.2.0 accepterar den här parametern nu bråk värden.</span><span class="sxs-lookup"><span data-stu-id="38a15-123">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="38a15-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38a15-124">CommonParameters</span></span>

<span data-ttu-id="38a15-125">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38a15-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38a15-126">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="38a15-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="38a15-127">INDATA</span><span class="sxs-lookup"><span data-stu-id="38a15-127">INPUTS</span></span>

### <span data-ttu-id="38a15-128">System. Int32</span><span class="sxs-lookup"><span data-stu-id="38a15-128">System.Int32</span></span>

<span data-ttu-id="38a15-129">Du kan skicka vidare antalet sekunder till `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="38a15-129">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="38a15-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="38a15-130">OUTPUTS</span></span>

### <span data-ttu-id="38a15-131">Inget</span><span class="sxs-lookup"><span data-stu-id="38a15-131">None</span></span>

<span data-ttu-id="38a15-132">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="38a15-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="38a15-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="38a15-133">NOTES</span></span>

- <span data-ttu-id="38a15-134">Du kan också referera till `Start-Sleep` med dess inbyggda alias `sleep` .</span><span class="sxs-lookup"><span data-stu-id="38a15-134">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="38a15-135">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="38a15-135">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="38a15-136">`Ctrl+C` slutar på `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="38a15-136">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="38a15-137">`Ctrl+C` delas inte ut från `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="38a15-137">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="38a15-138">Mer information finns i [metoden Thread. vilo läge](/dotnet/api/system.threading.thread.sleep).</span><span class="sxs-lookup"><span data-stu-id="38a15-138">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="38a15-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="38a15-139">RELATED LINKS</span></span>
