---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 4703586008d9044ae68fd7375db65f0d0a9b9980
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2020
ms.locfileid: "93269181"
---
# <span data-ttu-id="9ecbb-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="9ecbb-103">Invoke-DscResource</span></span>

## <span data-ttu-id="9ecbb-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9ecbb-104">SYNOPSIS</span></span>
<span data-ttu-id="9ecbb-105">Kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-105">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="9ecbb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9ecbb-106">SYNTAX</span></span>

```
Invoke-DscResource [[-Method] <Object>] [[-Name] <Object>] [[-Property] <Object>]
 [[-ModuleName] <Object>] [-AsJob] [<CommonParameters>]
```

## <span data-ttu-id="9ecbb-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9ecbb-107">DESCRIPTION</span></span>

<span data-ttu-id="9ecbb-108">`Invoke-DscResource`Cmdleten kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-108">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="9ecbb-109">Den här cmdleten anropar en DSC-resurs direkt utan att skapa ett konfigurations dokument.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-109">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="9ecbb-110">Med den här cmdleten kan konfigurations hanterings produkter hantera Windows eller Linux med hjälp av DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-110">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="9ecbb-111">Den här cmdleten aktiverar även fel sökning av resurser när DSC-motorn körs med fel sökning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-111">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="9ecbb-112">`Invoke-DscResource` är en experimentell funktion i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-112">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="9ecbb-113">Om du vill använda cmdleten måste du aktivera den med hjälp av följande kommando.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-113">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="9ecbb-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9ecbb-114">EXAMPLES</span></span>

### <span data-ttu-id="9ecbb-115">Exempel 1: anropa set-metoden för en resurs genom att ange dess obligatoriska egenskaper</span><span class="sxs-lookup"><span data-stu-id="9ecbb-115">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="9ecbb-116">Det här exemplet anropar **set** -metoden för en resurs med namnet **WindowsProcess** och ger den obligatoriska **sökvägen** och **argument** egenskaperna för att starta den angivna Windows-processen.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-116">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="9ecbb-117">Exempel 2: anropa test metoden för en resurs för en angiven modul</span><span class="sxs-lookup"><span data-stu-id="9ecbb-117">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="9ecbb-118">I det här exemplet anropas **test** metoden för en resurs med namnet **WindowsProcess** , som finns i modulen med namnet **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-118">This example invokes the **Test** method of a resource named **WindowsProcess** , which is in the module named **PSDesiredStateConfiguration**.</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="9ecbb-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9ecbb-119">PARAMETERS</span></span>

### <span data-ttu-id="9ecbb-120">-Metod</span><span class="sxs-lookup"><span data-stu-id="9ecbb-120">-Method</span></span>

<span data-ttu-id="9ecbb-121">Anger metoden för den resurs som denna cmdlet anropar.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-121">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="9ecbb-122">De acceptabla värdena för den här parametern är: **Get** , **set** och **test**.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-122">The acceptable values for this parameter are: **Get** , **Set** , and **Test**.</span></span>

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ecbb-123">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="9ecbb-123">-ModuleName</span></span>

<span data-ttu-id="9ecbb-124">Anger namnet på den modul från vilken denna cmdlet anropar den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-124">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ecbb-125">-Name</span><span class="sxs-lookup"><span data-stu-id="9ecbb-125">-Name</span></span>

<span data-ttu-id="9ecbb-126">Anger namnet på den DSC-resurs som ska startas.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-126">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ecbb-127">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="9ecbb-127">-Property</span></span>

<span data-ttu-id="9ecbb-128">Anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel respektive värde.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-128">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ecbb-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ecbb-129">CommonParameters</span></span>

<span data-ttu-id="9ecbb-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ecbb-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9ecbb-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ecbb-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="9ecbb-132">INPUTS</span></span>

## <span data-ttu-id="9ecbb-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9ecbb-133">OUTPUTS</span></span>

### <span data-ttu-id="9ecbb-134">Microsoft. Management. Infrastructure. CimInstance, system. Boolean</span><span class="sxs-lookup"><span data-stu-id="9ecbb-134">Microsoft.Management.Infrastructure.CimInstance, System.Boolean</span></span>

## <span data-ttu-id="9ecbb-135">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9ecbb-135">NOTES</span></span>

- <span data-ttu-id="9ecbb-136">Tidigare kördes Windows PowerShell 5,1-resurser under system kontext, om inget annat anges med användar kontext med nyckeln **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-136">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential**.</span></span> <span data-ttu-id="9ecbb-137">I PowerShell 7,0, körs resurser i användarens kontext och **PsDscRunAsCredential** stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-137">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="9ecbb-138">Tidigare konfigurationer som använder den här nyckeln kommer att utlösa ett undantag.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-138">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="9ecbb-139">Från och med PowerShell 7 `Invoke-DscResource` har inte längre stöd för att anropa WMI DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-139">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="9ecbb-140">Detta inkluderar **fil** -och **logg** resurser i **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="9ecbb-140">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

## <span data-ttu-id="9ecbb-141">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9ecbb-141">RELATED LINKS</span></span>

[<span data-ttu-id="9ecbb-142">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ecbb-142">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="9ecbb-143">Get-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="9ecbb-143">Get-DscResource</span></span>](Get-DscResource.md)
