---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: 0e531b3cc072b7cc1efe0ef06fb741326bf3a72b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708916"
---
# <span data-ttu-id="121da-102">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="121da-102">Get-CimSession</span></span>

## <span data-ttu-id="121da-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="121da-103">SYNOPSIS</span></span>
<span data-ttu-id="121da-104">Hämtar CIM-sessionsobjekt från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="121da-104">Gets the CIM session objects from the current session.</span></span>

## <span data-ttu-id="121da-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="121da-105">SYNTAX</span></span>

### <span data-ttu-id="121da-106">ComputerNameSet (standard)</span><span class="sxs-lookup"><span data-stu-id="121da-106">ComputerNameSet (Default)</span></span>

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="121da-107">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="121da-107">SessionIdSet</span></span>

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### <span data-ttu-id="121da-108">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="121da-108">InstanceIdSet</span></span>

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="121da-109">NameSet</span><span class="sxs-lookup"><span data-stu-id="121da-109">NameSet</span></span>

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## <span data-ttu-id="121da-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="121da-110">DESCRIPTION</span></span>

<span data-ttu-id="121da-111">Som standard hämtar cmdleten alla CIM-sessioner som skapats i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="121da-111">By default, the cmdlet gets all of the CIM sessions created in the current PowerShell session.</span></span> <span data-ttu-id="121da-112">Du kan använda parametrarna för `Get-CimSession` för att hämta de sessioner som är specifika för vissa datorer, eller så kan du identifiera sessioner efter namn eller andra identifierare.</span><span class="sxs-lookup"><span data-stu-id="121da-112">You can use the parameters of `Get-CimSession` to get the sessions that are for particular computers, or you can identify sessions by their names or other identifiers.</span></span> <span data-ttu-id="121da-113">`Get-CimSession` hämtar inte CIM-sessioner som skapats i andra PowerShell-sessioner eller som skapades på andra datorer.</span><span class="sxs-lookup"><span data-stu-id="121da-113">`Get-CimSession` does not get CIM sessions that were created in other PowerShell sessions or that were created on other computers.</span></span>

