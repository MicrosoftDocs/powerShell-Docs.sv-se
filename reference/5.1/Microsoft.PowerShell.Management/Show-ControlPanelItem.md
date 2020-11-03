---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265370"
---
# <span data-ttu-id="02423-103">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="02423-103">Show-ControlPanelItem</span></span>

## <span data-ttu-id="02423-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="02423-104">SYNOPSIS</span></span>
<span data-ttu-id="02423-105">Öppnar kontroll panels objekt.</span><span class="sxs-lookup"><span data-stu-id="02423-105">Opens control panel items.</span></span>

## <span data-ttu-id="02423-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="02423-106">SYNTAX</span></span>

### <span data-ttu-id="02423-107">RegularName (standard)</span><span class="sxs-lookup"><span data-stu-id="02423-107">RegularName (Default)</span></span>

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="02423-108">CanonicalName</span><span class="sxs-lookup"><span data-stu-id="02423-108">CanonicalName</span></span>

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="02423-109">ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="02423-109">ControlPanelItem</span></span>

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## <span data-ttu-id="02423-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="02423-110">DESCRIPTION</span></span>

<span data-ttu-id="02423-111">`Show-ControlPanelItem`Cmdlet: en öppnar objekt på kontroll panelen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="02423-111">The `Show-ControlPanelItem` cmdlet opens control panel items on the local computer.</span></span> <span data-ttu-id="02423-112">Du kan använda den för att öppna kontroll panels objekt efter namn, kategori eller beskrivning, även på system som inte har något användar gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="02423-112">You can use it to open control panel items by name, category, or description, even on systems that do not have a user interface.</span></span> <span data-ttu-id="02423-113">Du kan skicka vidare till kontroll panels objekt från `Get-ControlPanelItem` cmdleten till `Show-ControlPanelItem` .</span><span class="sxs-lookup"><span data-stu-id="02423-113">You can pipe control panel items from the `Get-ControlPanelItem` cmdlet to `Show-ControlPanelItem`.</span></span>

<span data-ttu-id="02423-114">`Show-ControlPanelItem` söker endast efter objekt på kontroll panelen som kan öppnas i systemet.</span><span class="sxs-lookup"><span data-stu-id="02423-114">`Show-ControlPanelItem` searches only control panel items that can be opened on the system.</span></span> <span data-ttu-id="02423-115">På datorer som inte har **kontroll panelen** eller **Utforskaren** `Show-ControlPanelItem` söker sökningen endast på kontroll panelens objekt som kan öppnas utan de här komponenterna.</span><span class="sxs-lookup"><span data-stu-id="02423-115">On computers that do not have **Control Panel** or **File Explorer** , `Show-ControlPanelItem` searches only control panel items that can open without these components.</span></span>

<span data-ttu-id="02423-116">Denna cmdlet introducerades i Windows PowerShell 3,0 och fungerar på Windows 8, Windows Server 2012 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="02423-116">This cmdlet was introduced in Windows PowerShell 3.0 and works on Windows 8, Windows Server 2012, and higher versions.</span></span>

## <span data-ttu-id="02423-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="02423-117">EXAMPLES</span></span>

### <span data-ttu-id="02423-118">Exempel 1: Visa ett kontroll panels objekt</span><span class="sxs-lookup"><span data-stu-id="02423-118">Example 1: Show a control panel item</span></span>

<span data-ttu-id="02423-119">I det här exemplet öppnas alternativet **spela upp automatiskt** på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="02423-119">This example launches the **AutoPlay** control panel item.</span></span>

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### <span data-ttu-id="02423-120">Exempel 2: Skicka ett objekt till en kontroll panel till denna cmdlet</span><span class="sxs-lookup"><span data-stu-id="02423-120">Example 2: Pipe a control panel item to this cmdlet</span></span>

