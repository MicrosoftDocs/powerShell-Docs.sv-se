---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 551ac39084ff7bf1729618d09cfa521cb6858242
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266655"
---
# <span data-ttu-id="a9a63-103">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="a9a63-103">Get-CimClass</span></span>

## <span data-ttu-id="a9a63-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a9a63-104">SYNOPSIS</span></span>
<span data-ttu-id="a9a63-105">Hämtar en lista över CIM-klasser i en angiven namnrymd.</span><span class="sxs-lookup"><span data-stu-id="a9a63-105">Gets a list of CIM classes in a specific namespace.</span></span>

## <span data-ttu-id="a9a63-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9a63-106">SYNTAX</span></span>

### <span data-ttu-id="a9a63-107">ComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="a9a63-107">ComputerSet (Default)</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### <span data-ttu-id="a9a63-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="a9a63-108">SessionSet</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## <span data-ttu-id="a9a63-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a9a63-109">DESCRIPTION</span></span>

<span data-ttu-id="a9a63-110">`Get-CimClass`Cmdlet: en hämtar en lista över CIM-klasser i en angiven namnrymd.</span><span class="sxs-lookup"><span data-stu-id="a9a63-110">The `Get-CimClass` cmdlet retrieves a list of CIM classes in a specific namespace.</span></span> <span data-ttu-id="a9a63-111">Om inget klass namn har angetts returnerar cmdleten alla klasser i namn området.</span><span class="sxs-lookup"><span data-stu-id="a9a63-111">If there is no class name supplied, then the cmdlet returns all the classes in the namespace.</span></span> <span data-ttu-id="a9a63-112">Till skillnad från en CIM-instans innehåller CIM-klasser inte CIM-sessionen eller dator namnet som de hämtas från.</span><span class="sxs-lookup"><span data-stu-id="a9a63-112">Unlike a CIM instance, CIM classes do not contain the CIM session or computer name from which they are retrieved.</span></span>

## <span data-ttu-id="a9a63-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a9a63-113">EXAMPLES</span></span>

### <span data-ttu-id="a9a63-114">Exempel 1: Hämta alla klass definitioner</span><span class="sxs-lookup"><span data-stu-id="a9a63-114">Example 1: Get all the class definitions</span></span>

<span data-ttu-id="a9a63-115">Det här exemplet hämtar alla klass definitioner under namn områdets **rot-/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="a9a63-115">This example gets all the class definitions under the namespace **root/cimv2**.</span></span>

```powershell
Get-CimClass
```

### <span data-ttu-id="a9a63-116">Exempel 2: Hämta klasserna med ett angivet namn</span><span class="sxs-lookup"><span data-stu-id="a9a63-116">Example 2: Get the classes with a specific name</span></span>

<span data-ttu-id="a9a63-117">Det här exemplet hämtar de klasser som innehåller ordet **disk** i sina namn.</span><span class="sxs-lookup"><span data-stu-id="a9a63-117">This example gets the classes that contain the word **disk** in their names.</span></span>

```powershell
Get-CimClass -ClassName *disk*
```

### <span data-ttu-id="a9a63-118">Exempel 3: Hämta klasserna med ett angivet metod namn</span><span class="sxs-lookup"><span data-stu-id="a9a63-118">Example 3: Get the classes with a specific method name</span></span>

<span data-ttu-id="a9a63-119">Det här exemplet hämtar de klasser som börjar med namnet **Win32** och har ett metod namn som börjar med **term**.</span><span class="sxs-lookup"><span data-stu-id="a9a63-119">This example gets the classes that start with the name **Win32** and have a method name that starts with **Term**.</span></span>

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### <span data-ttu-id="a9a63-120">Exempel 4: Hämta klasserna med ett angivet egenskaps namn</span><span class="sxs-lookup"><span data-stu-id="a9a63-120">Example 4: Get the classes with a specific property name</span></span>

