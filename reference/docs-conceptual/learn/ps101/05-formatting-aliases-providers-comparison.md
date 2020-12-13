---
title: Formatering, alias, leverantörer, jämförelse
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: I det här kapitlet beskrivs begreppen utdata, kommando-alias, providers och jämförelse åtgärder.
ms.openlocfilehash: efe70d2d220f8451e781603b6000c3553dda910c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501617"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a><span data-ttu-id="0b9cd-103">Kapitel 5 – formatering, alias, providers, jämförelse</span><span class="sxs-lookup"><span data-stu-id="0b9cd-103">Chapter 5 - Formatting, aliases, providers, comparison</span></span>

## <a name="requirements"></a><span data-ttu-id="0b9cd-104">Krav</span><span class="sxs-lookup"><span data-stu-id="0b9cd-104">Requirements</span></span>

<span data-ttu-id="0b9cd-105">Den SQL Server PowerShell-modulen krävs av några av exemplen som visas i det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-105">The SQL Server PowerShell module is required by some of the examples shown in this chapter.</span></span> <span data-ttu-id="0b9cd-106">Modulen installeras som en del av [SQL Server Management Studio (Smss)][SMSS].</span><span class="sxs-lookup"><span data-stu-id="0b9cd-106">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="0b9cd-107">Den används också i efterföljande kapitel.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-107">It's also used in subsequent chapters.</span></span> <span data-ttu-id="0b9cd-108">Ladda ned och installera den på datorn med Windows 10 labb miljö.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-108">Download and install it on your Windows 10 lab environment computer.</span></span>

## <a name="format-right"></a><span data-ttu-id="0b9cd-109">Formatera höger</span><span class="sxs-lookup"><span data-stu-id="0b9cd-109">Format Right</span></span>

<span data-ttu-id="0b9cd-110">I kapitel 4 har du lärt dig att filtrera så långt till vänster som möjligt.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-110">In Chapter 4, you learned to filter as far to the left as possible.</span></span> <span data-ttu-id="0b9cd-111">Regeln för manuell formatering av ett kommandos utdata liknar den regeln, förutom att det måste inträffa så långt till höger som möjligt.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-111">The rule for manually formatting a command's output is similar to that rule except it needs to occur as far to the right as possible.</span></span>

