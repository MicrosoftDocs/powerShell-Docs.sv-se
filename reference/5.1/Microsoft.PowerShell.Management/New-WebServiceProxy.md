---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265515"
---
# <span data-ttu-id="9b527-103">New-WebServiceProxy</span><span class="sxs-lookup"><span data-stu-id="9b527-103">New-WebServiceProxy</span></span>

## <span data-ttu-id="9b527-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9b527-104">SYNOPSIS</span></span>
<span data-ttu-id="9b527-105">Skapar ett proxy-objekt för webb tjänsten som gör att du kan använda och hantera webb tjänsten i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b527-105">Creates a Web service proxy object that lets you use and manage the Web service in PowerShell.</span></span>

## <span data-ttu-id="9b527-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9b527-106">SYNTAX</span></span>

### <span data-ttu-id="9b527-107">Nocredentials (standard)</span><span class="sxs-lookup"><span data-stu-id="9b527-107">NoCredentials (Default)</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### <span data-ttu-id="9b527-108">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="9b527-108">Credential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="9b527-109">UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="9b527-109">UseDefaultCredential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## <span data-ttu-id="9b527-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9b527-110">DESCRIPTION</span></span>

<span data-ttu-id="9b527-111">Med `New-WebServiceProxy` cmdleten kan du använda en webb tjänst i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b527-111">The `New-WebServiceProxy` cmdlet lets you use a Web service in PowerShell.</span></span> <span data-ttu-id="9b527-112">Cmdleten ansluter till en webb tjänst och skapar ett proxy-objekt för webb tjänsten i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b527-112">The cmdlet connects to a Web service and creates a Web service proxy object in PowerShell.</span></span> <span data-ttu-id="9b527-113">Du kan använda objektet proxy för att hantera webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="9b527-113">You can use the proxy object to manage the Web service.</span></span>

<span data-ttu-id="9b527-114">En webb tjänst är ett XML-baserat program som utbyter data över ett nätverk, särskilt via Internet.</span><span class="sxs-lookup"><span data-stu-id="9b527-114">A Web service is an XML-based program that exchanges data over a network, especially over the Internet.</span></span> <span data-ttu-id="9b527-115">Microsoft .NET Framework tillhandahåller proxy-objekt för webb tjänsten som representerar webb tjänsten som ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="9b527-115">The Microsoft .NET Framework provides Web service proxy objects that represent the Web service as a .NET Framework object.</span></span>

## <span data-ttu-id="9b527-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9b527-116">EXAMPLES</span></span>

### <span data-ttu-id="9b527-117">Exempel 1: skapa en proxy för en webb tjänst</span><span class="sxs-lookup"><span data-stu-id="9b527-117">Example 1: Create a proxy for a Web service</span></span>

<span data-ttu-id="9b527-118">I det här exemplet skapas en .NET Framework proxy för webb tjänsten kalkylator i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b527-118">This example creates a .NET Framework proxy of the calculator Web service in Windows PowerShell.</span></span>

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### <span data-ttu-id="9b527-119">Exempel 2: skapa en proxy för en webb tjänst och ange namnrymd och klass</span><span class="sxs-lookup"><span data-stu-id="9b527-119">Example 2: Create a proxy for a Web service and specify namespace and class</span></span>

<span data-ttu-id="9b527-120">I det här exemplet används `New-WebServiceProxy` cmdleten för att skapa en .NET Framework proxy för webb tjänsten kalkylator.</span><span class="sxs-lookup"><span data-stu-id="9b527-120">This example uses the `New-WebServiceProxy` cmdlet to create a .NET Framework proxy of the calculator Web service.</span></span>

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

<span data-ttu-id="9b527-121">Kommandot använder **URI** -parametern för att ange URI: n och **namn området** och **klass** parametrarna för att ange objektets namnrymd och klass.</span><span class="sxs-lookup"><span data-stu-id="9b527-121">The command uses the **Uri** parameter to specify the URI and the **Namespace** and **Class** parameters to specify the namespace and class of the object.</span></span>

### <span data-ttu-id="9b527-122">Exempel 3: Visa metoder för en webbtjänstproxy</span><span class="sxs-lookup"><span data-stu-id="9b527-122">Example 3: Display methods of a Web service proxy</span></span>

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

