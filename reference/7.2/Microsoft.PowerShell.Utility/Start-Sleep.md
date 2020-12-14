---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4d06fdd1d5a616c24a4dd7bec10ea4dadea4062
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709732"
---
# <span data-ttu-id="80178-102">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="80178-102">Start-Sleep</span></span>

## <span data-ttu-id="80178-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="80178-103">SYNOPSIS</span></span>
<span data-ttu-id="80178-104">Pausar aktiviteten i ett skript eller en session under den angivna tids perioden.</span><span class="sxs-lookup"><span data-stu-id="80178-104">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="80178-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="80178-105">SYNTAX</span></span>

### <span data-ttu-id="80178-106">Sekunder (standard)</span><span class="sxs-lookup"><span data-stu-id="80178-106">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="80178-107">Millisekunder</span><span class="sxs-lookup"><span data-stu-id="80178-107">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="80178-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="80178-108">DESCRIPTION</span></span>

<span data-ttu-id="80178-109">`Start-Sleep`Cmdleten pausar aktiviteten i ett skript eller en session under den angivna tids perioden.</span><span class="sxs-lookup"><span data-stu-id="80178-109">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="80178-110">Du kan använda det för många aktiviteter, till exempel vänta på att en åtgärd ska slutföras eller pausas innan en åtgärd upprepas.</span><span class="sxs-lookup"><span data-stu-id="80178-110">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="80178-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="80178-111">EXAMPLES</span></span>

### <span data-ttu-id="80178-112">Exempel 1: vila alla kommandon i 15 sekunder</span><span class="sxs-lookup"><span data-stu-id="80178-112">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="80178-113">Exempel 2: vila alla kommandon i 1,5 sekunder</span><span class="sxs-lookup"><span data-stu-id="80178-113">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="80178-114">Det här exemplet gör alla kommandon i sessionen i vilo läge för en och en halv på en sekund.</span><span class="sxs-lookup"><span data-stu-id="80178-114">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="80178-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="80178-115">PARAMETERS</span></span>

### <span data-ttu-id="80178-116">– Millisekunder</span><span class="sxs-lookup"><span data-stu-id="80178-116">-Milliseconds</span></span>

<span data-ttu-id="80178-117">Anger hur länge resursen är i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="80178-117">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="80178-118">Parametern kan vara förkortad som **m**.</span><span class="sxs-lookup"><span data-stu-id="80178-118">The parameter can be abbreviated as **m**.</span></span>

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

### <span data-ttu-id="80178-119">– Sekunder</span><span class="sxs-lookup"><span data-stu-id="80178-119">-Seconds</span></span>

<span data-ttu-id="80178-120">Anger hur länge resursen är i sekunder.</span><span class="sxs-lookup"><span data-stu-id="80178-120">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="80178-121">Du kan utelämna parameter namnet eller så kan du förkorta det som **s**.</span><span class="sxs-lookup"><span data-stu-id="80178-121">You can omit the parameter name or you can abbreviate it as **s**.</span></span> <span data-ttu-id="80178-122">Från och med PowerShell-6.2.0 accepterar den här parametern nu bråk värden.</span><span class="sxs-lookup"><span data-stu-id="80178-122">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

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

### <span data-ttu-id="80178-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="80178-123">CommonParameters</span></span>

<span data-ttu-id="80178-124">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="80178-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="80178-125">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="80178-125">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="80178-126">INDATA</span><span class="sxs-lookup"><span data-stu-id="80178-126">INPUTS</span></span>

### <span data-ttu-id="80178-127">System. Int32</span><span class="sxs-lookup"><span data-stu-id="80178-127">System.Int32</span></span>

<span data-ttu-id="80178-128">Du kan skicka vidare antalet sekunder till `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="80178-128">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="80178-129">UTDATA</span><span class="sxs-lookup"><span data-stu-id="80178-129">OUTPUTS</span></span>

### <span data-ttu-id="80178-130">Inga</span><span class="sxs-lookup"><span data-stu-id="80178-130">None</span></span>

<span data-ttu-id="80178-131">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="80178-131">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="80178-132">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="80178-132">NOTES</span></span>

- <span data-ttu-id="80178-133">Du kan också referera till `Start-Sleep` med dess inbyggda alias `sleep` .</span><span class="sxs-lookup"><span data-stu-id="80178-133">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="80178-134">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="80178-134">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="80178-135">`Ctrl+C` slutar på `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="80178-135">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="80178-136">`Ctrl+C` delas inte ut från `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="80178-136">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="80178-137">Mer information finns i [metoden Thread. vilo läge](/dotnet/api/system.threading.thread.sleep).</span><span class="sxs-lookup"><span data-stu-id="80178-137">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="80178-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="80178-138">RELATED LINKS</span></span>

