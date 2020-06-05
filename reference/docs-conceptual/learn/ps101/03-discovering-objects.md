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
# <a name="chapter-3---discovering-objects-properties-and-methods"></a>Kapitel 3 – identifiera objekt, egenskaper och metoder

Min första introduktion till datorer var en Commodore 64, men min första moderna dator var 286 12 MHz IBM-klon med 1 megabyte minne, en 40-megabyte-hårddisk och en 5-1/4-tums diskett enhet med CGA-övervakaren som kör Microsoft DOS 3,3.

Många IT-proffs, precis som mig, är inte Stranger till kommando raden, men när objektets, egenskapernas och metodernas ämne hämtas, får de Deer i Headlights look och säger "Jag är inte utvecklare". Gissa vad? Du behöver inte vara utvecklare för att lyckas med PowerShell. Få inte bogged nedåt i terminologin. Allt kanske inte är meningen första gången, men efter en lite praktisk erfarenhet börjar du med att ha de här momenten med "glöd lampa". Aha! Så det är vad boken pratar om. "

Se till att testa exemplen på din dator för att få lite praktisk erfarenhet.

## <a name="requirements"></a>Krav

Den Active Directory PowerShell-modulen krävs av några av exemplen som visas i det här kapitlet.
Modulen är en del av verktyg för fjärrserveradministration (RSAT) för Windows. För 1809 (eller högre) version av Windows installeras RSAT-verktyg som en Windows-funktion.

- Information om hur du installerar RSAT-verktyg finns i [Windows Management-moduler][].
- För äldre versioner av Windows, se [RSAT för Windows][].

## <a name="get-member"></a>Hämta medlem

`Get-Member`hjälper dig att identifiera vilka objekt, egenskaper och metoder som är tillgängliga för kommandon.
Alla kommandon som producerar objektbaserade utdata kan skickas till `Get-Member` . En egenskap är en egenskap för ett objekt. Driv rutins licensen har en egenskap som kallas ögon färg och de vanligaste värdena för den egenskapen är blå och brun. En metod är en åtgärd som kan vidtas för ett objekt. I och med licens exempel för driv rutiner är en av metoderna "återkalla" eftersom motor fordonets avdelning kan återkalla driv rutins licensen.

### <a name="properties"></a>Egenskaper

I följande exempel hämtar jag information om Windows tids tjänst som körs på datorn.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

**Status**, **namn**och **DisplayName** är exempel på egenskaper som visas i den föregående uppsättningen med resultat. Värdet för egenskapen **status** är `Running` , värdet för egenskapen **Name** är `w32time` och värdet för **DisplayName** är `Windows Time` .

Nu ska jag skicka en pipe till samma kommando för att `Get-Member` :

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

Den första raden i resultatet i föregående exempel innehåller en viktig information. **TypeName** anger vilken typ av objekt som returnerades. I det här exemplet returnerades ett **system. ServiceProcess. ServiceController** -objekt. Detta är ofta förkortat som delen av **TypeName** precis efter den senaste perioden. **ServiceController** i det här exemplet.

När du vet vilken typ av objekt ett kommando genererar kan du använda den här informationen för att hitta kommandon som accepterar den typen av objekt som indata.

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

Alla dessa kommandon har en parameter som godkänner en **ServiceController** objekt typ efter pipeline, parameter Indatatyp eller både och.

Observera att det finns fler egenskaper än vad som visas som standard. Även om dessa ytterligare egenskaper inte visas som standard kan de väljas från pipelinen genom att skicka kommandot till `Select-Object` cmdlet: en och använda **egenskaps** parametern. I följande exempel väljs alla egenskaper genom att skicka resultatet från `Get-Service` till `Select-Object` och ange `*` jokertecknet som värde för **egenskapen Property** .

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

Du kan också välja vissa egenskaper med hjälp av en kommaavgränsad lista för värdet för **egenskaps** parametern.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