<span data-ttu-id="121da-114">Mer information om CIM-sessioner finns [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="121da-114">For more information about CIM sessions, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

## <span data-ttu-id="121da-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="121da-115">EXAMPLES</span></span>

### <span data-ttu-id="121da-116">Exempel 1: Hämta CIM-sessioner från den aktuella PowerShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="121da-116">Example 1: Get CIM sessions from the current PowerShell session</span></span>

<span data-ttu-id="121da-117">I det här exemplet skapas CIM [-sessioner med New-CimSession](New-CimSession.md)och sedan hämtas CIM-sessioner med hjälp av `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="121da-117">This example creates CIM sessions using [New-CimSession](New-CimSession.md), and then gets the CIM sessions using `Get-CimSession`.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="121da-118">Exempel 2: Hämta CIM-sessionerna till en angiven dator</span><span class="sxs-lookup"><span data-stu-id="121da-118">Example 2: Get the CIM sessions to a specific computer</span></span>

<span data-ttu-id="121da-119">Det här exemplet hämtar de CIM-sessioner som är anslutna till datorn med namnet **Server02**.</span><span class="sxs-lookup"><span data-stu-id="121da-119">This example gets the CIM sessions that are connected to the computer named **Server02**.</span></span>

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="121da-120">Exempel 3: Hämta en lista över CIM-sessioner och formatera sedan listan</span><span class="sxs-lookup"><span data-stu-id="121da-120">Example 3: Get a list of CIM sessions and then format the list</span></span>

<span data-ttu-id="121da-121">Det här exemplet hämtar alla CIM-sessioner i den aktuella PowerShell-sessionen och visar en tabell som endast innehåller egenskaperna **computername** och **InstanceID** .</span><span class="sxs-lookup"><span data-stu-id="121da-121">This example gets all CIM sessions in the current PowerShell session and displays a table containing only the **ComputerName** and **InstanceID** properties.</span></span>

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### <span data-ttu-id="121da-122">Exempel 4: Hämta alla CIM-sessioner som har vissa namn</span><span class="sxs-lookup"><span data-stu-id="121da-122">Example 4: Get all the CIM sessions that have specific names</span></span>

<span data-ttu-id="121da-123">Det här exemplet hämtar alla CIM-sessioner som har namn som börjar med **Serv**.</span><span class="sxs-lookup"><span data-stu-id="121da-123">This example gets all CIM sessions that have names that begin with **serv**.</span></span>

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="121da-124">Exempel 5: Hämta en angiven CIM-session</span><span class="sxs-lookup"><span data-stu-id="121da-124">Example 5: Get a specific CIM session</span></span>

<span data-ttu-id="121da-125">Det här exemplet hämtar CIM-sessionen med **ID** 2.</span><span class="sxs-lookup"><span data-stu-id="121da-125">This example gets the CIM session that has an **Id** of 2.</span></span>

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## <span data-ttu-id="121da-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="121da-126">PARAMETERS</span></span>

### <span data-ttu-id="121da-127">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="121da-127">-ComputerName</span></span>

<span data-ttu-id="121da-128">Anger namnet på den dator där CIM-sessioner som är anslutna till ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="121da-128">Specifies the name of the computer to get CIM sessions connected to.</span></span> <span data-ttu-id="121da-129">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="121da-129">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="121da-130">-ID</span><span class="sxs-lookup"><span data-stu-id="121da-130">-Id</span></span>

<span data-ttu-id="121da-131">Anger identifieraren för den CIM-session som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="121da-131">Specifies the identifier of the CIM session to get.</span></span> <span data-ttu-id="121da-132">Använd kommatecken för att avgränsa ID: n eller Använd intervall operatorn () för `..` att ange ett intervall med ID: n för flera ID: n.</span><span class="sxs-lookup"><span data-stu-id="121da-132">For multiple IDs, use commas to separate the IDs or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="121da-133">Ett **ID** är ett heltal som unikt identifierar CIM-sessionen inom den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="121da-133">An **Id** is an integer that uniquely identifies the CIM session within the current PowerShell session.</span></span>

<span data-ttu-id="121da-134">Mer information om operatorn Range finns [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="121da-134">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="121da-135">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="121da-135">-InstanceId</span></span>

<span data-ttu-id="121da-136">Anger instans-ID för CIM-sessionen som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="121da-136">Specifies the instance IDs of the CIM session to get.</span></span>

<span data-ttu-id="121da-137">**InstanceID** är en globalt unik IDENTIFIERARE (GUID) som unikt identifierar en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="121da-137">**InstanceId** is a globally-unique identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="121da-138">**InstanceID** är unikt, även om du har flera sessioner som körs i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="121da-138">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="121da-139">**InstanceID** lagras i egenskapen **InstanceID** för objektet som representerar en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="121da-139">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="121da-140">-Name</span><span class="sxs-lookup"><span data-stu-id="121da-140">-Name</span></span>

<span data-ttu-id="121da-141">Hämtar en eller flera CIM-sessioner som innehåller angivna egna namn.</span><span class="sxs-lookup"><span data-stu-id="121da-141">Gets one or more CIM sessions which contain the specified friendly names.</span></span> <span data-ttu-id="121da-142">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="121da-142">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="121da-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="121da-143">CommonParameters</span></span>
<span data-ttu-id="121da-144">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="121da-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="121da-145">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="121da-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="121da-146">INDATA</span><span class="sxs-lookup"><span data-stu-id="121da-146">INPUTS</span></span>

### <span data-ttu-id="121da-147">Inga</span><span class="sxs-lookup"><span data-stu-id="121da-147">None</span></span>

## <span data-ttu-id="121da-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="121da-148">OUTPUTS</span></span>

### <span data-ttu-id="121da-149">Microsoft. Management. Infrastructure. CimSession</span><span class="sxs-lookup"><span data-stu-id="121da-149">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="121da-150">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="121da-150">NOTES</span></span>

## <span data-ttu-id="121da-151">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="121da-151">RELATED LINKS</span></span>

[<span data-ttu-id="121da-152">Format-Table</span><span class="sxs-lookup"><span data-stu-id="121da-152">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="121da-153">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="121da-153">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="121da-154">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="121da-154">Remove-CimSession</span></span>](remove-cimsession.md)

[<span data-ttu-id="121da-155">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="121da-155">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

