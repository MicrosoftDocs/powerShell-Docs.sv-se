---
title: Identifiera objekt, egenskaper och metoder
description: Du behöver inte vara utvecklare för att förstå och använda objekt, egenskaper och metoder.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 5ab972755afeba0d94bf6c2debaf84ec84cd9244
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436367"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a><span data-ttu-id="2ea53-103">Kapitel 3 – identifiera objekt, egenskaper och metoder</span><span class="sxs-lookup"><span data-stu-id="2ea53-103">Chapter 3 - Discovering objects, properties, and methods</span></span>

<span data-ttu-id="2ea53-104">Min första introduktion till datorer var en Commodore 64, men min första moderna dator var 286 12 MHz IBM-klon med 1 megabyte minne, en 40-megabyte-hårddisk och en 5-1/4-tums diskett enhet med CGA-övervakaren som kör Microsoft DOS 3,3.</span><span class="sxs-lookup"><span data-stu-id="2ea53-104">My first introduction to computers was a Commodore 64, but my first modern computer was a 286 12-Mhz IBM clone with 1 megabyte of memory, a 40-megabyte hard drive, and one 5-1/4 inch floppy disk drive with a CGA monitor running Microsoft DOS 3.3.</span></span>

<span data-ttu-id="2ea53-105">Många IT-proffs, precis som mig, är inte Stranger till kommando raden, men när objektets, egenskapernas och metodernas ämne hämtas, får de Deer i Headlights look och säger "Jag är inte utvecklare".</span><span class="sxs-lookup"><span data-stu-id="2ea53-105">Many IT Pros, like myself, are no stranger to the command line, but when the subject of objects, properties, and methods comes up, they get the deer in the headlights look and say, "I'm not a developer."</span></span> <span data-ttu-id="2ea53-106">Gissa vad?</span><span class="sxs-lookup"><span data-stu-id="2ea53-106">Guess what?</span></span> <span data-ttu-id="2ea53-107">Du behöver inte vara utvecklare för att lyckas med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ea53-107">You don't have to be a developer to be successful with PowerShell.</span></span> <span data-ttu-id="2ea53-108">Få inte bogged nedåt i terminologin.</span><span class="sxs-lookup"><span data-stu-id="2ea53-108">Don't get bogged down in the terminology.</span></span> <span data-ttu-id="2ea53-109">Allt kanske inte är meningen första gången, men efter en lite praktisk erfarenhet börjar du med att ha de här momenten med "glöd lampa".</span><span class="sxs-lookup"><span data-stu-id="2ea53-109">Not everything may make sense initially, but after a little hands-on experience you'll start to have those "light bulb" moments.</span></span> <span data-ttu-id="2ea53-110">Aha!</span><span class="sxs-lookup"><span data-stu-id="2ea53-110">"Aha!</span></span> <span data-ttu-id="2ea53-111">Så det är vad boken pratar om. "</span><span class="sxs-lookup"><span data-stu-id="2ea53-111">So that's what the book was talking about."</span></span>

<span data-ttu-id="2ea53-112">Se till att testa exemplen på din dator för att få lite praktisk erfarenhet.</span><span class="sxs-lookup"><span data-stu-id="2ea53-112">Be sure to try the examples on your computer to gain some of that hands-on experience.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ea53-113">Krav</span><span class="sxs-lookup"><span data-stu-id="2ea53-113">Requirements</span></span>

<span data-ttu-id="2ea53-114">Den Active Directory PowerShell-modulen krävs av några av exemplen som visas i det här kapitlet.</span><span class="sxs-lookup"><span data-stu-id="2ea53-114">The Active Directory PowerShell module is required by some of the examples shown in this chapter.</span></span>
<span data-ttu-id="2ea53-115">Modulen är en del av verktyg för fjärrserveradministration (RSAT) för Windows.</span><span class="sxs-lookup"><span data-stu-id="2ea53-115">The module is part of the Remote Server Administration Tools (RSAT) for Windows.</span></span> <span data-ttu-id="2ea53-116">För 1809 (eller högre) version av Windows installeras RSAT-verktyg som en Windows-funktion.</span><span class="sxs-lookup"><span data-stu-id="2ea53-116">For the 1809 (or higher) build of Windows, the RSAT tools are installed as a Windows feature.</span></span>