<span data-ttu-id="0b9cd-112">De vanligaste format kommandona är `Format-Table` och `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="0b9cd-112">The most common format commands are `Format-Table` and `Format-List`.</span></span> <span data-ttu-id="0b9cd-113">`Format-Wide` och `Format-Custom` kan också användas, men är mindre vanliga.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-113">`Format-Wide` and `Format-Custom` can also be used, but are less common.</span></span>

<span data-ttu-id="0b9cd-114">Som anges i kapitel 3, ett kommando som returnerar fler än fyra egenskaper till en lista, om inte anpassad formatering används.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-114">As mentioned in Chapter 3, a command that returns more than four properties defaults to a list unless custom formatting is used.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="0b9cd-115">Använd `Format-Table` cmdleten för att manuellt åsidosätta formateringen och visa utdata i en tabell i stället för en lista.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-115">Use the `Format-Table` cmdlet to manually override the formatting and show the output in a table instead of a list.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

<span data-ttu-id="0b9cd-116">Standardutdata för `Get-Service` är tre egenskaper i en tabell.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-116">The default output for `Get-Service` is three properties in a table.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="0b9cd-117">Använd `Format-List` cmdleten för att åsidosätta standardformateringen och returnera resultatet i en lista.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-117">Use the `Format-List` cmdlet to override the default formatting and return the results in a list.</span></span>

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

<span data-ttu-id="0b9cd-118">Observera att det bara rör `Get-Service` sig om att lämna `Format-List` tillbaka ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-118">Notice that simply piping `Get-Service` to `Format-List` made it return additional properties.</span></span> <span data-ttu-id="0b9cd-119">Detta inträffar inte med varje kommando på grund av hur formateringen för det specifika kommandot har kon figurer ATS i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-119">This doesn't occur with every command because of the way the formatting for that particular command is set up behind the scenes.</span></span>

<span data-ttu-id="0b9cd-120">Antalet som är ett sak att vara medveten om med format-cmdletar är att de producerar format objekt som skiljer sig från vanliga objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-120">The number one thing to be aware of with the format cmdlets is they produce format objects that are different than normal objects in PowerShell.</span></span>

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

<span data-ttu-id="0b9cd-121">Det innebär att format kommandon inte kan skickas till de flesta andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-121">What this means is format commands can't be piped to most other commands.</span></span> <span data-ttu-id="0b9cd-122">De kan skickas till några av `Out-*` kommandona, men det är det.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-122">They can be piped to some of the `Out-*` commands, but that's about it.</span></span> <span data-ttu-id="0b9cd-123">Detta är anledningen till varför du vill utföra formateringen i slutet av raden (format höger).</span><span class="sxs-lookup"><span data-stu-id="0b9cd-123">This is why you want to perform any formatting at the very end of the line (format right).</span></span>

## <a name="aliases"></a><span data-ttu-id="0b9cd-124">Alias</span><span class="sxs-lookup"><span data-stu-id="0b9cd-124">Aliases</span></span>

<span data-ttu-id="0b9cd-125">Ett alias i PowerShell är ett kortare namn för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-125">An alias in PowerShell is a shorter name for a command.</span></span> <span data-ttu-id="0b9cd-126">PowerShell innehåller en uppsättning inbyggda alias och du kan också definiera egna alias.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-126">PowerShell includes a set of built-in aliases and you can also define your own aliases.</span></span>

<span data-ttu-id="0b9cd-127">`Get-Alias`Cmdleten används för att hitta alias.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-127">The `Get-Alias` cmdlet is used to find aliases.</span></span> <span data-ttu-id="0b9cd-128">Om du redan känner till aliaset för ett kommando används **namn** parametern för att avgöra vilket kommando som aliaset är associerat med.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-128">If you already know the alias for a command, the **Name** parameter is used to determine what command the alias is associated with.</span></span>

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

<span data-ttu-id="0b9cd-129">Du kan ange flera alias för värdet för **Name** -parametern.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-129">Multiple aliases can be specified for the value of the **Name** parameter.</span></span>

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="0b9cd-130">Du kan ofta se **namn** parametern som utelämnats eftersom det är en positions parameter.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-130">You'll often see the **Name** parameter omitted since it's a positional parameter.</span></span>

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

<span data-ttu-id="0b9cd-131">Om du vill söka efter alias för ett kommando måste du använda **definitions** parametern.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-131">If you want to find aliases for a command, you'll need to use the **Definition** parameter.</span></span>

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="0b9cd-132">Det går inte att använda **definitions** parametern i stället för att den måste anges.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-132">The **Definition** parameter can't be used positionally so it must be specified.</span></span>

<span data-ttu-id="0b9cd-133">Alias kan spara några tangenttryckningar och de är bra när du skriver in kommandon i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-133">Aliases can save you a few keystrokes and they're fine when you're typing commands into the console.</span></span>
<span data-ttu-id="0b9cd-134">De bör inte användas i skript eller någon kod som du sparar eller delar med andra.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-134">They shouldn't be used in scripts or any code that you're saving or sharing with others.</span></span> <span data-ttu-id="0b9cd-135">Som tidigare nämnts i den här boken, är det enkelt att förstå om du använder fullständig cmdlet och parameter namn.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-135">As mentioned earlier in this book, using full cmdlet and parameter names is self-documenting and easier to understand.</span></span>

<span data-ttu-id="0b9cd-136">Var försiktig när du skapar egna alias eftersom de bara finns i den aktuella PowerShell-sessionen på din dator.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-136">Use caution when creating your own aliases because they'll only exist in your current PowerShell session on your computer.</span></span>

## <a name="providers"></a><span data-ttu-id="0b9cd-137">Leverantörer</span><span class="sxs-lookup"><span data-stu-id="0b9cd-137">Providers</span></span>

<span data-ttu-id="0b9cd-138">En provider i PowerShell är ett gränssnitt som gör det möjligt att använda fil systemet till exempel åtkomst till ett data lager.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-138">A provider in PowerShell is an interface that allows file system like access to a datastore.</span></span> <span data-ttu-id="0b9cd-139">Det finns ett antal inbyggda providrar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-139">There are a number of built-in providers in PowerShell.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

<span data-ttu-id="0b9cd-140">Som du kan se i föregående resultat finns det inbyggda providers för registret, alias, miljövariabler, fil systemet, funktioner, variabler, certifikat och WSMan.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-140">As you can see in the previous results, there are built-in providers for the registry, aliases, environment variables, the file system, functions, variables, certificates, and WSMan.</span></span>

<span data-ttu-id="0b9cd-141">De faktiska enheterna som dessa leverantörer använder för att exponera sina data lager kan bestämmas med `Get-PSDrive` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-141">The actual drives that these providers use to expose their datastore can be determined with the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="0b9cd-142">`Get-PSDrive`Cmdlet: en visar inte bara enheter som exponeras av providers, men visar även logiska Windows-enheter, inklusive enheter som är mappade till nätverks resurser.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-142">The `Get-PSDrive` cmdlet not only displays drives exposed by providers, but it also displays Windows logical drives including drives mapped to network shares.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="0b9cd-143">Moduler från tredje part, till exempel Active Directory PowerShell-modulen och SQLServer PowerShell-modulen, lägger både till sin egen PowerShell-Provider och PSDrive.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-143">Third-party modules such as the Active Directory PowerShell module and the SQLServer PowerShell module both add their own PowerShell provider and PSDrive.</span></span>

<span data-ttu-id="0b9cd-144">Importera Active Directory och SQL Server PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-144">Import the Active Directory and SQL Server PowerShell modules.</span></span>

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

<span data-ttu-id="0b9cd-145">Kontrol lera om ytterligare PowerShell-leverantörer har lagts till.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-145">Check to see if any additional PowerShell providers were added.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

<span data-ttu-id="0b9cd-146">Observera att två nya PowerShell-leverantörer nu finns i den föregående uppsättningen med resultat, en för Active Directory och en annan för SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-146">Notice that in the previous set of results, two new PowerShell providers now exist, one for Active Directory and another one for SQL Server.</span></span>

<span data-ttu-id="0b9cd-147">En PSDrive för var och en av dessa moduler har också lagts till.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-147">A PSDrive for each of those modules was also added.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="0b9cd-148">PSDrives kan nås precis som ett traditionellt fil system.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-148">PSDrives can be accessed just like a traditional file system.</span></span>

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a><span data-ttu-id="0b9cd-149">Jämförelseoperatorer</span><span class="sxs-lookup"><span data-stu-id="0b9cd-149">Comparison Operators</span></span>

<span data-ttu-id="0b9cd-150">PowerShell innehåller ett antal jämförelse operatorer som används för att jämföra värden eller hitta värden som matchar vissa mönster.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-150">PowerShell contains a number of comparison operators that are used to compare values or find values that match certain patterns.</span></span> <span data-ttu-id="0b9cd-151">Tabell 5-1 innehåller en lista över jämförelse operatorer i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-151">Table 5-1 contains a list of comparison operators in PowerShell.</span></span>

|    <span data-ttu-id="0b9cd-152">Operator</span><span class="sxs-lookup"><span data-stu-id="0b9cd-152">Operator</span></span>    |                          <span data-ttu-id="0b9cd-153">Definition</span><span class="sxs-lookup"><span data-stu-id="0b9cd-153">Definition</span></span>                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | <span data-ttu-id="0b9cd-154">Lika med</span><span class="sxs-lookup"><span data-stu-id="0b9cd-154">Equal to</span></span>                                                     |
| `-ne`          | <span data-ttu-id="0b9cd-155">Inte lika med</span><span class="sxs-lookup"><span data-stu-id="0b9cd-155">Not equal to</span></span>                                                 |
| `-gt`          | <span data-ttu-id="0b9cd-156">Större än</span><span class="sxs-lookup"><span data-stu-id="0b9cd-156">Greater than</span></span>                                                 |
| `-ge`          | <span data-ttu-id="0b9cd-157">Större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="0b9cd-157">Greater than or equal to</span></span>                                     |
| `-lt`          | <span data-ttu-id="0b9cd-158">Mindre än</span><span class="sxs-lookup"><span data-stu-id="0b9cd-158">Less than</span></span>                                                    |
| `-le`          | <span data-ttu-id="0b9cd-159">Mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="0b9cd-159">Less than or equal to</span></span>                                        |
| `-Like`        | <span data-ttu-id="0b9cd-160">Matcha med `*` jokertecknet</span><span class="sxs-lookup"><span data-stu-id="0b9cd-160">Match using the `*` wildcard character</span></span>                       |
| `-NotLike`     | <span data-ttu-id="0b9cd-161">Överensstämmer inte med `*` jokertecknet</span><span class="sxs-lookup"><span data-stu-id="0b9cd-161">Does not match using the `*` wildcard character</span></span>              |
| `-Match`       | <span data-ttu-id="0b9cd-162">Matchar det angivna reguljära uttrycket</span><span class="sxs-lookup"><span data-stu-id="0b9cd-162">Matches the specified regular expression</span></span>                     |
| `-NotMatch`    | <span data-ttu-id="0b9cd-163">Matchar inte det angivna reguljära uttrycket</span><span class="sxs-lookup"><span data-stu-id="0b9cd-163">Does not match the specified regular expression</span></span>              |
| `-Contains`    | <span data-ttu-id="0b9cd-164">Anger om en samling innehåller ett angivet värde</span><span class="sxs-lookup"><span data-stu-id="0b9cd-164">Determines if a collection contains a specified value</span></span>        |
| `-NotContains` | <span data-ttu-id="0b9cd-165">Anger om en samling inte innehåller ett angivet värde</span><span class="sxs-lookup"><span data-stu-id="0b9cd-165">Determines if a collection does not contain a specific value</span></span> |
| `-In`          | <span data-ttu-id="0b9cd-166">Anger om ett angivet värde finns i en samling</span><span class="sxs-lookup"><span data-stu-id="0b9cd-166">Determines if a specified value is in a collection</span></span>           |
| `-NotIn`       | <span data-ttu-id="0b9cd-167">Anger om ett angivet värde inte finns i en samling</span><span class="sxs-lookup"><span data-stu-id="0b9cd-167">Determines if a specified value is not in a collection</span></span>       |
| `-Replace`     | <span data-ttu-id="0b9cd-168">Ersätter det angivna värdet</span><span class="sxs-lookup"><span data-stu-id="0b9cd-168">Replaces the specified value</span></span>                                 |

<span data-ttu-id="0b9cd-169">Alla operatorer som anges i tabell 5-1 är Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-169">All of the operators listed in Table 5-1 are case-insensitive.</span></span> <span data-ttu-id="0b9cd-170">Placera en `c` framför operatorn som visas i tabell 5-1 för att göra den Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-170">Place a `c` in front of the operator listed in Table 5-1 to make it case-sensitive.</span></span> <span data-ttu-id="0b9cd-171">Till exempel `-ceq` är den Skift läges känsliga versionen av `-eq` jämförelse operatorn.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-171">For example, `-ceq` is the case-sensitive version of the `-eq` comparison operator.</span></span>

<span data-ttu-id="0b9cd-172">Gemener "PowerShell" är lika med gemener "PowerShell" med hjälp av jämförelse operatorn Equals.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-172">Proper case "PowerShell" is equal to lower case "powershell" using the equals comparison operator.</span></span>

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

<span data-ttu-id="0b9cd-173">Den är inte lika med den Skift läges känsliga versionen av jämförelse operatorn Equals.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-173">It's not equal using the case-sensitive version of the equals comparison operator.</span></span>

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

<span data-ttu-id="0b9cd-174">Den icke-identiska jämförelse operatorn kastar om villkoret.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-174">The not equal comparison operator reverses the condition.</span></span>

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

<span data-ttu-id="0b9cd-175">Större än, större än eller lika med, mindre än och mindre än eller lika med alla fungerar med sträng eller numeriska värden.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-175">Greater than, greater than or equal to, less than, and less than or equal all work with string or numeric values.</span></span>

```powershell
5 -gt 5
```

```Output
False
```

<span data-ttu-id="0b9cd-176">Om du använder större än eller lika med i stället för större än med föregående exempel returneras det **booleska** värdet True eftersom fem är lika med fem.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-176">Using greater than or equal to instead of greater than with the previous example returns the **Boolean** true since five is equal to five.</span></span>

```powershell
5 -ge 5
```

```Output
True
```

<span data-ttu-id="0b9cd-177">Baserat på resultaten från de föregående två exemplen kan du förmodligen gissa dig att både mindre än och mindre än eller lika med fungerar.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-177">Based on the results from the previous two examples, you can probably guess how both less than and less than or equal to work.</span></span>

```powershell
5 -lt 10
```

```Output
True
```

<span data-ttu-id="0b9cd-178">`-Like` `-Match` Operatorerna och kan vara förvirrande, även för erfarna PowerShell-användare.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-178">The `-Like` and `-Match` operators can be confusing, even for experienced PowerShell users.</span></span> <span data-ttu-id="0b9cd-179">`-Like` används med jokertecken för tecknen `*` och `?` för att utföra "Like"-matchningar.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-179">`-Like` is used with wildcard the characters `*` and `?` to perform "like" matches.</span></span>

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

<span data-ttu-id="0b9cd-180">`-Match` använder ett reguljärt uttryck för att utföra matchningen.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-180">`-Match` uses a regular expression to perform the matching.</span></span>

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

<span data-ttu-id="0b9cd-181">Använd operatorn Range för att lagra talen 1 till och med 10 i en variabel.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-181">Use the range operator to store the numbers 1 through 10 in a variable.</span></span>

```powershell
$Numbers = 1..10
```

```Output
```

<span data-ttu-id="0b9cd-182">Ta reda på om `$Numbers` variabeln innehåller 15.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-182">Determine if the `$Numbers` variable includes 15.</span></span>

```powershell
$Numbers -contains 15
```

```Output
False
```

<span data-ttu-id="0b9cd-183">Kontrol lera om det innehåller numret 10.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-183">Determine if it includes the number 10.</span></span>

```powershell
$Numbers -contains 10
```

```Output
True
```

<span data-ttu-id="0b9cd-184">`-NotContains` kastar om logiken för att se om `$Numbers` variabeln inte innehåller något värde.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-184">`-NotContains` reverses the logic to see if the `$Numbers` variable doesn't contain a value.</span></span>

```powershell
$Numbers -notcontains 15
```

```Output
True
```

<span data-ttu-id="0b9cd-185">Föregående exempel returnerar det **booleska** värdet sant eftersom det är sant att `$Numbers` variabeln inte innehåller 15.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-185">The previous example returns the **Boolean** true because it's true that the `$Numbers` variable doesn't contain 15.</span></span> <span data-ttu-id="0b9cd-186">Den innehåller dock talet 10 så det är falskt när det testas.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-186">It does however contain the number 10 so it's false when it's tested.</span></span>

```powershell
$Numbers -notcontains 10
```

```Output
False
```

<span data-ttu-id="0b9cd-187">Jämförelse operatorn "i" introducerades först i PowerShell version 3,0.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-187">The "in" comparison operator was first introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="0b9cd-188">Den används för att avgöra om ett värde är "i" en matris.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-188">It's used to determine if a value is "in" an array.</span></span> <span data-ttu-id="0b9cd-189">`$Numbers`Variabeln är en matris eftersom den innehåller flera värden.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-189">The `$Numbers` variable is an array since it contains multiple values.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="0b9cd-190">Med andra ord `-in` utförs samma test som innehåller jämförelse operatorn, förutom motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-190">In other words, `-in` performs the same test as the contains comparison operator except from the opposite direction.</span></span>

```powershell
10 -in $Numbers
```

```Output
True
```

<span data-ttu-id="0b9cd-191">15 finns inte i `$Numbers` matrisen så false returneras i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-191">15 isn't in the `$Numbers` array so false is returned in the following example.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="0b9cd-192">Precis som `-contains` operatorn `not` vänder sig `-in` operatorn för operatorn.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-192">Just like the `-contains` operator, `not` reverses the logic for the `-in` operator.</span></span>

```powershell
10 -notin $Numbers
```

```Output
False
```

<span data-ttu-id="0b9cd-193">Det tidigare exemplet returnerar false eftersom `$Numbers` matrisen innehåller 10 och villkoret kunde testas för att avgöra om det inte innehöll 10.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-193">The previous example returns false because the `$Numbers` array does include 10 and the condition was testing to determine if it didn't contain 10.</span></span>

<span data-ttu-id="0b9cd-194">15 är "inte i" `$Numbers` matrisen så att den returnerar det **booleska** värdet true.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-194">15 is "not in" the `$Numbers` array so it returns the **Boolean** true.</span></span>

```powershell
15 -notin $Numbers
```

```Output
True
```

<span data-ttu-id="0b9cd-195">`-replace`Operatören vill bara tänka dig.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-195">The `-replace` operator does just want you would think.</span></span> <span data-ttu-id="0b9cd-196">Den används för att ersätta något.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-196">It's used to replace something.</span></span> <span data-ttu-id="0b9cd-197">Om du anger ett värde ersätts värdet med Nothing.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-197">Specifying one value replaces that value with nothing.</span></span> <span data-ttu-id="0b9cd-198">I följande exempel ersätter jag "Shell" med Nothing.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-198">In the following example, I replace "Shell" with nothing.</span></span>

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

<span data-ttu-id="0b9cd-199">Om du vill ersätta ett värde med ett annat värde anger du det nya värdet efter det mönster som du vill ersätta.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-199">If you want to replace a value with a different value, specify the new value after the pattern you want to replace.</span></span> <span data-ttu-id="0b9cd-200">SQL lördag i Baton Rouge är en händelse som jag försöker tala om varje år.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-200">SQL Saturday in Baton Rouge is an event that I try to speak at every year.</span></span> <span data-ttu-id="0b9cd-201">I följande exempel ersätter jag ordet "lördag" med förkortningen "söt".</span><span class="sxs-lookup"><span data-stu-id="0b9cd-201">In the following example, I replace the word "Saturday" with the abbreviation "Sat".</span></span>

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="0b9cd-202">Det finns också metoder som **Ersätt ()** som kan användas för att ersätta saker som liknar hur ersättnings operatorn fungerar.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-202">There are also methods like **Replace()** that can be used to replace things similar to the way the replace operator works.</span></span> <span data-ttu-id="0b9cd-203">`-Replace`Operatorn är dock Skift läges känslig som standard och metoden **replace ()** är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-203">However, the `-Replace` operator is case-insensitive by default, and the **Replace()** method is case-sensitive.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

<span data-ttu-id="0b9cd-204">Observera att ordet "lördag" inte ersattes i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-204">Notice that the word "Saturday" wasn't replaced in the previous example.</span></span> <span data-ttu-id="0b9cd-205">Detta beror på att den angavs i ett annat fall än originalet.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-205">This is because it was specified in a different case than the original.</span></span> <span data-ttu-id="0b9cd-206">När ordet "lördag" anges i samma fall som den ursprungliga, ersätter metoden **replace ()** det som förväntat.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-206">When the word "Saturday" is specified in the same case as the original, the **Replace()** method does replace it as expected.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="0b9cd-207">Var försiktig när du använder metoder för att transformera data eftersom du kan köra oväntade problem, t. ex. om du inte gör ett _kalkon test_.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-207">Be careful when using methods to transform data because you can run into unforeseen problems, such as failing the _Turkey Test_.</span></span> <span data-ttu-id="0b9cd-208">Ett exempel finns i blogg artikeln om [att använda pester för att testa PowerShell-kod med andra kulturer][].</span><span class="sxs-lookup"><span data-stu-id="0b9cd-208">For an example, see the blog article titled [Using Pester to Test PowerShell Code with Other Cultures][].</span></span> <span data-ttu-id="0b9cd-209">Min rekommendation är att använda en operatör i stället för en metod när det är möjligt att undvika dessa typer av problem.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-209">My recommendation is to use an operator instead of a method whenever possible to avoid these types of problems.</span></span>

<span data-ttu-id="0b9cd-210">Även om jämförelse operatorerna kan användas som du ser i föregående exempel, kan jag normalt hitta själv med hjälp av `Where-Object` cmdleten för att utföra viss typ av filtrering.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-210">While the comparison operators can be used as shown in the previous examples, I normally find myself using them with the `Where-Object` cmdlet to perform some type of filtering.</span></span>

## <a name="summary"></a><span data-ttu-id="0b9cd-211">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="0b9cd-211">Summary</span></span>

<span data-ttu-id="0b9cd-212">I det här kapitlet har du lärt dig ett antal olika ämnen för att ta med formatering höger, alias, providers och jämförelse operatorer.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-212">In this chapter, you've learned a number of different topics to include Formatting Right, Aliases, Providers, and Comparison Operators.</span></span>

## <a name="review"></a><span data-ttu-id="0b9cd-213">Genomgång</span><span class="sxs-lookup"><span data-stu-id="0b9cd-213">Review</span></span>

1. <span data-ttu-id="0b9cd-214">Varför är det nödvändigt att göra formateringen så långt till höger som möjligt?</span><span class="sxs-lookup"><span data-stu-id="0b9cd-214">Why is it necessary to perform Formatting as far to the right as possible?</span></span>
1. <span data-ttu-id="0b9cd-215">Hur avgör du vad den faktiska cmdleten är för `%` aliaset?</span><span class="sxs-lookup"><span data-stu-id="0b9cd-215">How do you determine what the actual cmdlet is for the `%` alias?</span></span>
1. <span data-ttu-id="0b9cd-216">Varför ska du inte använda alias i skript som du sparar eller kodar som du delar med andra?</span><span class="sxs-lookup"><span data-stu-id="0b9cd-216">Why shouldn't you use aliases in scripts you save or code you share with others?</span></span>
1. <span data-ttu-id="0b9cd-217">Utföra en katalog lista på de enheter som är associerade med en av register leverantörerna.</span><span class="sxs-lookup"><span data-stu-id="0b9cd-217">Perform a directory listing on the drives that are associated with one of the registry providers.</span></span>
1. <span data-ttu-id="0b9cd-218">Vad är en av de största fördelarna med att använda ersättnings operatorn i stället för ersättnings metoden?</span><span class="sxs-lookup"><span data-stu-id="0b9cd-218">What's one of the main benefits of using the replace operator instead of the replace method?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="0b9cd-219">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="0b9cd-219">Recommended Reading</span></span>

- <span data-ttu-id="0b9cd-220">[Format-Table][]</span><span class="sxs-lookup"><span data-stu-id="0b9cd-220">[Format-Table][]</span></span>
- <span data-ttu-id="0b9cd-221">[Format-List][]</span><span class="sxs-lookup"><span data-stu-id="0b9cd-221">[Format-List][]</span></span>
- <span data-ttu-id="0b9cd-222">[Format-Wide][]</span><span class="sxs-lookup"><span data-stu-id="0b9cd-222">[Format-Wide][]</span></span>
- <span data-ttu-id="0b9cd-223">[about_Aliases][]</span><span class="sxs-lookup"><span data-stu-id="0b9cd-223">[about_Aliases][]</span></span>
- <span data-ttu-id="0b9cd-224">[about_Providers][]</span><span class="sxs-lookup"><span data-stu-id="0b9cd-224">[about_Providers][]</span></span>
- <span data-ttu-id="0b9cd-225">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="0b9cd-225">[about_Comparison_Operators][]</span></span>
- <span data-ttu-id="0b9cd-226">[about_Arrays][]</span><span class="sxs-lookup"><span data-stu-id="0b9cd-226">[about_Arrays][]</span></span>

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Använda pester för att testa PowerShell-kod med andra kulturer]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
[Using Pester to Test PowerShell Code with Other Cultures]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
