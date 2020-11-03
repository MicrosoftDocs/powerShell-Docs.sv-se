---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 3/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4add39c09b6123aaf8c9302529346a6b1dec391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264825"
---
# <span data-ttu-id="4ca93-103">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="4ca93-103">Start-Sleep</span></span>

## <span data-ttu-id="4ca93-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4ca93-104">SYNOPSIS</span></span>
<span data-ttu-id="4ca93-105">Pausar aktiviteten i ett skript eller en session under den angivna tids perioden.</span><span class="sxs-lookup"><span data-stu-id="4ca93-105">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="4ca93-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4ca93-106">SYNTAX</span></span>

### <span data-ttu-id="4ca93-107">Sekunder (standard)</span><span class="sxs-lookup"><span data-stu-id="4ca93-107">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="4ca93-108">Millisekunder</span><span class="sxs-lookup"><span data-stu-id="4ca93-108">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="4ca93-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4ca93-109">DESCRIPTION</span></span>

<span data-ttu-id="4ca93-110">`Start-Sleep`Cmdleten pausar aktiviteten i ett skript eller en session under den angivna tids perioden.</span><span class="sxs-lookup"><span data-stu-id="4ca93-110">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span>
<span data-ttu-id="4ca93-111">Du kan använda det för många aktiviteter, till exempel vänta på att en åtgärd ska slutföras eller pausas innan en åtgärd upprepas.</span><span class="sxs-lookup"><span data-stu-id="4ca93-111">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="4ca93-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4ca93-112">EXAMPLES</span></span>

### <span data-ttu-id="4ca93-113">Exempel 1: vila alla kommandon i 15 sekunder</span><span class="sxs-lookup"><span data-stu-id="4ca93-113">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

<span data-ttu-id="4ca93-114">Det här kommandot gör alla kommandon i sessionen i vilo läge i 15 sekunder.</span><span class="sxs-lookup"><span data-stu-id="4ca93-114">This command makes all commands in the session sleep for 15 seconds.</span></span>

### <span data-ttu-id="4ca93-115">Exempel 2: vila alla kommandon</span><span class="sxs-lookup"><span data-stu-id="4ca93-115">Example 2: Sleep all commands</span></span>

```powershell
Start-Sleep -m 500
```

<span data-ttu-id="4ca93-116">Det här kommandot gör alla kommandon i sessionen i vilo läge för en halv i en sekund (500 millisekunder).</span><span class="sxs-lookup"><span data-stu-id="4ca93-116">This command makes all the commands in the session sleep for one-half of a second (500 milliseconds).</span></span>

## <span data-ttu-id="4ca93-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4ca93-117">PARAMETERS</span></span>

### <span data-ttu-id="4ca93-118">– Millisekunder</span><span class="sxs-lookup"><span data-stu-id="4ca93-118">-Milliseconds</span></span>

<span data-ttu-id="4ca93-119">Anger hur länge resursen är i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="4ca93-119">Specifies how long the resource sleeps in milliseconds.</span></span>
<span data-ttu-id="4ca93-120">Parametern kan vara förkortad som **m**.</span><span class="sxs-lookup"><span data-stu-id="4ca93-120">The parameter can be abbreviated as **m**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4ca93-121">– Sekunder</span><span class="sxs-lookup"><span data-stu-id="4ca93-121">-Seconds</span></span>

<span data-ttu-id="4ca93-122">Anger hur länge resursen är i sekunder.</span><span class="sxs-lookup"><span data-stu-id="4ca93-122">Specifies how long the resource sleeps in seconds.</span></span>
<span data-ttu-id="4ca93-123">Du kan utelämna parameter namnet ( **sekunder** ) eller så kan du förkorta det som **s**.</span><span class="sxs-lookup"><span data-stu-id="4ca93-123">You can omit the parameter name ( **Seconds** ), or you can abbreviate it as **s**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4ca93-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4ca93-124">CommonParameters</span></span>

<span data-ttu-id="4ca93-125">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4ca93-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4ca93-126">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4ca93-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4ca93-127">INDATA</span><span class="sxs-lookup"><span data-stu-id="4ca93-127">INPUTS</span></span>

### <span data-ttu-id="4ca93-128">System. Int32</span><span class="sxs-lookup"><span data-stu-id="4ca93-128">System.Int32</span></span>

<span data-ttu-id="4ca93-129">Du kan skicka vidare antalet sekunder till `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="4ca93-129">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="4ca93-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4ca93-130">OUTPUTS</span></span>

### <span data-ttu-id="4ca93-131">Inget</span><span class="sxs-lookup"><span data-stu-id="4ca93-131">None</span></span>

<span data-ttu-id="4ca93-132">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4ca93-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="4ca93-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4ca93-133">NOTES</span></span>

- <span data-ttu-id="4ca93-134">Du kan också referera till `Start-Sleep` med dess inbyggda alias `sleep` .</span><span class="sxs-lookup"><span data-stu-id="4ca93-134">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="4ca93-135">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="4ca93-135">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="4ca93-136">`Ctrl+C` slutar på `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="4ca93-136">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="4ca93-137">`Ctrl+C` delas inte ut från `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="4ca93-137">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="4ca93-138">Mer information finns i [metoden Thread. vilo läge](/dotnet/api/system.threading.thread.sleep).</span><span class="sxs-lookup"><span data-stu-id="4ca93-138">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="4ca93-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4ca93-139">RELATED LINKS</span></span>