Som standard returneras fyra egenskaper i en tabell och fem eller fler returneras i en lista. Vissa kommandon använder anpassad formatering för att åsidosätta hur många egenskaper som visas som standard i en tabell.
Det finns flera `Format-*` cmdletar som kan användas för att åsidosätta dessa standardvärden manuellt. De vanligaste är `Format-Table` och `Format-List` , som båda kommer att omfattas av ett kommande kapitel.

Jokertecken kan användas när du anger egenskaps namnen med `Select-Object` .

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

I föregående exempel `Can*` användes som ett av värdena för **egenskaps** parametern för att returnera alla egenskaper som börjar med `Can` . Dessa inkluderar **CanPauseAndContinue**, **CanShutdown**och **CanStop**.

### <a name="methods"></a>Metoder

Metoder är en åtgärd som kan vidtas. Använd parametern **MemberType** för att begränsa resultaten av för `Get-Member` att bara Visa metoderna för `Get-Service` .

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

Som du kan se finns det många sätt. **Stop** -metoden kan användas för att stoppa en Windows-tjänst.

```powershell
(Get-Service -Name w32time).Stop()
```

Nu kan du kontrol lera att Windows tids tjänst verkligen har stoppats.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

Jag har sällan hittat mig med metoder, men de är något du behöver känna till. Det finns tider som du kommer att komma över ett `Get-*` kommando utan motsvarande kommando för att ändra objektet.
Ofta kan en metod användas för att utföra en åtgärd som ändrar den. `Get-SqlAgentJob`Cmdleten i SQLServer PowerShell-modulen är ett användbart exempel på detta. Modulen installeras som en del av [SQL Server Management Studio (Smss)][SMSS]. `Set-*`Det finns ingen motsvarande cmdlet, men metoden kan användas för att slutföra samma uppgift.

Ett annat skäl att vara medveten om metoderna är att många nybörjare antar destruktiva ändringar kan inte utföras med `Get-*` kommandon. Men de kan orsaka allvarliga problem om de används på ett felaktigt sätt.

Ett bättre alternativ är att använda en cmdlet för att utföra åtgärden om en sådan finns. Gå vidare och starta Windows tids tjänst, förutom den här gången använder du cmdleten för att starta tjänster.

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Som standard `Start-Service` returnerar inte några resultat precis som start metoden för `Get-Service` .
Men en av fördelarna med att använda en cmdlet är att många gånger cmdleten erbjuder ytterligare funktioner som inte är tillgängliga med en-metod. I det föregående exemplet användes parametern **Passthru** . Detta orsakar en cmdlet som normalt inte producerar utdata för att skapa utdata.

Var försiktig med antaganden om utdata för en cmdlet. Vi vet vad som händer när du antar saker. Jag hämtar information om PowerShell-processen som körs på min Windows 10 labb miljö dator.

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

Nu ska jag skicka vidare samma kommando för att hämta medlem:

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

Observera att det finns fler egenskaper än vad som visas som standard. Ett antal av de standard egenskaper som visas visas inte som egenskaper när du visar resultatet av `Get-Member` . Detta beror på att många av de värden som visas, till exempel,, `NPM(K)` `PM(K)` `WS(K)` och `CPU(s)` , är beräknade egenskaper. Om du vill fastställa de faktiska egenskaps namnen måste kommandot vara skickas `Get-Member` .

Om ett kommando inte producerar utdata kan det inte skickas till `Get-Member` . Eftersom `Start-Service` inte genererar några utdata som standard genererar den ett fel när du försöker skicka vidare den till `Get-Member` .

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

Parametern **Passthru** kan anges med `Start-Service` cmdleten gör att den genererar utdata, som sedan skickas till `Get-Member` utan fel.

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

För att skickas ska kunna köras `Get-Member` måste ett kommando skapa objektbaserade utdata.

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

`Out-Host`skriver direkt till PowerShell-värden, men genererar inte objektbaserade utdata för pipelinen. Så det går inte att skickas till `Get-Member` .

## <a name="active-directory"></a>Active Directory

> [!NOTE]
> Det verktyg för fjärrserveradministration som anges i avsnittet krav i det här kapitlet krävs för att slutföra det här avsnittet. Som vi nämnt i introduktionen till den här boken måste din dator med Windows 10-labb miljö vara medlem i labb miljö domänen.