- <span data-ttu-id="2ea53-117">Information om hur du installerar RSAT-verktyg finns i [Windows Management-moduler][].</span><span class="sxs-lookup"><span data-stu-id="2ea53-117">For information about installing the RSAT tools, see [Windows Management modules][].</span></span>
- <span data-ttu-id="2ea53-118">För äldre versioner av Windows, se [RSAT för Windows][].</span><span class="sxs-lookup"><span data-stu-id="2ea53-118">For older versions of Windows, see [RSAT for Windows][].</span></span>

## <a name="get-member"></a><span data-ttu-id="2ea53-119">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="2ea53-119">Get-Member</span></span>

<span data-ttu-id="2ea53-120">`Get-Member`hjälper dig att identifiera vilka objekt, egenskaper och metoder som är tillgängliga för kommandon.</span><span class="sxs-lookup"><span data-stu-id="2ea53-120">`Get-Member` helps you discover what objects, properties, and methods are available for commands.</span></span>
<span data-ttu-id="2ea53-121">Alla kommandon som producerar objektbaserade utdata kan skickas till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-121">Any command that produces object-based output can be piped to `Get-Member`.</span></span> <span data-ttu-id="2ea53-122">En egenskap är en egenskap för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="2ea53-122">A property is a characteristic about an item.</span></span> <span data-ttu-id="2ea53-123">Driv rutins licensen har en egenskap som kallas ögon färg och de vanligaste värdena för den egenskapen är blå och brun.</span><span class="sxs-lookup"><span data-stu-id="2ea53-123">Your drivers license has a property called eye color and the most common values for that property are blue and brown.</span></span> <span data-ttu-id="2ea53-124">En metod är en åtgärd som kan vidtas för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="2ea53-124">A method is an action that can be taken on an item.</span></span> <span data-ttu-id="2ea53-125">I och med licens exempel för driv rutiner är en av metoderna "återkalla" eftersom motor fordonets avdelning kan återkalla driv rutins licensen.</span><span class="sxs-lookup"><span data-stu-id="2ea53-125">In staying with the drivers license example, one of the methods is "Revoke" because the department of motor vehicles can revoke your drivers license.</span></span>

### <a name="properties"></a><span data-ttu-id="2ea53-126">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="2ea53-126">Properties</span></span>

<span data-ttu-id="2ea53-127">I följande exempel hämtar jag information om Windows tids tjänst som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="2ea53-127">In the following example, I'll retrieve information about the Windows Time service running on my computer.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="2ea53-128">**Status**, **namn**och **DisplayName** är exempel på egenskaper som visas i den föregående uppsättningen med resultat.</span><span class="sxs-lookup"><span data-stu-id="2ea53-128">**Status**, **Name**, and **DisplayName** are examples of properties as shown in the previous set of results.</span></span> <span data-ttu-id="2ea53-129">Värdet för egenskapen **status** är `Running` , värdet för egenskapen **Name** är `w32time` och värdet för **DisplayName** är `Windows Time` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-129">The value for the **Status** property is `Running`, the value for the **Name** property is `w32time`, and the value for **DisplayName** is `Windows Time`.</span></span>

<span data-ttu-id="2ea53-130">Nu ska jag skicka en pipe till samma kommando för att `Get-Member` :</span><span class="sxs-lookup"><span data-stu-id="2ea53-130">Now I'll pipe that same command to `Get-Member`:</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="2ea53-131">Den första raden i resultatet i föregående exempel innehåller en viktig information.</span><span class="sxs-lookup"><span data-stu-id="2ea53-131">The first line of the results in the previous example contains one piece of very important information.</span></span> <span data-ttu-id="2ea53-132">**TypeName** anger vilken typ av objekt som returnerades.</span><span class="sxs-lookup"><span data-stu-id="2ea53-132">**TypeName** tells you what type of object was returned.</span></span> <span data-ttu-id="2ea53-133">I det här exemplet returnerades ett **system. ServiceProcess. ServiceController** -objekt.</span><span class="sxs-lookup"><span data-stu-id="2ea53-133">In this example, a **System.ServiceProcess.ServiceController** object was returned.</span></span> <span data-ttu-id="2ea53-134">Detta är ofta förkortat som delen av **TypeName** precis efter den senaste perioden. **ServiceController** i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="2ea53-134">This is often abbreviated as the portion of the **TypeName** just after the last period; **ServiceController** in this example.</span></span>

