---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 8e64c3e3a782fadf1669f1310d1615f3a014ccee
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262130"
---
# <span data-ttu-id="aa1e2-103">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="aa1e2-103">New-WinEvent</span></span>

## <span data-ttu-id="aa1e2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aa1e2-104">SYNOPSIS</span></span>
<span data-ttu-id="aa1e2-105">Skapar en ny Windows-händelse för den angivna händelse leverantören.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-105">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="aa1e2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aa1e2-106">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="aa1e2-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aa1e2-107">DESCRIPTION</span></span>

<span data-ttu-id="aa1e2-108">Cmdlet: en **New-WinEvent** skapar en ETW (Event tracing for Windows)-händelse (ETW) för en händelse leverantör.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-108">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="aa1e2-109">Du kan använda denna cmdlet för att lägga till händelser till ETW-kanaler från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-109">You can use this cmdlet to add events to ETW channels from PowerShell.</span></span>

## <span data-ttu-id="aa1e2-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aa1e2-110">EXAMPLES</span></span>

### <span data-ttu-id="aa1e2-111">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="aa1e2-111">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="aa1e2-112">Det här kommandot använder cmdleten **New-WinEvent** för att skapa händelse 45090 för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-112">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="aa1e2-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aa1e2-113">PARAMETERS</span></span>

### <span data-ttu-id="aa1e2-114">-ID</span><span class="sxs-lookup"><span data-stu-id="aa1e2-114">-Id</span></span>

<span data-ttu-id="aa1e2-115">Anger ett händelse-ID som har registrerats via ett Instrumentation-manifest.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-115">Specifies an event id that was registered through an instrumentation manifest.</span></span>

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

### <span data-ttu-id="aa1e2-116">– Nytto Last</span><span class="sxs-lookup"><span data-stu-id="aa1e2-116">-Payload</span></span>

<span data-ttu-id="aa1e2-117">Anger meddelandet för händelsen.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-117">Specifies the message for the event.</span></span> <span data-ttu-id="aa1e2-118">När händelsen skrivs till en händelse logg, lagras nytto lasten i händelse objektets **meddelande** egenskap.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-118">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="aa1e2-119">När den angivna nytto lasten inte matchar nytto lasten i händelse definitionen genererar PowerShell en varning, men kommandot slutförs fortfarande.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-119">When the specified payload does not match the payload in the event definition, PowerShell generates a warning, but the command still succeeds.</span></span>

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

### <span data-ttu-id="aa1e2-120">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="aa1e2-120">-ProviderName</span></span>

<span data-ttu-id="aa1e2-121">Anger den Händelseprovidern som skriver händelsen till en händelse logg, till exempel "Microsoft-Windows-PowerShell".</span><span class="sxs-lookup"><span data-stu-id="aa1e2-121">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="aa1e2-122">En ETW-Händelseprovidern är en logisk entitet som skriver händelser till ETW-sessioner.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-122">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

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

### <span data-ttu-id="aa1e2-123">-Version</span><span class="sxs-lookup"><span data-stu-id="aa1e2-123">-Version</span></span>

<span data-ttu-id="aa1e2-124">Anger händelsens versions nummer.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-124">Specifies the version number of the event.</span></span> <span data-ttu-id="aa1e2-125">Skriv händelse numret.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-125">Type the event number.</span></span> <span data-ttu-id="aa1e2-126">PowerShell konverterar talet till den typ av byte som krävs.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-126">PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="aa1e2-127">Med den här parametern kan du ange en händelse när olika versioner av samma händelse definieras.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-127">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

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

### <span data-ttu-id="aa1e2-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa1e2-128">CommonParameters</span></span>

<span data-ttu-id="aa1e2-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa1e2-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aa1e2-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aa1e2-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="aa1e2-131">INPUTS</span></span>

### <span data-ttu-id="aa1e2-132">Inget</span><span class="sxs-lookup"><span data-stu-id="aa1e2-132">None</span></span>

<span data-ttu-id="aa1e2-133">Den här cmdleten tar inte emot några ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-133">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="aa1e2-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aa1e2-134">OUTPUTS</span></span>

### <span data-ttu-id="aa1e2-135">Inget</span><span class="sxs-lookup"><span data-stu-id="aa1e2-135">None</span></span>

<span data-ttu-id="aa1e2-136">Den här cmdleten genererar utdata.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-136">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="aa1e2-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="aa1e2-137">NOTES</span></span>

* <span data-ttu-id="aa1e2-138">När providern skriver till en EventLog kan du hämta händelsen från händelse loggen med hjälp av cmdleten Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="aa1e2-138">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="aa1e2-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="aa1e2-139">RELATED LINKS</span></span>

[<span data-ttu-id="aa1e2-140">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="aa1e2-140">Get-WinEvent</span></span>](Get-WinEvent.md)
