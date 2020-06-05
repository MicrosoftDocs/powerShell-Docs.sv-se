---
title: PowerShell-fjärranvändning
description: Det finns många olika sätt att köra kommandon mot fjärrdatorer i PowerShell.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ee83af41b53b254dd3dd993931333edac2f44f5a
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436465"
---
# <a name="chapter-8---powershell-remoting"></a>Kapitel 8 – PowerShell-fjärrkommunikation

PowerShell har många olika sätt att köra kommandon mot fjärrdatorer. I det sista kapitlet såg du hur du fjärrfrågar WMI med CIM-cmdletarna. PowerShell innehåller också flera cmdletar som har en inbyggd **computername** -parameter.

Som du ser i följande exempel, `Get-Command` kan användas med parametern **ParameterName** för att avgöra vilka kommandon som har en **computername** -parameter.

```powershell
Get-Command -ParameterName ComputerName
```

```Output
CommandType Name                        Version Source
----------- ----                        ------- ------
Cmdlet      Connect-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Connect-WSMan               7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Disconnect-WSMan            7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Enter-PSSession             7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-CimAssociatedInstance   7.0.0.0 CimCmdlets
Cmdlet      Get-CimClass                7.0.0.0 CimCmdlets
Cmdlet      Get-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Get-CimSession              7.0.0.0 CimCmdlets
Cmdlet      Get-Counter                 7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-HotFix                  7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Get-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-WinEvent                7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Invoke-CimMethod            7.0.0.0 CimCmdlets
Cmdlet      Invoke-Command              7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Invoke-WSManAction          7.0.0.0 Microsoft.WSMan.Management
Cmdlet      New-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      New-CimSession              7.0.0.0 CimCmdlets
Cmdlet      New-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      New-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Receive-Job                 7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Receive-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Register-CimIndicationEvent 7.0.0.0 CimCmdlets
Cmdlet      Remove-CimInstance          7.0.0.0 CimCmdlets
Cmdlet      Remove-CimSession           7.0.0.0 CimCmdlets
Cmdlet      Remove-PSSession            7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Remove-WSManInstance        7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Rename-Computer             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Restart-Computer            7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Send-MailMessage            7.0.0.0 Microsoft.PowerShell.Utility
Cmdlet      Set-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Set-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Stop-Computer               7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-Connection             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-WSMan                  7.0.0.0 Microsoft.WSMan.Management
```

Kommandon som `Get-Process` och `Get-Hotfix` har en **computername** -parameter. Detta är inte den långsiktiga riktningen som Microsoft är rubrik för att köra kommandon mot fjärrdatorer. Även om du hittar ett kommando som har en **computername** -parameter, är det möjligt att du behöver ange alternativa autentiseringsuppgifter och att den inte har någon **Credential** -parameter. Om du har valt att köra PowerShell från ett förhöjt konto kan en brand vägg mellan dig och fjärrdatorn blockera begäran.

Om du vill använda PowerShell-fjärrkommandon som visas i det här kapitlet måste PowerShell-fjärrkommunikation vara aktiverat på fjärrdatorn. Använd `Enable-PSRemoting` cmdleten för att aktivera PowerShell-fjärrkommunikation.

```powershell
Enable-PSRemoting
```

```Output
WinRM has been updated to receive requests.
WinRM service type changed successfully.
WinRM service started.

WinRM has been updated for remote management.
WinRM firewall exception enabled.
```

## <a name="one-to-one-remoting"></a>En-till-en-fjärrkommunikation

Om du vill att fjärrsessionen ska vara interaktiv, är en-till-en-fjärr kommunikation vad du vill ha.
Den här typen av fjärr kommunikation tillhandahålls via `Enter-PSSession` cmdleten.

I det sista kapitlet sparade jag autentiseringsuppgifterna för domän administratören i en variabel med namnet `$Cred` . Om du inte redan har gjort det kan du gå vidare och spara dina autentiseringsuppgifter för domän administratören i `$Cred` variabeln.

På så sätt kan du ange autentiseringsuppgifterna en gång och använda dem på per kommando så länge den aktuella PowerShell-sessionen är aktiv.

```powershell
$Cred = Get-Credential
```

Skapa en en-till-en PowerShell-fjärrsession till domänkontrollanten med namnet dc01.

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

Observera att PowerShell-prompten föregås av i föregående exempel `[dc01]` . Det innebär att du befinner dig i en interaktiv PowerShell-session till fjärrdatorn med namnet dc01. Alla kommandon som du kör på dc01, inte på den lokala datorn. Tänk också på att du bara har åtkomst till PowerShell-kommandon som finns på fjärrdatorn och inte på den lokala datorn. Om du har installerat ytterligare moduler på datorn är det med andra ord inte tillgängligt på fjärrdatorn.

När du är ansluten till en fjärrdator via en en-till-en interaktiv PowerShell-fjärrsession, sitter du effektivt på fjärrdatorn. Objekten är normala objekt precis som de som du har arbetat med i hela boken.

```powershell
[dc01]:  Get-Process | Get-Member
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
[dc01]:
```

När du är klar med fjärrdatorn avslutar du en-till-en-fjärrsession med hjälp av `Exit-PSSession` cmdleten.

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a>En-till-många-fjärrkommunikation

Ibland kan du behöva utföra en aktivitet interaktivt på en fjärrdator. Men fjärr kommunikation är mycket mer kraftfullt när du utför en aktivitet på flera fjärrdatorer samtidigt. Använd `Invoke-Command` cmdleten för att köra ett kommando mot en eller flera fjärranslutna datorer samtidigt.

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

