---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266168"
---
# <span data-ttu-id="aacf5-103">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="aacf5-103">Get-ControlPanelItem</span></span>

## <span data-ttu-id="aacf5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aacf5-104">SYNOPSIS</span></span>
<span data-ttu-id="aacf5-105">Hämtar objekt på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="aacf5-105">Gets control panel items.</span></span>

## <span data-ttu-id="aacf5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aacf5-106">SYNTAX</span></span>

### <span data-ttu-id="aacf5-107">RegularName (standard)</span><span class="sxs-lookup"><span data-stu-id="aacf5-107">RegularName (Default)</span></span>

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="aacf5-108">CanonicalName</span><span class="sxs-lookup"><span data-stu-id="aacf5-108">CanonicalName</span></span>

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="aacf5-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aacf5-109">DESCRIPTION</span></span>

<span data-ttu-id="aacf5-110">`Get-ControlPanelItem`Cmdlet: en hämtar objekt på kontroll panelen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="aacf5-110">The `Get-ControlPanelItem` cmdlet gets control panel items on the local computer.</span></span> <span data-ttu-id="aacf5-111">Du kan använda den för att hitta objekt på kontroll panelen efter namn, kategori eller beskrivning, även på system som inte har något användar gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="aacf5-111">You can use it to find control panel items by name, category, or description, even on systems that do not have a user interface.</span></span>

<span data-ttu-id="aacf5-112">Denna cmdlet hämtar bara objekt på kontroll panelen som kan öppnas i systemet.</span><span class="sxs-lookup"><span data-stu-id="aacf5-112">This cmdlet gets only the control panel items that can be opened on the system.</span></span> <span data-ttu-id="aacf5-113">På datorer som inte har kontroll panelen eller Utforskaren, hämtar denna cmdlet endast kontroll panels objekt som kan öppnas utan dessa komponenter.</span><span class="sxs-lookup"><span data-stu-id="aacf5-113">On computers that do not have Control Panel or File Explorer, this cmdlet gets only control panel items that can open without these components.</span></span>

<span data-ttu-id="aacf5-114">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aacf5-114">This cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="aacf5-115">Det fungerar bara på Windows 8 och Windows Server 2012 och senare.</span><span class="sxs-lookup"><span data-stu-id="aacf5-115">It works only on Windows 8 and Windows Server 2012 and newer.</span></span>

## <span data-ttu-id="aacf5-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aacf5-116">EXAMPLES</span></span>

### <span data-ttu-id="aacf5-117">Exempel 1: Hämta alla objekt på kontroll panelen</span><span class="sxs-lookup"><span data-stu-id="aacf5-117">Example 1: Get all control panel items</span></span>

<span data-ttu-id="aacf5-118">Det här kommandot hämtar alla objekt på kontroll panelen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="aacf5-118">This command gets all control panel items on the local computer.</span></span>

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### <span data-ttu-id="aacf5-119">Exempel 2: Hämta objekt på kontroll panelen efter namn</span><span class="sxs-lookup"><span data-stu-id="aacf5-119">Example 2: Get control panel items by name</span></span>

<span data-ttu-id="aacf5-120">I det här exemplet får du kontroll panels objekt som har program eller appar i sina namn.</span><span class="sxs-lookup"><span data-stu-id="aacf5-120">This example gets control panel items that have Program or App in their names.</span></span>

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### <span data-ttu-id="aacf5-121">Exempel 3: Hämta objekt på kontroll panelen efter kategori</span><span class="sxs-lookup"><span data-stu-id="aacf5-121">Example 3: Get control panel items by category</span></span>

<span data-ttu-id="aacf5-122">Det här kommandot hämtar alla kontroll panels objekt i kategorier som har säkerhet i sina namn.</span><span class="sxs-lookup"><span data-stu-id="aacf5-122">This command gets all control panel items in categories that have Security in their names.</span></span>

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### <span data-ttu-id="aacf5-123">Exempel 4: öppna ett kontroll panels objekt</span><span class="sxs-lookup"><span data-stu-id="aacf5-123">Example 4: Open a control panel item</span></span>

<span data-ttu-id="aacf5-124">I det här exemplet öppnas objekt på kontroll panelen i Windows-brandväggen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="aacf5-124">This example opens the Windows Firewall control panel item on the local computer.</span></span>

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="aacf5-125">`Get-ControlPanelItem`Cmdlet: en hämtar kontroll panels objekt.</span><span class="sxs-lookup"><span data-stu-id="aacf5-125">The `Get-ControlPanelItem` cmdlet gets the control panel item.</span></span> <span data-ttu-id="aacf5-126">`Show-ControlPanelItem`Cmdlet: en öppnar den.</span><span class="sxs-lookup"><span data-stu-id="aacf5-126">The `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="aacf5-127">Exempel 5: Hämta kontroll panels objekt på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="aacf5-127">Example 5: Get control panel items on a remote computer</span></span>

<span data-ttu-id="aacf5-128">Det här exemplet hämtar BitLocker-diskkryptering kontroll panels objekt på den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="aacf5-128">This example gets the BitLocker Drive Encryption control panel item on the Server01 remote computer.</span></span>
<span data-ttu-id="aacf5-129">`Invoke-Command`Cmdlet: en Fjärrkör `Get-ControlPanelItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aacf5-129">The `Invoke-Command` cmdlet runs the `Get-ControlPanelItem` cmdlet remotely.</span></span>

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### <span data-ttu-id="aacf5-130">Exempel 6: Sök efter beskrivningar av objekt på kontroll panelen</span><span class="sxs-lookup"><span data-stu-id="aacf5-130">Example 6: Search the descriptions of control panel items</span></span>