<span data-ttu-id="9b527-123">I det här exemplet används `Get-Member` cmdleten för att Visa metoderna för webbtjänstproxyn för Web Service i `$calc` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9b527-123">This example uses the `Get-Member` cmdlet to display the methods of the Web service proxy object in the `$calc` variable.</span></span> <span data-ttu-id="9b527-124">Vi använder dessa metoder i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="9b527-124">We uses these methods in the following example.</span></span>

<span data-ttu-id="9b527-125">Observera att **TypeName** för proxyobjekt, WebServiceProxy, återspeglar namn området och klass namnen som angavs i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="9b527-125">Notice that the **TypeName** of the proxy object, WebServiceProxy, reflects the namespace and class names that were specified in the previous example.</span></span>

### <span data-ttu-id="9b527-126">Exempel 4: Använd en webbtjänstproxy</span><span class="sxs-lookup"><span data-stu-id="9b527-126">Example 4: Use a Web service proxy</span></span>

```powershell
PS> $calc.Multiply(6,7)
42
```

<span data-ttu-id="9b527-127">I det här exemplet används webbtjänstproxyn som lagras i `$calc` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9b527-127">This example uses the Web service proxy stored in the `$calc` variable.</span></span> <span data-ttu-id="9b527-128">Kommandot använder metoden **multiplikation** i proxyn.</span><span class="sxs-lookup"><span data-stu-id="9b527-128">The command uses the **Multiply** method of the proxy.</span></span>

## <span data-ttu-id="9b527-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9b527-129">PARAMETERS</span></span>

### <span data-ttu-id="9b527-130">– Klass</span><span class="sxs-lookup"><span data-stu-id="9b527-130">-Class</span></span>

<span data-ttu-id="9b527-131">Anger ett namn för den proxy-klass som cmdleten skapar för webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="9b527-131">Specifies a name for the proxy class that the cmdlet creates for the Web service.</span></span> <span data-ttu-id="9b527-132">Värdet för den här parametern används tillsammans med **namn områdes** parametern för att tillhandahålla ett fullständigt kvalificerat namn för klassen.</span><span class="sxs-lookup"><span data-stu-id="9b527-132">The value of this parameter is used together with the **Namespace** parameter to provide a fully qualified name for the class.</span></span> <span data-ttu-id="9b527-133">Standardvärdet genereras från Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="9b527-133">The default value is generated from the Uniform Resource Identifier (URI).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b527-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="9b527-134">-Credential</span></span>

<span data-ttu-id="9b527-135">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="9b527-135">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="9b527-136">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="9b527-136">The default is the current user.</span></span> <span data-ttu-id="9b527-137">Detta är ett alternativ till att använda parametern **UseDefaultCredential** .</span><span class="sxs-lookup"><span data-stu-id="9b527-137">This is an alternative to using the **UseDefaultCredential** parameter.</span></span>

<span data-ttu-id="9b527-138">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b527-138">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9b527-139">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b527-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b527-140">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="9b527-140">-Namespace</span></span>

<span data-ttu-id="9b527-141">Anger ett namn område för den nya klassen.</span><span class="sxs-lookup"><span data-stu-id="9b527-141">Specifies a namespace for the new class.</span></span>

<span data-ttu-id="9b527-142">Värdet för den här parametern används tillsammans med värdet för **klass** parametern för att generera ett fullständigt kvalificerat namn för klassen.</span><span class="sxs-lookup"><span data-stu-id="9b527-142">The value of this parameter is used together with the value of the **Class** parameter to generate a fully qualified name for the class.</span></span> <span data-ttu-id="9b527-143">Standardvärdet är **Microsoft. PowerShell. commands. NewWebserviceProxy. AutogeneratedTypes** plus en typ som genereras från URI: n.</span><span class="sxs-lookup"><span data-stu-id="9b527-143">The default value is **Microsoft.PowerShell.Commands.NewWebserviceProxy.AutogeneratedTypes** plus a type that is generated from the URI.</span></span>