<span data-ttu-id="2ea53-135">När du vet vilken typ av objekt ett kommando genererar kan du använda den här informationen för att hitta kommandon som accepterar den typen av objekt som indata.</span><span class="sxs-lookup"><span data-stu-id="2ea53-135">Once you know what type of object a command produces, you can use this information to find commands that accept that type of object as input.</span></span>

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

<span data-ttu-id="2ea53-136">Alla dessa kommandon har en parameter som godkänner en **ServiceController** objekt typ efter pipeline, parameter Indatatyp eller både och.</span><span class="sxs-lookup"><span data-stu-id="2ea53-136">All of those commands have a parameter that accepts a **ServiceController** object type by pipeline, parameter input, or both.</span></span>

<span data-ttu-id="2ea53-137">Observera att det finns fler egenskaper än vad som visas som standard.</span><span class="sxs-lookup"><span data-stu-id="2ea53-137">Notice that there are more properties than are displayed by default.</span></span> <span data-ttu-id="2ea53-138">Även om dessa ytterligare egenskaper inte visas som standard kan de väljas från pipelinen genom att skicka kommandot till `Select-Object` cmdlet: en och använda **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="2ea53-138">Although these additional properties aren't displayed by default, they can be selected from the pipeline by piping the command to the `Select-Object` cmdlet and using the **Property** parameter.</span></span> <span data-ttu-id="2ea53-139">I följande exempel väljs alla egenskaper genom att skicka resultatet från `Get-Service` till `Select-Object` och ange `*` jokertecknet som värde för **egenskapen Property** .</span><span class="sxs-lookup"><span data-stu-id="2ea53-139">The following example selects all of the properties by piping the results of `Get-Service` to `Select-Object` and specifying the `*` wildcard character as the value for the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="2ea53-140">Du kan också välja vissa egenskaper med hjälp av en kommaavgränsad lista för värdet för **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="2ea53-140">Specific properties can also be selected using a comma-separated list for the value of the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

<span data-ttu-id="2ea53-141">Som standard returneras fyra egenskaper i en tabell och fem eller fler returneras i en lista.</span><span class="sxs-lookup"><span data-stu-id="2ea53-141">By default, four properties are returned in a table and five or more are returned in a list.</span></span> <span data-ttu-id="2ea53-142">Vissa kommandon använder anpassad formatering för att åsidosätta hur många egenskaper som visas som standard i en tabell.</span><span class="sxs-lookup"><span data-stu-id="2ea53-142">Some commands use custom formatting to override how many properties are displayed by default in a table.</span></span>
<span data-ttu-id="2ea53-143">Det finns flera `Format-*` cmdletar som kan användas för att åsidosätta dessa standardvärden manuellt.</span><span class="sxs-lookup"><span data-stu-id="2ea53-143">There are several `Format-*` cmdlets that can be used to manually override these defaults.</span></span> <span data-ttu-id="2ea53-144">De vanligaste är `Format-Table` och `Format-List` , som båda kommer att omfattas av ett kommande kapitel.</span><span class="sxs-lookup"><span data-stu-id="2ea53-144">The most common ones are `Format-Table` and `Format-List`, both of which will be covered in an upcoming chapter.</span></span>