<span data-ttu-id="02423-121">I det här exemplet öppnas objekt på kontroll panelen i **Windows Defender-brandväggen** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="02423-121">This example opens the **Windows Defender Firewall** control panel item on the local computer.</span></span>
<span data-ttu-id="02423-122">Namnet på kontroll panelens objekt i Windows-brandväggen har ändrats i Windows-brandväggens versioner.</span><span class="sxs-lookup"><span data-stu-id="02423-122">The name of the Windows Firewall control panel item has changed over the versions of Windows.</span></span> <span data-ttu-id="02423-123">Det här exemplet använder ett mönster för jokertecken för att hitta kontroll panelens objekt.</span><span class="sxs-lookup"><span data-stu-id="02423-123">This example uses a wildcard pattern to find the control panel item.</span></span>

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="02423-124">`Get-ControlPanelItem` hämtar kontroll panels objekt och `Show-ControlPanelItem` cmdlet: en öppnar den.</span><span class="sxs-lookup"><span data-stu-id="02423-124">`Get-ControlPanelItem` gets the control panel item and the `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="02423-125">Exempel 3: Använd ett fil namn för att öppna ett kontroll panels objekt</span><span class="sxs-lookup"><span data-stu-id="02423-125">Example 3: Use a file name to open a control panel item</span></span>

<span data-ttu-id="02423-126">I det här exemplet öppnas objekt på kontroll panelen **program och funktioner** med hjälp av dess program namn.</span><span class="sxs-lookup"><span data-stu-id="02423-126">This example opens the **Programs and Features** control panel item by using its application name.</span></span>

```powershell
appwiz.cpl
```

<span data-ttu-id="02423-127">Den här metoden är ett alternativ till att använda ett `Show-ControlPanelItem` kommando.</span><span class="sxs-lookup"><span data-stu-id="02423-127">This method is an alternative to using a `Show-ControlPanelItem` command.</span></span>

> [!NOTE]
> <span data-ttu-id="02423-128">I PowerShell kan du utelämna fil namns tillägget. cpl för kontroll panels filer eftersom det ingår i värdet för `$env:PathExt` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="02423-128">In PowerShell, you can omit the .cpl file extension for control panel files because it's included in the value of the `$env:PathExt` environment variable.</span></span>

## <span data-ttu-id="02423-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="02423-129">PARAMETERS</span></span>

### <span data-ttu-id="02423-130">– CanonicalName</span><span class="sxs-lookup"><span data-stu-id="02423-130">-CanonicalName</span></span>

<span data-ttu-id="02423-131">Anger objekt på kontroll panelen genom att använda de angivna kanoniska namnen eller namn mönstren.</span><span class="sxs-lookup"><span data-stu-id="02423-131">Specifies control panel items by using the specified canonical names or name patterns.</span></span> <span data-ttu-id="02423-132">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="02423-132">Wildcard characters are permitted.</span></span> <span data-ttu-id="02423-133">Om du anger flera namn öppnar denna cmdlet kontroll panels objekt som matchar något av namnen, som om objekten i namn listan skiljdes åt av en **or** -operator.</span><span class="sxs-lookup"><span data-stu-id="02423-133">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="02423-134">– InputObject</span><span class="sxs-lookup"><span data-stu-id="02423-134">-InputObject</span></span>

<span data-ttu-id="02423-135">Anger vilka kontroll panels objekt som ska öppnas genom att skicka objekt på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="02423-135">Specifies control panel items to open by submitting control panel item objects.</span></span> <span data-ttu-id="02423-136">Ange en variabel som innehåller objekt på kontroll panelen eller Skriv ett kommando eller uttryck som hämtar objekt på kontroll panelen, till exempel `Get-ControlPanelItem` .</span><span class="sxs-lookup"><span data-stu-id="02423-136">Enter a variable that contains control panel item objects, or type a command or expression that gets control panel item objects, such as `Get-ControlPanelItem`.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="02423-137">-Name</span><span class="sxs-lookup"><span data-stu-id="02423-137">-Name</span></span>

<span data-ttu-id="02423-138">Anger namn på kontroll panels objekt.</span><span class="sxs-lookup"><span data-stu-id="02423-138">Specifies names of control panel items.</span></span> <span data-ttu-id="02423-139">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="02423-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="02423-140">Om du anger flera namn öppnar denna cmdlet kontroll panels objekt som matchar något av namnen, som om objekten i namn listan skiljdes åt av en **or** -operator.</span><span class="sxs-lookup"><span data-stu-id="02423-140">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="02423-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="02423-141">CommonParameters</span></span>

<span data-ttu-id="02423-142">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="02423-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="02423-143">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="02423-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="02423-144">INDATA</span><span class="sxs-lookup"><span data-stu-id="02423-144">INPUTS</span></span>

### <span data-ttu-id="02423-145">System. String, Microsoft. PowerShell. commands. ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="02423-145">System.String, Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="02423-146">Du kan skicka ett objekt av namnet eller kontroll panelen objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02423-146">You can pipe a name or control panel item object to this cmdlet.</span></span>

## <span data-ttu-id="02423-147">UTDATA</span><span class="sxs-lookup"><span data-stu-id="02423-147">OUTPUTS</span></span>

### <span data-ttu-id="02423-148">Inget</span><span class="sxs-lookup"><span data-stu-id="02423-148">None</span></span>

<span data-ttu-id="02423-149">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="02423-149">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="02423-150">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="02423-150">NOTES</span></span>

## <span data-ttu-id="02423-151">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="02423-151">RELATED LINKS</span></span>

[<span data-ttu-id="02423-152">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="02423-152">Get-ControlPanelItem</span></span>](Get-ControlPanelItem.md)
