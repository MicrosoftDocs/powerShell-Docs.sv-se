---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 732db5a049a68e059db6062d2f6c3f850d579adc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709349"
---
# <span data-ttu-id="de46d-102">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="de46d-102">Invoke-DscResource</span></span>

## <span data-ttu-id="de46d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="de46d-103">SYNOPSIS</span></span>
<span data-ttu-id="de46d-104">Kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de46d-104">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="de46d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="de46d-105">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="de46d-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="de46d-106">DESCRIPTION</span></span>

<span data-ttu-id="de46d-107">`Invoke-DscResource`Cmdleten kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de46d-107">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="de46d-108">Den här cmdleten anropar en DSC-resurs direkt utan att skapa ett konfigurations dokument.</span><span class="sxs-lookup"><span data-stu-id="de46d-108">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="de46d-109">Med den här cmdleten kan konfigurations hanterings produkter hantera Windows eller Linux med hjälp av DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="de46d-109">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="de46d-110">Den här cmdleten aktiverar även fel sökning av resurser när DSC-motorn körs med fel sökning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="de46d-110">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="de46d-111">`Invoke-DscResource` är en experimentell funktion i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="de46d-111">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="de46d-112">Om du vill använda cmdleten måste du aktivera den med hjälp av följande kommando.</span><span class="sxs-lookup"><span data-stu-id="de46d-112">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="de46d-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="de46d-113">EXAMPLES</span></span>

### <span data-ttu-id="de46d-114">Exempel 1: anropa set-metoden för en resurs genom att ange dess obligatoriska egenskaper</span><span class="sxs-lookup"><span data-stu-id="de46d-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="de46d-115">Det här exemplet anropar **set** -metoden för en resurs med namnet **WindowsProcess** och ger den obligatoriska **sökvägen** och **argument** egenskaperna för att starta den angivna Windows-processen.</span><span class="sxs-lookup"><span data-stu-id="de46d-115">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="de46d-116">Exempel 2: anropa test metoden för en resurs för en angiven modul</span><span class="sxs-lookup"><span data-stu-id="de46d-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="de46d-117">I det här exemplet anropas **test** metoden för en resurs med namnet **WindowsProcess**, som finns i modulen med namnet **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="de46d-117">This example invokes the **Test** method of a resource named **WindowsProcess**, which is in the module named **PSDesiredStateConfiguration**.</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="de46d-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="de46d-118">PARAMETERS</span></span>

### <span data-ttu-id="de46d-119">-Metod</span><span class="sxs-lookup"><span data-stu-id="de46d-119">-Method</span></span>

<span data-ttu-id="de46d-120">Anger metoden för den resurs som denna cmdlet anropar.</span><span class="sxs-lookup"><span data-stu-id="de46d-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="de46d-121">De acceptabla värdena för den här parametern är: **Get**, **set** och **test**.</span><span class="sxs-lookup"><span data-stu-id="de46d-121">The acceptable values for this parameter are: **Get**, **Set**, and **Test**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de46d-122">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="de46d-122">-ModuleName</span></span>

<span data-ttu-id="de46d-123">Anger namnet på den modul från vilken denna cmdlet anropar den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="de46d-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="de46d-124">-Name</span><span class="sxs-lookup"><span data-stu-id="de46d-124">-Name</span></span>

<span data-ttu-id="de46d-125">Anger namnet på den DSC-resurs som ska startas.</span><span class="sxs-lookup"><span data-stu-id="de46d-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="de46d-126">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="de46d-126">-Property</span></span>

<span data-ttu-id="de46d-127">Anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel respektive värde.</span><span class="sxs-lookup"><span data-stu-id="de46d-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de46d-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="de46d-128">CommonParameters</span></span>

<span data-ttu-id="de46d-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="de46d-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="de46d-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="de46d-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="de46d-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="de46d-131">INPUTS</span></span>

### <span data-ttu-id="de46d-132">System. String</span><span class="sxs-lookup"><span data-stu-id="de46d-132">System.String</span></span>

### <span data-ttu-id="de46d-133">Microsoft. PowerShell. commands. ModuleSpecification</span><span class="sxs-lookup"><span data-stu-id="de46d-133">Microsoft.PowerShell.Commands.ModuleSpecification</span></span>

## <span data-ttu-id="de46d-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="de46d-134">OUTPUTS</span></span>

### <span data-ttu-id="de46d-135">System. Object</span><span class="sxs-lookup"><span data-stu-id="de46d-135">System.Object</span></span>

## <span data-ttu-id="de46d-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="de46d-136">NOTES</span></span>

- <span data-ttu-id="de46d-137">Tidigare kördes Windows PowerShell 5,1-resurser under system kontext, om inget annat anges med användar kontext med nyckeln **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="de46d-137">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential**.</span></span> <span data-ttu-id="de46d-138">I PowerShell 7,0, körs resurser i användarens kontext och **PsDscRunAsCredential** stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="de46d-138">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="de46d-139">Tidigare konfigurationer som använder den här nyckeln kommer att utlösa ett undantag.</span><span class="sxs-lookup"><span data-stu-id="de46d-139">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="de46d-140">Från och med PowerShell 7 `Invoke-DscResource` har inte längre stöd för att anropa WMI DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="de46d-140">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="de46d-141">Detta inkluderar **fil** -och **logg** resurser i **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="de46d-141">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

## <span data-ttu-id="de46d-142">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="de46d-142">RELATED LINKS</span></span>

[<span data-ttu-id="de46d-143">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="de46d-143">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="de46d-144">Get-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="de46d-144">Get-DscResource</span></span>](Get-DscResource.md)