<span data-ttu-id="2ea53-145">Jokertecken kan användas när du anger egenskaps namnen med `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-145">Wildcard characters can be used when specifying the property names with `Select-Object`.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="2ea53-146">I föregående exempel `Can*` användes som ett av värdena för **egenskaps** parametern för att returnera alla egenskaper som börjar med `Can` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-146">In the previous example, `Can*` was used as one of the values for the **Property** parameter to return all the properties that start with `Can`.</span></span> <span data-ttu-id="2ea53-147">Dessa inkluderar **CanPauseAndContinue**, **CanShutdown**och **CanStop**.</span><span class="sxs-lookup"><span data-stu-id="2ea53-147">These include **CanPauseAndContinue**, **CanShutdown**, and **CanStop**.</span></span>

### <a name="methods"></a><span data-ttu-id="2ea53-148">Metoder</span><span class="sxs-lookup"><span data-stu-id="2ea53-148">Methods</span></span>

<span data-ttu-id="2ea53-149">Metoder är en åtgärd som kan vidtas.</span><span class="sxs-lookup"><span data-stu-id="2ea53-149">Methods are an action that can be taken.</span></span> <span data-ttu-id="2ea53-150">Använd parametern **MemberType** för att begränsa resultaten av för `Get-Member` att bara Visa metoderna för `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-150">Use the **MemberType** parameter to narrow down the results of `Get-Member` to only show the methods for `Get-Service`.</span></span>

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

<span data-ttu-id="2ea53-151">Som du kan se finns det många sätt.</span><span class="sxs-lookup"><span data-stu-id="2ea53-151">As you can see, there are many methods.</span></span> <span data-ttu-id="2ea53-152">**Stop** -metoden kan användas för att stoppa en Windows-tjänst.</span><span class="sxs-lookup"><span data-stu-id="2ea53-152">The **Stop** method can be used to stop a Windows service.</span></span>

```powershell
(Get-Service -Name w32time).Stop()
```

<span data-ttu-id="2ea53-153">Nu kan du kontrol lera att Windows tids tjänst verkligen har stoppats.</span><span class="sxs-lookup"><span data-stu-id="2ea53-153">Now to verify the Windows time service has indeed been stopped.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

<span data-ttu-id="2ea53-154">Jag har sällan hittat mig med metoder, men de är något du behöver känna till.</span><span class="sxs-lookup"><span data-stu-id="2ea53-154">I rarely find myself using methods, but they're something you need to be aware of.</span></span> <span data-ttu-id="2ea53-155">Det finns tider som du kommer att komma över ett `Get-*` kommando utan motsvarande kommando för att ändra objektet.</span><span class="sxs-lookup"><span data-stu-id="2ea53-155">There are times that you'll come across a `Get-*` command without a corresponding command to modify that item.</span></span>
<span data-ttu-id="2ea53-156">Ofta kan en metod användas för att utföra en åtgärd som ändrar den.</span><span class="sxs-lookup"><span data-stu-id="2ea53-156">Often, a method can be used to perform an action that modifies it.</span></span> <span data-ttu-id="2ea53-157">`Get-SqlAgentJob`Cmdleten i SQLServer PowerShell-modulen är ett användbart exempel på detta.</span><span class="sxs-lookup"><span data-stu-id="2ea53-157">The `Get-SqlAgentJob` cmdlet in the SqlServer PowerShell module is a good example of this.</span></span> <span data-ttu-id="2ea53-158">Modulen installeras som en del av [SQL Server Management Studio (Smss)][SMSS].</span><span class="sxs-lookup"><span data-stu-id="2ea53-158">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="2ea53-159">`Set-*`Det finns ingen motsvarande cmdlet, men metoden kan användas för att slutföra samma uppgift.</span><span class="sxs-lookup"><span data-stu-id="2ea53-159">No corresponding `Set-*` cmdlet exists, but a method can be used to complete the same task.</span></span>

<span data-ttu-id="2ea53-160">Ett annat skäl att vara medveten om metoderna är att många nybörjare antar destruktiva ändringar kan inte utföras med `Get-*` kommandon.</span><span class="sxs-lookup"><span data-stu-id="2ea53-160">Another reason to be aware of methods is that many beginners assume destructive changes can't be made with `Get-*` commands.</span></span> <span data-ttu-id="2ea53-161">Men de kan orsaka allvarliga problem om de används på ett felaktigt sätt.</span><span class="sxs-lookup"><span data-stu-id="2ea53-161">But they indeed can cause serious problems if used inappropriately.</span></span>

