---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 5b4b150a1c02e5d0689b44db9b2a984e297db766
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710872"
---
# <span data-ttu-id="65f48-102">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="65f48-102">New-WinEvent</span></span>

## <span data-ttu-id="65f48-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="65f48-103">SYNOPSIS</span></span>
<span data-ttu-id="65f48-104">Skapar en ny Windows-händelse för den angivna händelse leverantören.</span><span class="sxs-lookup"><span data-stu-id="65f48-104">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="65f48-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="65f48-105">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="65f48-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="65f48-106">DESCRIPTION</span></span>

<span data-ttu-id="65f48-107">Cmdlet: en **New-WinEvent** skapar en ETW (Event tracing for Windows)-händelse (ETW) för en händelse leverantör.</span><span class="sxs-lookup"><span data-stu-id="65f48-107">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="65f48-108">Du kan använda denna cmdlet för att lägga till händelser till ETW-kanaler från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65f48-108">You can use this cmdlet to add events to ETW channels from PowerShell.</span></span>

## <span data-ttu-id="65f48-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="65f48-109">EXAMPLES</span></span>

### <span data-ttu-id="65f48-110">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="65f48-110">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="65f48-111">Det här kommandot använder cmdleten **New-WinEvent** för att skapa händelse 45090 för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="65f48-111">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="65f48-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="65f48-112">PARAMETERS</span></span>

### <span data-ttu-id="65f48-113">-ID</span><span class="sxs-lookup"><span data-stu-id="65f48-113">-Id</span></span>

<span data-ttu-id="65f48-114">Anger ett händelse-ID som har registrerats via ett Instrumentation-manifest.</span><span class="sxs-lookup"><span data-stu-id="65f48-114">Specifies an event id that was registered through an instrumentation manifest.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="65f48-115">– Nytto Last</span><span class="sxs-lookup"><span data-stu-id="65f48-115">-Payload</span></span>

<span data-ttu-id="65f48-116">Anger meddelandet för händelsen.</span><span class="sxs-lookup"><span data-stu-id="65f48-116">Specifies the message for the event.</span></span> <span data-ttu-id="65f48-117">När händelsen skrivs till en händelse logg, lagras nytto lasten i händelse objektets **meddelande** egenskap.</span><span class="sxs-lookup"><span data-stu-id="65f48-117">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="65f48-118">När den angivna nytto lasten inte matchar nytto lasten i händelse definitionen genererar PowerShell en varning, men kommandot slutförs fortfarande.</span><span class="sxs-lookup"><span data-stu-id="65f48-118">When the specified payload does not match the payload in the event definition, PowerShell generates a warning, but the command still succeeds.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="65f48-119">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="65f48-119">-ProviderName</span></span>

<span data-ttu-id="65f48-120">Anger den Händelseprovidern som skriver händelsen till en händelse logg, till exempel "Microsoft-Windows-PowerShell".</span><span class="sxs-lookup"><span data-stu-id="65f48-120">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="65f48-121">En ETW-Händelseprovidern är en logisk entitet som skriver händelser till ETW-sessioner.</span><span class="sxs-lookup"><span data-stu-id="65f48-121">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="65f48-122">-Version</span><span class="sxs-lookup"><span data-stu-id="65f48-122">-Version</span></span>

<span data-ttu-id="65f48-123">Anger händelsens versions nummer.</span><span class="sxs-lookup"><span data-stu-id="65f48-123">Specifies the version number of the event.</span></span> <span data-ttu-id="65f48-124">Skriv händelse numret.</span><span class="sxs-lookup"><span data-stu-id="65f48-124">Type the event number.</span></span> <span data-ttu-id="65f48-125">PowerShell konverterar talet till den typ av byte som krävs.</span><span class="sxs-lookup"><span data-stu-id="65f48-125">PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="65f48-126">Med den här parametern kan du ange en händelse när olika versioner av samma händelse definieras.</span><span class="sxs-lookup"><span data-stu-id="65f48-126">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

```yaml
Type: System.Byte
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="65f48-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="65f48-127">CommonParameters</span></span>

<span data-ttu-id="65f48-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="65f48-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="65f48-129">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="65f48-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="65f48-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="65f48-130">INPUTS</span></span>

### <span data-ttu-id="65f48-131">Inga</span><span class="sxs-lookup"><span data-stu-id="65f48-131">None</span></span>

<span data-ttu-id="65f48-132">Den här cmdleten tar inte emot några ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="65f48-132">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="65f48-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="65f48-133">OUTPUTS</span></span>

### <span data-ttu-id="65f48-134">Inga</span><span class="sxs-lookup"><span data-stu-id="65f48-134">None</span></span>

<span data-ttu-id="65f48-135">Den här cmdleten genererar utdata.</span><span class="sxs-lookup"><span data-stu-id="65f48-135">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="65f48-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="65f48-136">NOTES</span></span>

* <span data-ttu-id="65f48-137">När providern skriver till en EventLog kan du hämta händelsen från händelse loggen med hjälp av cmdleten Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="65f48-137">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="65f48-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="65f48-138">RELATED LINKS</span></span>

[<span data-ttu-id="65f48-139">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="65f48-139">Get-WinEvent</span></span>](Get-WinEvent.md)

