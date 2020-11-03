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
# New-WebServiceProxy

## SAMMANFATTNING
Skapar ett proxy-objekt för webb tjänsten som gör att du kan använda och hantera webb tjänsten i PowerShell.

## SYNTAX

### Nocredentials (standard)

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### Autentiseringsuppgift

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### UseDefaultCredential

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## BESKRIVNING

Med `New-WebServiceProxy` cmdleten kan du använda en webb tjänst i PowerShell. Cmdleten ansluter till en webb tjänst och skapar ett proxy-objekt för webb tjänsten i PowerShell. Du kan använda objektet proxy för att hantera webb tjänsten.

En webb tjänst är ett XML-baserat program som utbyter data över ett nätverk, särskilt via Internet. Microsoft .NET Framework tillhandahåller proxy-objekt för webb tjänsten som representerar webb tjänsten som ett .NET Framework-objekt.

## EXEMPEL

### Exempel 1: skapa en proxy för en webb tjänst

I det här exemplet skapas en .NET Framework proxy för webb tjänsten kalkylator i Windows PowerShell.

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### Exempel 2: skapa en proxy för en webb tjänst och ange namnrymd och klass

I det här exemplet används `New-WebServiceProxy` cmdleten för att skapa en .NET Framework proxy för webb tjänsten kalkylator.

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

Kommandot använder **URI** -parametern för att ange URI: n och **namn området** och **klass** parametrarna för att ange objektets namnrymd och klass.

### Exempel 3: Visa metoder för en webbtjänstproxy

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

I det här exemplet används `Get-Member` cmdleten för att Visa metoderna för webbtjänstproxyn för Web Service i `$calc` variabeln. Vi använder dessa metoder i följande exempel.

Observera att **TypeName** för proxyobjekt, WebServiceProxy, återspeglar namn området och klass namnen som angavs i föregående exempel.

### Exempel 4: Använd en webbtjänstproxy

```powershell
PS> $calc.Multiply(6,7)
42
```

I det här exemplet används webbtjänstproxyn som lagras i `$calc` variabeln. Kommandot använder metoden **multiplikation** i proxyn.

## PARAMETRAR

### – Klass

Anger ett namn för den proxy-klass som cmdleten skapar för webb tjänsten. Värdet för den här parametern används tillsammans med **namn områdes** parametern för att tillhandahålla ett fullständigt kvalificerat namn för klassen. Standardvärdet genereras från Uniform Resource Identifier (URI).

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

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren. Detta är ett alternativ till att använda parametern **UseDefaultCredential** .

Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

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

### – Namnrymd

Anger ett namn område för den nya klassen.

Värdet för den här parametern används tillsammans med värdet för **klass** parametern för att generera ett fullständigt kvalificerat namn för klassen. Standardvärdet är **Microsoft. PowerShell. commands. NewWebserviceProxy. AutogeneratedTypes** plus en typ som genereras från URI: n.

Du kan ange värdet för parametern **namespace** så att du kan komma åt flera webb tjänster som har samma namn.

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

### -URI

Anger webb tjänstens URI. Ange en URI eller sökväg och fil namn för en fil som innehåller en tjänst beskrivning.

URI: n måste returnera en `.asmx` sida eller till en sida som returnerar en tjänst beskrivning. Om du vill returnera en tjänst Beskrivning av en webb tjänst som skapades med ASP.NET lägger du till? WSDL "till URL: en för webb tjänsten (till exempel `http://www.contoso.com/MyWebService.asmx?WSDL` ).

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

### -UseDefaultCredential

Anger att denna cmdlet använder standard referensen. Denna cmdlet anger egenskapen **UseDefaultCredential** i det resulterande proxyobjekt till true. Detta är ett alternativ till att använda parametern **Credential** .

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Ett proxy-objekt för webb tjänst

Denna cmdlet returnerar ett proxy-objekt för webb tjänsten. Objektets namnrymd och klass bestäms av kommandots parametrar. Standardvärdet genereras från indataports-URI: n.

## ANTECKNINGAR

`New-WebServiceProxy` använder klassen **system .net. WebClient** för att läsa in den angivna webb tjänsten.

## RELATERADE LÄNKAR

[New-Service](New-Service.md)
