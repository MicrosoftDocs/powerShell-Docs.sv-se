---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 8425c3e68573fe214ec5de465c8492e0bf99b309
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2020
ms.locfileid: "93269187"
---
# <span data-ttu-id="07eaa-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="07eaa-103">Invoke-DscResource</span></span>

## <span data-ttu-id="07eaa-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="07eaa-104">SYNOPSIS</span></span>
<span data-ttu-id="07eaa-105">Kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07eaa-105">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="07eaa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07eaa-106">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="07eaa-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="07eaa-107">DESCRIPTION</span></span>

<span data-ttu-id="07eaa-108">`Invoke-DscResource`Cmdleten kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07eaa-108">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="07eaa-109">Den här cmdleten anropar en DSC-resurs direkt utan att skapa ett konfigurations dokument.</span><span class="sxs-lookup"><span data-stu-id="07eaa-109">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="07eaa-110">Med den här cmdleten kan konfigurations hanterings produkter hantera Windows eller Linux med hjälp av DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="07eaa-110">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="07eaa-111">Den här cmdleten aktiverar även fel sökning av resurser när DSC-motorn körs med fel sökning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="07eaa-111">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="07eaa-112">`Invoke-DscResource` är en experimentell funktion i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="07eaa-112">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="07eaa-113">Om du vill använda cmdleten måste du aktivera den med hjälp av följande kommando.</span><span class="sxs-lookup"><span data-stu-id="07eaa-113">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="07eaa-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="07eaa-114">EXAMPLES</span></span>

### <span data-ttu-id="07eaa-115">Exempel 1: anropa set-metoden för en resurs genom att ange dess obligatoriska egenskaper</span><span class="sxs-lookup"><span data-stu-id="07eaa-115">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="07eaa-116">Det här exemplet anropar **set** -metoden för en resurs med namnet **WindowsProcess** och ger den obligatoriska **sökvägen** och **argument** egenskaperna för att starta den angivna Windows-processen.</span><span class="sxs-lookup"><span data-stu-id="07eaa-116">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="07eaa-117">Exempel 2: anropa test metoden för en resurs för en angiven modul</span><span class="sxs-lookup"><span data-stu-id="07eaa-117">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="07eaa-118">I det här exemplet anropas **test** metoden för en resurs med namnet **WindowsProcess** , som finns i modulen med namnet **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="07eaa-118">This example invokes the **Test** method of a resource named **WindowsProcess** , which is in the module named **PSDesiredStateConfiguration**.</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="07eaa-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="07eaa-119">PARAMETERS</span></span>

### <span data-ttu-id="07eaa-120">-Metod</span><span class="sxs-lookup"><span data-stu-id="07eaa-120">-Method</span></span>

<span data-ttu-id="07eaa-121">Anger metoden för den resurs som denna cmdlet anropar.</span><span class="sxs-lookup"><span data-stu-id="07eaa-121">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="07eaa-122">De acceptabla värdena för den här parametern är: **Get** , **set** och **test**.</span><span class="sxs-lookup"><span data-stu-id="07eaa-122">The acceptable values for this parameter are: **Get** , **Set** , and **Test**.</span></span>

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

### <span data-ttu-id="07eaa-123">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="07eaa-123">-ModuleName</span></span>

<span data-ttu-id="07eaa-124">Anger namnet på den modul från vilken denna cmdlet anropar den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="07eaa-124">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

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

### <span data-ttu-id="07eaa-125">-Name</span><span class="sxs-lookup"><span data-stu-id="07eaa-125">-Name</span></span>

<span data-ttu-id="07eaa-126">Anger namnet på den DSC-resurs som ska startas.</span><span class="sxs-lookup"><span data-stu-id="07eaa-126">Specifies the name of the DSC resource to start.</span></span>

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

### <span data-ttu-id="07eaa-127">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="07eaa-127">-Property</span></span>

<span data-ttu-id="07eaa-128">Anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel respektive värde.</span><span class="sxs-lookup"><span data-stu-id="07eaa-128">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

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

### <span data-ttu-id="07eaa-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07eaa-129">CommonParameters</span></span>

<span data-ttu-id="07eaa-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07eaa-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07eaa-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="07eaa-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07eaa-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="07eaa-132">INPUTS</span></span>

### <span data-ttu-id="07eaa-133">System. String</span><span class="sxs-lookup"><span data-stu-id="07eaa-133">System.String</span></span>

### <span data-ttu-id="07eaa-134">Microsoft. PowerShell. commands. ModuleSpecification</span><span class="sxs-lookup"><span data-stu-id="07eaa-134">Microsoft.PowerShell.Commands.ModuleSpecification</span></span>

## <span data-ttu-id="07eaa-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="07eaa-135">OUTPUTS</span></span>

### <span data-ttu-id="07eaa-136">System. Object</span><span class="sxs-lookup"><span data-stu-id="07eaa-136">System.Object</span></span>

## <span data-ttu-id="07eaa-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="07eaa-137">NOTES</span></span>

- <span data-ttu-id="07eaa-138">Tidigare kördes Windows PowerShell 5,1-resurser under system kontext, om inget annat anges med användar kontext med nyckeln **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="07eaa-138">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential**.</span></span> <span data-ttu-id="07eaa-139">I PowerShell 7,0, körs resurser i användarens kontext och **PsDscRunAsCredential** stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="07eaa-139">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="07eaa-140">Tidigare konfigurationer som använder den här nyckeln kommer att utlösa ett undantag.</span><span class="sxs-lookup"><span data-stu-id="07eaa-140">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="07eaa-141">Från och med PowerShell 7 `Invoke-DscResource` har inte längre stöd för att anropa WMI DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="07eaa-141">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="07eaa-142">Detta inkluderar **fil** -och **logg** resurser i **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="07eaa-142">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

## <span data-ttu-id="07eaa-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="07eaa-143">RELATED LINKS</span></span>

[<span data-ttu-id="07eaa-144">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="07eaa-144">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="07eaa-145">Get-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="07eaa-145">Get-DscResource</span></span>](Get-DscResource.md)