<span data-ttu-id="9b527-144">Du kan ange värdet för parametern **namespace** så att du kan komma åt flera webb tjänster som har samma namn.</span><span class="sxs-lookup"><span data-stu-id="9b527-144">You can set the value of the **Namespace** parameter so that you can access multiple Web services that have the same name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b527-145">-URI</span><span class="sxs-lookup"><span data-stu-id="9b527-145">-Uri</span></span>

<span data-ttu-id="9b527-146">Anger webb tjänstens URI.</span><span class="sxs-lookup"><span data-stu-id="9b527-146">Specifies the URI of the Web service.</span></span> <span data-ttu-id="9b527-147">Ange en URI eller sökväg och fil namn för en fil som innehåller en tjänst beskrivning.</span><span class="sxs-lookup"><span data-stu-id="9b527-147">Enter a URI or the path and filename of a file that contains a service description.</span></span>

<span data-ttu-id="9b527-148">URI: n måste returnera en `.asmx` sida eller till en sida som returnerar en tjänst beskrivning.</span><span class="sxs-lookup"><span data-stu-id="9b527-148">The URI must return an `.asmx` page or to a page that returns a service description.</span></span> <span data-ttu-id="9b527-149">Om du vill returnera en tjänst Beskrivning av en webb tjänst som skapades med ASP.NET lägger du till? WSDL "till URL: en för webb tjänsten (till exempel `http://www.contoso.com/MyWebService.asmx?WSDL` ).</span><span class="sxs-lookup"><span data-stu-id="9b527-149">To return a service description of a Web service that was created using ASP.NET, append "?WSDL" to the URL of the Web service (for example, `http://www.contoso.com/MyWebService.asmx?WSDL`).</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b527-150">-UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="9b527-150">-UseDefaultCredential</span></span>

<span data-ttu-id="9b527-151">Anger att denna cmdlet använder standard referensen.</span><span class="sxs-lookup"><span data-stu-id="9b527-151">Indicates that this cmdlet uses the default credential.</span></span> <span data-ttu-id="9b527-152">Denna cmdlet anger egenskapen **UseDefaultCredential** i det resulterande proxyobjekt till true.</span><span class="sxs-lookup"><span data-stu-id="9b527-152">This cmdlet sets the **UseDefaultCredential** property in the resulting proxy object to True.</span></span> <span data-ttu-id="9b527-153">Detta är ett alternativ till att använda parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="9b527-153">This is an alternative to using the **Credential** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b527-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b527-154">CommonParameters</span></span>

<span data-ttu-id="9b527-155">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b527-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b527-156">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9b527-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b527-157">INDATA</span><span class="sxs-lookup"><span data-stu-id="9b527-157">INPUTS</span></span>

### <span data-ttu-id="9b527-158">Inget</span><span class="sxs-lookup"><span data-stu-id="9b527-158">None</span></span>

<span data-ttu-id="9b527-159">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b527-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9b527-160">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9b527-160">OUTPUTS</span></span>

### <span data-ttu-id="9b527-161">Ett proxy-objekt för webb tjänst</span><span class="sxs-lookup"><span data-stu-id="9b527-161">A Web service proxy object</span></span>

<span data-ttu-id="9b527-162">Denna cmdlet returnerar ett proxy-objekt för webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="9b527-162">This cmdlet returns a Web service proxy object.</span></span> <span data-ttu-id="9b527-163">Objektets namnrymd och klass bestäms av kommandots parametrar.</span><span class="sxs-lookup"><span data-stu-id="9b527-163">The namespace and class of the object are determined by the parameters of the command.</span></span> <span data-ttu-id="9b527-164">Standardvärdet genereras från indataports-URI: n.</span><span class="sxs-lookup"><span data-stu-id="9b527-164">The default is generated from the input URI.</span></span>

## <span data-ttu-id="9b527-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9b527-165">NOTES</span></span>

<span data-ttu-id="9b527-166">`New-WebServiceProxy` använder klassen **system .net. WebClient** för att läsa in den angivna webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="9b527-166">`New-WebServiceProxy` uses the **System.Net.WebClient** class to load the specified Web service.</span></span>

## <span data-ttu-id="9b527-167">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9b527-167">RELATED LINKS</span></span>

[<span data-ttu-id="9b527-168">New-Service</span><span class="sxs-lookup"><span data-stu-id="9b527-168">New-Service</span></span>](New-Service.md)
