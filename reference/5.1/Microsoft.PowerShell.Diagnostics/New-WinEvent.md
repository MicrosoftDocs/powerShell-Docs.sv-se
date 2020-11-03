---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 202d1792769dcdcda7a156621bfc50c89a1a92ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263552"
---
# <span data-ttu-id="5b18a-103">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="5b18a-103">New-WinEvent</span></span>

## <span data-ttu-id="5b18a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5b18a-104">SYNOPSIS</span></span>

<span data-ttu-id="5b18a-105">Skapar en ny Windows-händelse för den angivna händelse leverantören.</span><span class="sxs-lookup"><span data-stu-id="5b18a-105">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="5b18a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b18a-106">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="5b18a-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5b18a-107">DESCRIPTION</span></span>

<span data-ttu-id="5b18a-108">Cmdlet: en **New-WinEvent** skapar en ETW (Event tracing for Windows)-händelse (ETW) för en händelse leverantör.</span><span class="sxs-lookup"><span data-stu-id="5b18a-108">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="5b18a-109">Du kan använda denna cmdlet för att lägga till händelser i ETW-kanaler från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5b18a-109">You can use this cmdlet to add events to ETW channels from Windows PowerShell.</span></span>

## <span data-ttu-id="5b18a-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5b18a-110">EXAMPLES</span></span>

### <span data-ttu-id="5b18a-111">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="5b18a-111">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="5b18a-112">Det här kommandot använder cmdleten **New-WinEvent** för att skapa händelse 45090 för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="5b18a-112">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="5b18a-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5b18a-113">PARAMETERS</span></span>

### <span data-ttu-id="5b18a-114">-ID</span><span class="sxs-lookup"><span data-stu-id="5b18a-114">-Id</span></span>

<span data-ttu-id="5b18a-115">Anger ett händelse-ID som har registrerats via ett Instrumentation-manifest.</span><span class="sxs-lookup"><span data-stu-id="5b18a-115">Specifies an event id that was registered through an instrumentation manifest.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b18a-116">– Nytto Last</span><span class="sxs-lookup"><span data-stu-id="5b18a-116">-Payload</span></span>

<span data-ttu-id="5b18a-117">Anger meddelandet för händelsen.</span><span class="sxs-lookup"><span data-stu-id="5b18a-117">Specifies the message for the event.</span></span> <span data-ttu-id="5b18a-118">När händelsen skrivs till en händelse logg, lagras nytto lasten i händelse objektets **meddelande** egenskap.</span><span class="sxs-lookup"><span data-stu-id="5b18a-118">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="5b18a-119">När den angivna nytto lasten inte matchar nytto lasten i händelse definitionen genererar Windows PowerShell en varning, men kommandot slutförs ändå.</span><span class="sxs-lookup"><span data-stu-id="5b18a-119">When the specified payload does not match the payload in the event definition, Windows PowerShell generates a warning, but the command still succeeds.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b18a-120">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="5b18a-120">-ProviderName</span></span>

<span data-ttu-id="5b18a-121">Anger den Händelseprovidern som skriver händelsen till en händelse logg, till exempel "Microsoft-Windows-PowerShell".</span><span class="sxs-lookup"><span data-stu-id="5b18a-121">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="5b18a-122">En ETW-Händelseprovidern är en logisk entitet som skriver händelser till ETW-sessioner.</span><span class="sxs-lookup"><span data-stu-id="5b18a-122">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b18a-123">-Version</span><span class="sxs-lookup"><span data-stu-id="5b18a-123">-Version</span></span>

<span data-ttu-id="5b18a-124">Anger händelsens versions nummer.</span><span class="sxs-lookup"><span data-stu-id="5b18a-124">Specifies the version number of the event.</span></span> <span data-ttu-id="5b18a-125">Skriv händelse numret.</span><span class="sxs-lookup"><span data-stu-id="5b18a-125">Type the event number.</span></span> <span data-ttu-id="5b18a-126">Windows PowerShell konverterar talet till den typ av byte som krävs.</span><span class="sxs-lookup"><span data-stu-id="5b18a-126">Windows PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="5b18a-127">Med den här parametern kan du ange en händelse när olika versioner av samma händelse definieras.</span><span class="sxs-lookup"><span data-stu-id="5b18a-127">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

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

### <span data-ttu-id="5b18a-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b18a-128">CommonParameters</span></span>

<span data-ttu-id="5b18a-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5b18a-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b18a-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5b18a-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5b18a-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="5b18a-131">INPUTS</span></span>

### <span data-ttu-id="5b18a-132">Inget</span><span class="sxs-lookup"><span data-stu-id="5b18a-132">None</span></span>

<span data-ttu-id="5b18a-133">Den här cmdleten tar inte emot några ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5b18a-133">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="5b18a-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5b18a-134">OUTPUTS</span></span>

### <span data-ttu-id="5b18a-135">Inget</span><span class="sxs-lookup"><span data-stu-id="5b18a-135">None</span></span>

<span data-ttu-id="5b18a-136">Den här cmdleten genererar utdata.</span><span class="sxs-lookup"><span data-stu-id="5b18a-136">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="5b18a-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5b18a-137">NOTES</span></span>

* <span data-ttu-id="5b18a-138">När providern skriver till en EventLog kan du hämta händelsen från händelse loggen med hjälp av cmdleten Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="5b18a-138">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="5b18a-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5b18a-139">RELATED LINKS</span></span>

[<span data-ttu-id="5b18a-140">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="5b18a-140">Get-WinEvent</span></span>](Get-WinEvent.md)