I föregående exempel frågades tre servrar om status för Windows tids tjänst. `Get-Service`Cmdleten placerades inuti skript blocket för `Invoke-Command` . `Get-Service`körs faktiskt på fjärrdatorn och resultatet returneras till din lokala dator som avserialiserade objekt.

Rör föregående kommando för att `Get-Member` Visa att resultaten är deserialiserade objekt.

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred | Get-Member
```

```Output
   TypeName: Deserialized.System.ServiceProcess.ServiceController

Name                MemberType   Definition
----                ----------   ----------
GetType             Method       type GetType()
ToString            Method       string ToString(), string ToString(string format, Sys...
Name                NoteProperty string Name=W32time
PSComputerName      NoteProperty string PSComputerName=sql02
PSShowComputerName  NoteProperty bool PSShowComputerName=True
RequiredServices    NoteProperty Deserialized.System.ServiceProcess.ServiceController[...
RunspaceId          NoteProperty guid RunspaceId=570313c4-ac84-4109-bf67-c6b33236af0a
CanPauseAndContinue Property     System.Boolean {get;set;}
CanShutdown         Property     System.Boolean {get;set;}
CanStop             Property     System.Boolean {get;set;}
Container           Property      {get;set;}
DependentServices   Property     Deserialized.System.ServiceProcess.ServiceController[...
DisplayName         Property     System.String {get;set;}
MachineName         Property     System.String {get;set;}
ServiceHandle       Property     System.String {get;set;}
ServiceName         Property     System.String {get;set;}
ServicesDependedOn  Property     Deserialized.System.ServiceProcess.ServiceController[...
ServiceType         Property     System.String {get;set;}
Site                Property      {get;set;}
StartType           Property     System.String {get;set;}
Status              Property     System.String {get;set;}
```

Observera att de flesta metoderna saknas på avserialiserade objekt. Det innebär att de inte är Live-objekt. de är inerta. Det går inte att starta eller stoppa en tjänst med hjälp av ett avserialiserat objekt eftersom det är en ögonblicks bild av det objektets tillstånd som den tidpunkt då kommandot kördes på fjärrdatorn.

Det innebär inte att du inte kan starta eller stoppa en tjänst med hjälp av en metod med `Invoke-Command` trots. Det innebär bara att metoden måste anropas i fjärrsessionen.

Jag stoppar Windows tids tjänst på alla tre dessa fjärrservrar med hjälp av metoden **Stop ()** för att bevisa den här punkten.

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {(Get-Service -Name W32time).Stop()} -Credential $Cred
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

Som vi nämnt i föregående kapitel, om det finns en cmdlet för att utföra en uppgift rekommenderar vi att du använder den i stället för att använda en metod. I föregående scenario rekommenderar vi att du använder `Stop-Service` cmdleten i stället för metoden Stop. Jag valde att använda metoden **Stop ()** för att bevisa en punkt eftersom många personer är under den fel begreppen att metoder inte kan anropas när PowerShell-fjärrkommunikation används. De kan inte anropas för det objekt som returneras eftersom det har deserialiserats, men de kan anropas i själva fjärrsessionen.

## <a name="powershell-sessions"></a>PowerShell-sessioner

I det sista exemplet i föregående avsnitt körde jag två kommandon med hjälp av `Invoke-Command` cmdleten.
Det innebär att två separata sessioner måste konfigureras och avgränsas för att köra dessa två kommandon.

Precis som i de CIM-sessioner som diskuteras i kapitel 7, kan en PowerShell-session till en fjärrdator användas för att köra flera kommandon mot fjärrdatorn utan att du behöver göra en ny session för varje enskilt kommando.

Skapa en PowerShell-session för var och en av de tre datorerna som vi har arbetat med i det här kapitlet, DC01, SQL02 och WEB01.

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

Använd nu variabeln `$Session` som heter för att starta Windows tids tjänst med en metod och kontrol lera tjänstens status.

```powershell
Invoke-Command -Session $Session {(Get-Service -Name W32time).Start()}
Invoke-Command -Session $Session {Get-Service -Name W32time}
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

När sessionen har skapats med alternativa autentiseringsuppgifter, behöver du inte längre ange autentiseringsuppgifterna varje gång ett kommando körs.

När du är klar med att använda sessionerna måste du ta bort dem.

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a>Sammanfattning

I det här kapitlet har du lärt dig om PowerShell-fjärrkommunikation, hur du kör kommandon i en interaktiv session med en fjärran sluten dator och hur du kör kommandon mot flera datorer med en-till-många-fjärrkommunikation. Du har också lärt dig fördelarna med att använda en PowerShell-session när du kör flera kommandon mot samma fjärrdator.

## <a name="review"></a>Granska

1. Hur aktiverar jag PowerShell-fjärrkommunikation?
1. Vad är PowerShell-kommandot för att starta en interaktiv session med en fjärran sluten dator?
1. Vad är en fördel med att använda en PowerShell-fjärrsession jämfört med att bara ange dator namnet med varje kommando?
1. Kan en PowerShell-fjärrsession användas med en en-till-en-fjärrsession?
1. Vad är skillnaden i den typ av objekt som returneras av cmdletar jämfört med de som returneras när du kör samma cmdlets mot fjärrdatorer med `Invoke-Command` ?

## <a name="recommended-reading"></a>Rekommenderad läsning

- [about_Remote][]
- [about_Remote_FAQ][]
- [about_Remote_Output][]
- [about_Remote_Requirements][]
- [about_Remote_Troubleshooting][]
- [about_Remote_Variables][]

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