<span data-ttu-id="a9a63-121">Det här exemplet hämtar de klasser som börjar med namnet **Win32** och har en egenskap med namnet **handle**.</span><span class="sxs-lookup"><span data-stu-id="a9a63-121">This example gets the classes that start with the name **Win32** and have a property named **Handle**.</span></span>

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### <span data-ttu-id="a9a63-122">Exempel 5: Hämta klasserna med ett angivet kvalificerande namn</span><span class="sxs-lookup"><span data-stu-id="a9a63-122">Example 5: Get the classes with a specific qualifier name</span></span>

<span data-ttu-id="a9a63-123">Det här exemplet hämtar de klasser som börjar med namnet **Win32** , innehåller ordet **disk** i sina namn och har den angivna kvalificerande **associationen**.</span><span class="sxs-lookup"><span data-stu-id="a9a63-123">This example gets the classes that start with the name **Win32** , contain the word **Disk** in their names and have the specified qualifier **Association**.</span></span>

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### <span data-ttu-id="a9a63-124">Exempel 6: Hämta klass definitionerna från ett angivet namn område</span><span class="sxs-lookup"><span data-stu-id="a9a63-124">Example 6: Get the class definitions from a specific namespace</span></span>

<span data-ttu-id="a9a63-125">Det här exemplet hämtar klass definitionerna som innehåller ordet **net** i sina namn från den angivna **rot-/standardCimv2** för namn området.</span><span class="sxs-lookup"><span data-stu-id="a9a63-125">This example gets the class definitions that contain the word **Net** in their names from the specified namespace **root/standardCimv2**.</span></span>

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### <span data-ttu-id="a9a63-126">Exempel 7: Hämta klass definitionerna från en fjärrserver</span><span class="sxs-lookup"><span data-stu-id="a9a63-126">Example 7: Get the class definitions from a remote server</span></span>

<span data-ttu-id="a9a63-127">I det här exemplet hämtas klass definitionerna som innehåller ordet **disk** i namnen från de angivna fjärrservrarna **Server01** och **Server02**.</span><span class="sxs-lookup"><span data-stu-id="a9a63-127">This example gets the class definitions that contain the word **disk** in their names from the specified remote servers **Server01** and **Server02**.</span></span>

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### <span data-ttu-id="a9a63-128">Exempel 8: Hämta klasserna med en CIM-session</span><span class="sxs-lookup"><span data-stu-id="a9a63-128">Example 8: Get the classes by using a CIM session</span></span>

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

<span data-ttu-id="a9a63-129">Den här uppsättningen kommandon skapar en session med flera datorer och lagrar den i en variabel `$s` med hjälp av `New-CimSession` cmdleten och hämtar sedan klasserna med hjälp av `Get-CimClass` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a9a63-129">This set of commands creates a session with multiple computers and stores it into a variable `$s` using the `New-CimSession` cmdlet, and then gets the classes using the `Get-CimClass` cmdlet.</span></span>

## <span data-ttu-id="a9a63-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a9a63-130">PARAMETERS</span></span>

### <span data-ttu-id="a9a63-131">– CimSession</span><span class="sxs-lookup"><span data-stu-id="a9a63-131">-CimSession</span></span>

<span data-ttu-id="a9a63-132">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a9a63-132">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="a9a63-133">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata för en- `New-CimSession` eller- `Get-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a9a63-133">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span> <span data-ttu-id="a9a63-134">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a9a63-134">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a9a63-135">-ClassName</span><span class="sxs-lookup"><span data-stu-id="a9a63-135">-ClassName</span></span>

<span data-ttu-id="a9a63-136">Anger namnet på CIM-klassen som åtgärden ska utföras för.</span><span class="sxs-lookup"><span data-stu-id="a9a63-136">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="a9a63-137">Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.</span><span class="sxs-lookup"><span data-stu-id="a9a63-137">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a9a63-138">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a9a63-138">-ComputerName</span></span>