<span data-ttu-id="2ea53-162">Ett bättre alternativ är att använda en cmdlet för att utföra åtgärden om en sådan finns.</span><span class="sxs-lookup"><span data-stu-id="2ea53-162">A better option is to use a cmdlet to perform the action if one exists.</span></span> <span data-ttu-id="2ea53-163">Gå vidare och starta Windows tids tjänst, förutom den här gången använder du cmdleten för att starta tjänster.</span><span class="sxs-lookup"><span data-stu-id="2ea53-163">Go ahead and start the Windows Time service, except this time use the cmdlet for starting services.</span></span>

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="2ea53-164">Som standard `Start-Service` returnerar inte några resultat precis som start metoden för `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-164">By default, `Start-Service` doesn't return any results just like the start method of `Get-Service`.</span></span>
<span data-ttu-id="2ea53-165">Men en av fördelarna med att använda en cmdlet är att många gånger cmdleten erbjuder ytterligare funktioner som inte är tillgängliga med en-metod.</span><span class="sxs-lookup"><span data-stu-id="2ea53-165">But one of the benefits of using a cmdlet is that many times the cmdlet offers additional functionality that isn't available with a method.</span></span> <span data-ttu-id="2ea53-166">I det föregående exemplet användes parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="2ea53-166">In the previous example, the **PassThru** parameter was used.</span></span> <span data-ttu-id="2ea53-167">Detta orsakar en cmdlet som normalt inte producerar utdata för att skapa utdata.</span><span class="sxs-lookup"><span data-stu-id="2ea53-167">This causes a cmdlet that doesn't normally produce output, to produce output.</span></span>

<span data-ttu-id="2ea53-168">Var försiktig med antaganden om utdata för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ea53-168">Be careful with assumptions about the output of a cmdlet.</span></span> <span data-ttu-id="2ea53-169">Vi vet vad som händer när du antar saker.</span><span class="sxs-lookup"><span data-stu-id="2ea53-169">We all know what happens when you assume things.</span></span> <span data-ttu-id="2ea53-170">Jag hämtar information om PowerShell-processen som körs på min Windows 10 labb miljö dator.</span><span class="sxs-lookup"><span data-stu-id="2ea53-170">I'll retrieve information about the PowerShell process running on my Windows 10 lab environment computer.</span></span>

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

<span data-ttu-id="2ea53-171">Nu ska jag skicka vidare samma kommando för att hämta medlem:</span><span class="sxs-lookup"><span data-stu-id="2ea53-171">Now I'll pipe that same command to Get-Member:</span></span>

```powershell
Get-Process -Name PowerShell | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
```

<span data-ttu-id="2ea53-172">Observera att det finns fler egenskaper än vad som visas som standard.</span><span class="sxs-lookup"><span data-stu-id="2ea53-172">Notice that there are more properties listed than are displayed by default.</span></span> <span data-ttu-id="2ea53-173">Ett antal av de standard egenskaper som visas visas inte som egenskaper när du visar resultatet av `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-173">A number of the default properties displayed don't show up as properties when viewing the results of `Get-Member`.</span></span> <span data-ttu-id="2ea53-174">Detta beror på att många av de värden som visas, till exempel,, `NPM(K)` `PM(K)` `WS(K)` och `CPU(s)` , är beräknade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2ea53-174">This is because many of the displayed values, such as `NPM(K)`, `PM(K)`, `WS(K)`, and `CPU(s)`, are calculated properties.</span></span> <span data-ttu-id="2ea53-175">Om du vill fastställa de faktiska egenskaps namnen måste kommandot vara skickas `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-175">To determine the actual property names, the command must be piped to `Get-Member`.</span></span>

<span data-ttu-id="2ea53-176">Om ett kommando inte producerar utdata kan det inte skickas till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-176">If a command does not produce output, it can't be piped to `Get-Member`.</span></span> <span data-ttu-id="2ea53-177">Eftersom `Start-Service` inte genererar några utdata som standard genererar den ett fel när du försöker skicka vidare den till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-177">Since `Start-Service` doesn't produce any output by default, it generates an error when you try to pipe it to `Get-Member`.</span></span>

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

<span data-ttu-id="2ea53-178">Parametern **Passthru** kan anges med `Start-Service` cmdleten gör att den genererar utdata, som sedan skickas till `Get-Member` utan fel.</span><span class="sxs-lookup"><span data-stu-id="2ea53-178">The **PassThru** parameter can be specified with the `Start-Service` cmdlet make it produce output, which is then piped to `Get-Member` without error.</span></span>

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="2ea53-179">För att skickas ska kunna köras `Get-Member` måste ett kommando skapa objektbaserade utdata.</span><span class="sxs-lookup"><span data-stu-id="2ea53-179">To be piped to `Get-Member`, a command must produce object-based output.</span></span>

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

<span data-ttu-id="2ea53-180">`Out-Host`skriver direkt till PowerShell-värden, men genererar inte objektbaserade utdata för pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2ea53-180">`Out-Host` writes directly to the PowerShell host, but it doesn't produce object-based output for the pipeline.</span></span> <span data-ttu-id="2ea53-181">Så det går inte att skickas till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="2ea53-181">So it can't be piped to `Get-Member`.</span></span>

## <a name="active-directory"></a><span data-ttu-id="2ea53-182">Active Directory</span><span class="sxs-lookup"><span data-stu-id="2ea53-182">Active Directory</span></span>

> [!NOTE]
> <span data-ttu-id="2ea53-183">Det verktyg för fjärrserveradministration som anges i avsnittet krav i det här kapitlet krävs för att slutföra det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="2ea53-183">The Remote Server Administration Tools listed in the requirements section of this chapter are required to complete this section.</span></span> <span data-ttu-id="2ea53-184">Som vi nämnt i introduktionen till den här boken måste din dator med Windows 10-labb miljö vara medlem i labb miljö domänen.</span><span class="sxs-lookup"><span data-stu-id="2ea53-184">Also, as mentioned in the introduction to this book, your Windows 10 lab environment computer must be a member of the lab environment domain.</span></span>

<span data-ttu-id="2ea53-185">Använd `Get-Command` parametern **module** för att avgöra vilka kommandon som lades till som en del av ActiveDirectory PowerShell-modulen när verktyg för fjärrserveradministration installerades.</span><span class="sxs-lookup"><span data-stu-id="2ea53-185">Use `Get-Command` with the **Module** parameter to determine what commands were added as part of the ActiveDirectory PowerShell module when the remote server administration tools were installed.</span></span>

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

<span data-ttu-id="2ea53-186">Totalt 147 kommandon har lagts till som en del av ActiveDirectory PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="2ea53-186">A total of 147 commands were added as part of the ActiveDirectory PowerShell module.</span></span> <span data-ttu-id="2ea53-187">Vissa kommandon för de här kommandona returnerar endast en del av de tillgängliga egenskaperna som standard.</span><span class="sxs-lookup"><span data-stu-id="2ea53-187">Some commands of these commands only return a portion of the available properties by default.</span></span>

<span data-ttu-id="2ea53-188">Har du ansett något som skiljer sig på namnen på kommandona i den här modulen?</span><span class="sxs-lookup"><span data-stu-id="2ea53-188">Did you notice anything different about the names of the commands in this module?</span></span> <span data-ttu-id="2ea53-189">Substantiv delen av kommandona har ett AD-prefix.</span><span class="sxs-lookup"><span data-stu-id="2ea53-189">The noun portion of the commands has an AD prefix.</span></span> <span data-ttu-id="2ea53-190">Detta är vanligt för att se kommandon i de flesta moduler.</span><span class="sxs-lookup"><span data-stu-id="2ea53-190">This is common to see on the commands of most modules.</span></span> <span data-ttu-id="2ea53-191">Prefixet är utformat för att hjälpa till att förhindra namngivnings konflikter.</span><span class="sxs-lookup"><span data-stu-id="2ea53-191">The prefix is designed to help prevent naming conflicts.</span></span>

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

<span data-ttu-id="2ea53-192">Även om du bara vaguely bekant med Active Directory är du förmodligen medveten om att ett användar konto har fler egenskaper än vad som visas i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="2ea53-192">Even if you're only vaguely familiar with Active Directory, you're probably aware that a user account has more properties than are shown in this example.</span></span>

<span data-ttu-id="2ea53-193">`Get-ADUser`Cmdleten har en **egenskaps** parameter som används för att ange de ytterligare egenskaper (som inte är standard) som du vill returnera.</span><span class="sxs-lookup"><span data-stu-id="2ea53-193">The `Get-ADUser` cmdlet has a **Properties** parameter that is used to specify the additional (non-default) properties you want to return.</span></span> <span data-ttu-id="2ea53-194">Att ange `*` jokertecknet returnerar alla.</span><span class="sxs-lookup"><span data-stu-id="2ea53-194">Specifying the `*` wildcard character returns all of them.</span></span>

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

<span data-ttu-id="2ea53-195">Nu ser du mer som det.</span><span class="sxs-lookup"><span data-stu-id="2ea53-195">Now that looks more like it.</span></span>

<span data-ttu-id="2ea53-196">Kan du tänka på en orsak till att egenskaperna för ett Active Directory användar konto är så begränsade som standard?</span><span class="sxs-lookup"><span data-stu-id="2ea53-196">Can you think of a reason why the properties of an Active Directory user account would be so limited by default?</span></span> <span data-ttu-id="2ea53-197">Tänk dig att du har returnerat varje egenskap för varje användar konto i produktions Active Directorys miljön.</span><span class="sxs-lookup"><span data-stu-id="2ea53-197">Imagine if you returned every property for every user account in your production Active Directory environment.</span></span> <span data-ttu-id="2ea53-198">Tänk på den prestanda försämring som du kan orsaka, inte bara till domän kontrol Lanterna själva, utan även i nätverket.</span><span class="sxs-lookup"><span data-stu-id="2ea53-198">Think of the performance degradation that you could cause, not only to the domain controllers themselves, but also to your network.</span></span> <span data-ttu-id="2ea53-199">Det är Doubtful att du verkligen behöver alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2ea53-199">It's doubtful that you'll actually need every property anyway.</span></span> <span data-ttu-id="2ea53-200">Att returnera alla egenskaper för ett enskilt användar konto är perfekt acceptabelt när du försöker fastställa vilka egenskaper som finns.</span><span class="sxs-lookup"><span data-stu-id="2ea53-200">Returning all of the properties for a single user account is perfectly acceptable when you're trying to determine what properties exist.</span></span>

<span data-ttu-id="2ea53-201">Det är inte ovanligt att köra ett kommando flera gånger vid prototypering av det.</span><span class="sxs-lookup"><span data-stu-id="2ea53-201">It's not uncommon to run a command many times when prototyping it.</span></span> <span data-ttu-id="2ea53-202">Om du kommer att utföra en stor mängd frågor kan du fråga den en gång och lagra resultatet i en variabel.</span><span class="sxs-lookup"><span data-stu-id="2ea53-202">If you're going to perform some huge query, query it once and store the results in a variable.</span></span> <span data-ttu-id="2ea53-203">Arbeta sedan med innehållet i variabeln i stället för upprepade gånger med en viss dyr fråga.</span><span class="sxs-lookup"><span data-stu-id="2ea53-203">Then work with the contents of the variable instead of repeatedly using some expensive query.</span></span>

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

<span data-ttu-id="2ea53-204">Använd innehållet i `$Users` variabeln i stället för att köra föregående kommando flera gånger.</span><span class="sxs-lookup"><span data-stu-id="2ea53-204">Use the contents of the `$Users` variable instead of running the previous command numerous times.</span></span>
<span data-ttu-id="2ea53-205">Tänk på att innehållet i variabeln inte uppdateras när ändringar görs i den användaren i Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2ea53-205">Keep in mind that the contents of the variable aren't updated when changes are made to that user in Active Directory.</span></span>

<span data-ttu-id="2ea53-206">Du kan skicka en pipe `$Users` till variabeln för `Get-Member` att identifiera tillgängliga egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2ea53-206">You could pipe the `$Users` variable to `Get-Member` to discover the available properties.</span></span>

```powershell
$Users | Get-Member
```

<span data-ttu-id="2ea53-207">Välj sedan de enskilda egenskaperna genom `$Users` att `Select-Object` skicka vidare till, allt utan att behöva fråga Active Directory mer än en gång.</span><span class="sxs-lookup"><span data-stu-id="2ea53-207">Then select the individual properties by piping `$Users` to `Select-Object`, all without ever having to query Active Directory more than one time.</span></span>

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

<span data-ttu-id="2ea53-208">Om du kommer att fråga Active Directory mer än en gång använder du parametern **Properties** för att ange egenskaper som inte är standard.</span><span class="sxs-lookup"><span data-stu-id="2ea53-208">If you are going to query Active Directory more than once, use the **Properties** parameter to specify any non-default properties you want.</span></span>

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a><span data-ttu-id="2ea53-209">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="2ea53-209">Summary</span></span>

<span data-ttu-id="2ea53-210">I det här kapitlet har du lärt dig hur du avgör vilken typ av objekt ett kommando skapar, hur du avgör vilka egenskaper och metoder som är tillgängliga för ett kommando och hur du arbetar med kommandon som begränsar de egenskaper som returneras som standard.</span><span class="sxs-lookup"><span data-stu-id="2ea53-210">In this chapter, you've learned how to determine what type of object a command produces, how to determine what properties and methods are available for a command, and how to work with commands that limit the properties that are returned by default.</span></span>

## <a name="review"></a><span data-ttu-id="2ea53-211">Granska</span><span class="sxs-lookup"><span data-stu-id="2ea53-211">Review</span></span>

1. <span data-ttu-id="2ea53-212">Vilken typ av objekt `Get-Process` skapar cmdleten?</span><span class="sxs-lookup"><span data-stu-id="2ea53-212">What type of object does the `Get-Process` cmdlet produce?</span></span>
1. <span data-ttu-id="2ea53-213">Hur tar du reda på vilka egenskaper som är tillgängliga för ett kommando?</span><span class="sxs-lookup"><span data-stu-id="2ea53-213">How do you determine what the available properties are for a command?</span></span>
1. <span data-ttu-id="2ea53-214">Om det finns ett kommando för att hämta något men inte för att ange samma sak, vad ska du söka efter?</span><span class="sxs-lookup"><span data-stu-id="2ea53-214">If a command exists for getting something but not for setting the same thing, what should you check for?</span></span>
1. <span data-ttu-id="2ea53-215">Hur kan vissa kommandon som inte producerar utdata som standard skapas för att skapa utdata?</span><span class="sxs-lookup"><span data-stu-id="2ea53-215">How can certain commands that don't produce output by default be made to produce output?</span></span>
1. <span data-ttu-id="2ea53-216">Om du kommer att arbeta med resultatet av ett kommando som producerar enorma mängder utdata, vad bör du göra?</span><span class="sxs-lookup"><span data-stu-id="2ea53-216">If you're going to be working with the results of a command that produces an enormous amount of output, what should you consider doing?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="2ea53-217">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="2ea53-217">Recommended Reading</span></span>

- <span data-ttu-id="2ea53-218">[Hämta medlem][]</span><span class="sxs-lookup"><span data-stu-id="2ea53-218">[Get-Member][]</span></span>
- <span data-ttu-id="2ea53-219">[Visa objektstrukturen (Get-Member)][]</span><span class="sxs-lookup"><span data-stu-id="2ea53-219">[Viewing Object Structure (Get-Member)][]</span></span>
- <span data-ttu-id="2ea53-220">[about_Objects][]</span><span class="sxs-lookup"><span data-stu-id="2ea53-220">[about_Objects][]</span></span>
- <span data-ttu-id="2ea53-221">[about_Properties][]</span><span class="sxs-lookup"><span data-stu-id="2ea53-221">[about_Properties][]</span></span>
- <span data-ttu-id="2ea53-222">[about_Methods][]</span><span class="sxs-lookup"><span data-stu-id="2ea53-222">[about_Methods][]</span></span>
- <span data-ttu-id="2ea53-223">[Har du inte någon PowerShell-cmdlet för att starta eller stoppa något? Glöm inte att söka efter metoder på Get-cmdletar][use-methods]</span><span class="sxs-lookup"><span data-stu-id="2ea53-223">[No PowerShell Cmdlet to Start or Stop Something? Don’t Forget to Check for Methods on the Get Cmdlets][use-methods]</span></span>

<!-- link references -->
[RSAT för Windows]: https://support.microsoft.com/help/2693643
[RSAT for Windows]: https://support.microsoft.com/help/2693643
[Windows Management-moduler]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Windows Management modules]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Hämta medlem]: /powershell/module/microsoft.powershell.utility/get-member
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[Visa objektstrukturen (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[Viewing Object Structure (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