<span data-ttu-id="aacf5-131">I det här exemplet genomsöks egenskapen **Beskrivning** i kontroll panels objekt så att bara de som innehåller namnet **Device** visas.</span><span class="sxs-lookup"><span data-stu-id="aacf5-131">This example searches the **Description** property of the control panel items to get only those that contain the name **Device**.</span></span>

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

<span data-ttu-id="aacf5-132">`Get-ControlPanelItem`Cmdlet: en hämtar alla objekt på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="aacf5-132">The `Get-ControlPanelItem` cmdlet gets all control panel items.</span></span> <span data-ttu-id="aacf5-133">`Where-Object`Cmdleten filtrerar objekten efter värdet för egenskapen **Description** .</span><span class="sxs-lookup"><span data-stu-id="aacf5-133">The `Where-Object` cmdlet filters the items by the value of the **Description** property.</span></span>

## <span data-ttu-id="aacf5-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aacf5-134">PARAMETERS</span></span>

### <span data-ttu-id="aacf5-135">– CanonicalName</span><span class="sxs-lookup"><span data-stu-id="aacf5-135">-CanonicalName</span></span>

<span data-ttu-id="aacf5-136">Anger, som en sträng mat ris, objekt på kontroll panelen efter deras kanoniska namn eller namn mönster som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="aacf5-136">Specifies, as a string array, the control panel items by their canonical names or name patterns that this cmdlet gets.</span></span> <span data-ttu-id="aacf5-137">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="aacf5-137">Wildcards are permitted.</span></span> <span data-ttu-id="aacf5-138">Om du anger flera namn hämtar denna cmdlet kontroll panels objekt som matchar något av namnen, som om objekten i namn listan avgränsades med en "or"-Operator.</span><span class="sxs-lookup"><span data-stu-id="aacf5-138">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span>

<span data-ttu-id="aacf5-139">Som standard hämtar denna cmdlet alla kontroll panels objekt i systemet.</span><span class="sxs-lookup"><span data-stu-id="aacf5-139">By default, this cmdlet gets all control panel items in the system.</span></span>

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

### <span data-ttu-id="aacf5-140">– Kategori</span><span class="sxs-lookup"><span data-stu-id="aacf5-140">-Category</span></span>

<span data-ttu-id="aacf5-141">Anger, som en sträng mat ris, kategorierna i kontroll panelens objekt i de angivna kategorierna som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="aacf5-141">Specifies, as a string array, the categories of the control panel items in the specified categories that this cmdlet gets.</span></span> <span data-ttu-id="aacf5-142">Ange ett kategori namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="aacf5-142">Enter a category name or name pattern.</span></span> <span data-ttu-id="aacf5-143">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="aacf5-143">Wildcards are permitted.</span></span> <span data-ttu-id="aacf5-144">Om du anger flera namn hämtar denna cmdlet kontroll panels objekt som matchar något av namnen, som om objekten i namn listan avgränsades med en "or"-Operator.</span><span class="sxs-lookup"><span data-stu-id="aacf5-144">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span> <span data-ttu-id="aacf5-145">Som standard hämtar denna cmdlet alla kontroll panels objekt i systemet.</span><span class="sxs-lookup"><span data-stu-id="aacf5-145">By default, this cmdlet gets all control panel items in the system.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aacf5-146">-Name</span><span class="sxs-lookup"><span data-stu-id="aacf5-146">-Name</span></span>

<span data-ttu-id="aacf5-147">Anger, som en sträng mat ris, namnen eller namn mönstren på kontroll panelen som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="aacf5-147">Specifies, as a string array, the names or name patterns of the control panel that this cmdlet gets.</span></span>
<span data-ttu-id="aacf5-148">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="aacf5-148">Wildcards are permitted.</span></span> <span data-ttu-id="aacf5-149">Du kan också skicka ett namn eller namn-mönster till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aacf5-149">You can also pipe a name or name pattern to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="aacf5-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aacf5-150">CommonParameters</span></span>

<span data-ttu-id="aacf5-151">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aacf5-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aacf5-152">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aacf5-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aacf5-153">INDATA</span><span class="sxs-lookup"><span data-stu-id="aacf5-153">INPUTS</span></span>

### <span data-ttu-id="aacf5-154">System. String</span><span class="sxs-lookup"><span data-stu-id="aacf5-154">System.String</span></span>

<span data-ttu-id="aacf5-155">Du kan skicka vidare ett namn eller namn-mönster till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aacf5-155">You can pipe a name or name pattern to this cmdlet.</span></span>

## <span data-ttu-id="aacf5-156">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aacf5-156">OUTPUTS</span></span>

### <span data-ttu-id="aacf5-157">Microsoft. PowerShell. commands. ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="aacf5-157">Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="aacf5-158">Denna cmdlet hämtar objekt på kontroll panelen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="aacf5-158">This cmdlet gets control panel items on the local computer.</span></span>

## <span data-ttu-id="aacf5-159">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="aacf5-159">NOTES</span></span>

## <span data-ttu-id="aacf5-160">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="aacf5-160">RELATED LINKS</span></span>

[<span data-ttu-id="aacf5-161">Visa ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="aacf5-161">Show-ControlPanelItem</span></span>](Show-ControlPanelItem.md)