<span data-ttu-id="a9a63-139">Anger den dator som du vill köra CIM-åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="a9a63-139">Specifies the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="a9a63-140">Du kan ange ett fullständigt kvalificerat domän namn (FQDN) ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="a9a63-140">You can specify a fully qualified domain name (FQDN) a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="a9a63-141">Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="a9a63-141">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="a9a63-142">Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="a9a63-142">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="a9a63-143">Om flera åtgärder utförs på samma dator ger det bättre prestanda om du använder en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="a9a63-143">If multiple operations are being performed on the same computer, using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9a63-144">– MethodName</span><span class="sxs-lookup"><span data-stu-id="a9a63-144">-MethodName</span></span>

<span data-ttu-id="a9a63-145">Söker efter klasser som har en metod som matchar det här namnet.</span><span class="sxs-lookup"><span data-stu-id="a9a63-145">Finds the classes that have a method matching this name.</span></span> <span data-ttu-id="a9a63-146">Du kan använda jokertecken med den här parametern.</span><span class="sxs-lookup"><span data-stu-id="a9a63-146">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a9a63-147">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="a9a63-147">-Namespace</span></span>

<span data-ttu-id="a9a63-148">Anger namn området för CIM-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a9a63-148">Specifies the namespace for CIM operation.</span></span> <span data-ttu-id="a9a63-149">Standard namn området är **rot-/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="a9a63-149">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="a9a63-150">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="a9a63-150">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9a63-151">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="a9a63-151">-OperationTimeoutSec</span></span>

<span data-ttu-id="a9a63-152">Anger hur lång tid cmdleten väntar på ett svar från datorn.</span><span class="sxs-lookup"><span data-stu-id="a9a63-152">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="a9a63-153">Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="a9a63-153">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="a9a63-154">Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.</span><span class="sxs-lookup"><span data-stu-id="a9a63-154">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9a63-155">-PropertyName</span><span class="sxs-lookup"><span data-stu-id="a9a63-155">-PropertyName</span></span>

<span data-ttu-id="a9a63-156">Söker efter klasser som har en egenskap som matchar det här namnet.</span><span class="sxs-lookup"><span data-stu-id="a9a63-156">Finds the classes which have a property matching this name.</span></span> <span data-ttu-id="a9a63-157">Du kan använda jokertecken med den här parametern.</span><span class="sxs-lookup"><span data-stu-id="a9a63-157">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9a63-158">-QualifierName</span><span class="sxs-lookup"><span data-stu-id="a9a63-158">-QualifierName</span></span>

<span data-ttu-id="a9a63-159">Filtrerar klasserna efter kvalificerande namn på klass nivå.</span><span class="sxs-lookup"><span data-stu-id="a9a63-159">Filters the classes by class level qualifier name.</span></span> <span data-ttu-id="a9a63-160">Du kan använda jokertecken med den här parametern.</span><span class="sxs-lookup"><span data-stu-id="a9a63-160">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a9a63-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9a63-161">CommonParameters</span></span>

<span data-ttu-id="a9a63-162">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a9a63-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9a63-163">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a9a63-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9a63-164">INDATA</span><span class="sxs-lookup"><span data-stu-id="a9a63-164">INPUTS</span></span>

### <span data-ttu-id="a9a63-165">Inget</span><span class="sxs-lookup"><span data-stu-id="a9a63-165">None</span></span>

<span data-ttu-id="a9a63-166">Denna cmdlet accepterar inga inobjekt.</span><span class="sxs-lookup"><span data-stu-id="a9a63-166">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="a9a63-167">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a9a63-167">OUTPUTS</span></span>

### <span data-ttu-id="a9a63-168">Microsoft. Management. Infrastructure. CimClass</span><span class="sxs-lookup"><span data-stu-id="a9a63-168">Microsoft.Management.Infrastructure.CimClass</span></span>

<span data-ttu-id="a9a63-169">Den här cmdleten returnerar ett CIM Class-objekt.</span><span class="sxs-lookup"><span data-stu-id="a9a63-169">This cmdlet returns a CIM class object.</span></span>

## <span data-ttu-id="a9a63-170">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a9a63-170">NOTES</span></span>

## <span data-ttu-id="a9a63-171">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a9a63-171">RELATED LINKS</span></span>

[<span data-ttu-id="a9a63-172">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="a9a63-172">New-CimSession</span></span>](New-CimSession.md)
