---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266043"
---
# <span data-ttu-id="cb431-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="cb431-103">Invoke-DscResource</span></span>

## <span data-ttu-id="cb431-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cb431-104">SYNOPSIS</span></span>
<span data-ttu-id="cb431-105">Kör en metod för en angiven DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="cb431-105">Runs a method of a specified DSC resource.</span></span>

## <span data-ttu-id="cb431-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cb431-106">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## <span data-ttu-id="cb431-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cb431-107">DESCRIPTION</span></span>
<span data-ttu-id="cb431-108">Cmdleten **Invoke-dscresource Keyword Supports** kör en metod för en angiven DSC-resurs (Desired State Configuration) för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb431-108">The **Invoke-DscResource** cmdlet runs a method of a specified Windows PowerShell Desired State Configuration (DSC) resource.</span></span>
<span data-ttu-id="cb431-109">Innan du kör den här cmdleten ställer du in uppdaterings läget för den lokala Configuration Manager (LCM) på inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="cb431-109">Before you run this cmdlet, set the refresh mode of the Local Configuration Manager (LCM) to Disabled.</span></span>

<span data-ttu-id="cb431-110">Den här cmdleten anropar en DSC-resurs direkt utan att skapa ett konfigurations dokument.</span><span class="sxs-lookup"><span data-stu-id="cb431-110">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span>
<span data-ttu-id="cb431-111">Med den här cmdleten kan konfigurations hanterings produkter hantera Windows med hjälp av DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="cb431-111">Using this cmdlet, configuration management products can manage windows by using DSC resources.</span></span>
<span data-ttu-id="cb431-112">Den här cmdleten aktiverar även fel sökning av resurser när DSC-motorn eller LCM körs med fel sökning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="cb431-112">This cmdlet also enables debugging of resources when the DSC engine or LCM is running with debugging enabled.</span></span>

## <span data-ttu-id="cb431-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cb431-113">EXAMPLES</span></span>

### <span data-ttu-id="cb431-114">Exempel 1: anropa set-metoden för en resurs genom att ange dess obligatoriska egenskaper</span><span class="sxs-lookup"><span data-stu-id="cb431-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="cb431-115">Det här kommandot anropar **set** -metoden för en resurs med namnet log och anger en **meddelande** egenskap för den.</span><span class="sxs-lookup"><span data-stu-id="cb431-115">This command invokes the **Set** method of a resource named Log and specifies a **Message** property for it.</span></span>

### <span data-ttu-id="cb431-116">Exempel 2: anropa test metoden för en resurs för en angiven modul</span><span class="sxs-lookup"><span data-stu-id="cb431-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="cb431-117">Det här kommandot anropar **test** metoden för en resurs med namnet WindowsProcess, som finns i modulen med namnet PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="cb431-117">This command invokes the **Test** method of a resource named WindowsProcess, which is in the module named PSDesiredStateConfiguration.</span></span>

## <span data-ttu-id="cb431-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cb431-118">PARAMETERS</span></span>

### <span data-ttu-id="cb431-119">-Metod</span><span class="sxs-lookup"><span data-stu-id="cb431-119">-Method</span></span>
<span data-ttu-id="cb431-120">Anger metoden för den resurs som denna cmdlet anropar.</span><span class="sxs-lookup"><span data-stu-id="cb431-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="cb431-121">De acceptabla värdena för den här parametern är: get, set och test.</span><span class="sxs-lookup"><span data-stu-id="cb431-121">The acceptable values for this parameter are: Get, Set, and Test.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cb431-122">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="cb431-122">-ModuleName</span></span>
<span data-ttu-id="cb431-123">Anger namnet på den modul från vilken denna cmdlet anropar den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="cb431-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cb431-124">-Name</span><span class="sxs-lookup"><span data-stu-id="cb431-124">-Name</span></span>
<span data-ttu-id="cb431-125">Anger namnet på den DSC-resurs som ska startas.</span><span class="sxs-lookup"><span data-stu-id="cb431-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cb431-126">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="cb431-126">-Property</span></span>
<span data-ttu-id="cb431-127">Anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel respektive värde.</span><span class="sxs-lookup"><span data-stu-id="cb431-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="cb431-128">Använd cmdleten **Get-dscresource Keyword Supports** för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="cb431-128">Use the **Get-DscResource** cmdlet to discover resource properties and their types.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cb431-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cb431-129">CommonParameters</span></span>
<span data-ttu-id="cb431-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cb431-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cb431-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cb431-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cb431-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="cb431-132">INPUTS</span></span>

## <span data-ttu-id="cb431-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cb431-133">OUTPUTS</span></span>

### <span data-ttu-id="cb431-134">Microsoft. Management. Infrastructure. CimInstance, system. Boolean</span><span class="sxs-lookup"><span data-stu-id="cb431-134">Microsoft.Management.Infrastructure.CimInstance, System.Boolean</span></span>

## <span data-ttu-id="cb431-135">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cb431-135">NOTES</span></span>

## <span data-ttu-id="cb431-136">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cb431-136">RELATED LINKS</span></span>

[<span data-ttu-id="cb431-137">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb431-137">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="cb431-138">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb431-138">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="cb431-139">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="cb431-139">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="cb431-140">Get-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="cb431-140">Get-DscResource</span></span>](Get-DscResource.md)

[<span data-ttu-id="cb431-141">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb431-141">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="cb431-142">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cb431-142">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)

[<span data-ttu-id="cb431-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb431-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="cb431-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb431-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