Använd `Get-Command` parametern **module** för att avgöra vilka kommandon som lades till som en del av ActiveDirectory PowerShell-modulen när verktyg för fjärrserveradministration installerades.

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

Totalt 147 kommandon har lagts till som en del av ActiveDirectory PowerShell-modulen. Vissa kommandon för de här kommandona returnerar endast en del av de tillgängliga egenskaperna som standard.

Har du ansett något som skiljer sig på namnen på kommandona i den här modulen? Substantiv delen av kommandona har ett AD-prefix. Detta är vanligt för att se kommandon i de flesta moduler. Prefixet är utformat för att hjälpa till att förhindra namngivnings konflikter.

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

Även om du bara vaguely bekant med Active Directory är du förmodligen medveten om att ett användar konto har fler egenskaper än vad som visas i det här exemplet.

`Get-ADUser`Cmdleten har en **egenskaps** parameter som används för att ange de ytterligare egenskaper (som inte är standard) som du vill returnera. Att ange `*` jokertecknet returnerar alla.

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

Nu ser du mer som det.

Kan du tänka på en orsak till att egenskaperna för ett Active Directory användar konto är så begränsade som standard? Tänk dig att du har returnerat varje egenskap för varje användar konto i produktions Active Directorys miljön. Tänk på den prestanda försämring som du kan orsaka, inte bara till domän kontrol Lanterna själva, utan även i nätverket. Det är Doubtful att du verkligen behöver alla egenskaper. Att returnera alla egenskaper för ett enskilt användar konto är perfekt acceptabelt när du försöker fastställa vilka egenskaper som finns.

Det är inte ovanligt att köra ett kommando flera gånger vid prototypering av det. Om du kommer att utföra en stor mängd frågor kan du fråga den en gång och lagra resultatet i en variabel. Arbeta sedan med innehållet i variabeln i stället för upprepade gånger med en viss dyr fråga.

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

Använd innehållet i `$Users` variabeln i stället för att köra föregående kommando flera gånger.
Tänk på att innehållet i variabeln inte uppdateras när ändringar görs i den användaren i Active Directory.

Du kan skicka en pipe `$Users` till variabeln för `Get-Member` att identifiera tillgängliga egenskaper.

```powershell
$Users | Get-Member
```

Välj sedan de enskilda egenskaperna genom `$Users` att `Select-Object` skicka vidare till, allt utan att behöva fråga Active Directory mer än en gång.

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

Om du kommer att fråga Active Directory mer än en gång använder du parametern **Properties** för att ange egenskaper som inte är standard.

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

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig hur du avgör vilken typ av objekt ett kommando skapar, hur du avgör vilka egenskaper och metoder som är tillgängliga för ett kommando och hur du arbetar med kommandon som begränsar de egenskaper som returneras som standard.

## <a name="review"></a>Granska

1. Vilken typ av objekt `Get-Process` skapar cmdleten?
1. Hur tar du reda på vilka egenskaper som är tillgängliga för ett kommando?
1. Om det finns ett kommando för att hämta något men inte för att ange samma sak, vad ska du söka efter?
1. Hur kan vissa kommandon som inte producerar utdata som standard skapas för att skapa utdata?
1. Om du kommer att arbeta med resultatet av ett kommando som producerar enorma mängder utdata, vad bör du göra?

## <a name="recommended-reading"></a>Rekommenderad läsning

- [Hämta medlem][]
- [Visa objektstrukturen (Get-Member)][]
- [about_Objects][]
- [about_Properties][]
- [about_Methods][]
- [Har du inte någon PowerShell-cmdlet för att starta eller stoppa något? Glöm inte att söka efter metoder på Get-cmdletar][use-methods]

<!-- link references -->
[RSAT för Windows]: https://support.microsoft.com/help/2693643
[Windows Management-moduler]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Hämta medlem]: /powershell/module/microsoft.powershell.utility/get-member
[Visa objektstrukturen (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
