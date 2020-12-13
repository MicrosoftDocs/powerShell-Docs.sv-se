---
title: PowerShell-fjärranvändning
description: Det finns många olika sätt att köra kommandon mot fjärrdatorer i PowerShell.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ee83af41b53b254dd3dd993931333edac2f44f5a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "84436465"
---
# <a name="chapter-8---powershell-remoting"></a><span data-ttu-id="62dba-103">Kapitel 8 – PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="62dba-103">Chapter 8 - PowerShell remoting</span></span>

<span data-ttu-id="62dba-104">PowerShell har många olika sätt att köra kommandon mot fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="62dba-104">PowerShell has many different ways to run commands against remote computers.</span></span> <span data-ttu-id="62dba-105">I det sista kapitlet såg du hur du fjärrfrågar WMI med CIM-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="62dba-105">In the last chapter, you saw how to remotely query WMI using the CIM cmdlets.</span></span> <span data-ttu-id="62dba-106">PowerShell innehåller också flera cmdletar som har en inbyggd **computername** -parameter.</span><span class="sxs-lookup"><span data-stu-id="62dba-106">PowerShell also includes several cmdlets that have a built-in **ComputerName** parameter.</span></span>

<span data-ttu-id="62dba-107">Som du ser i följande exempel, `Get-Command` kan användas med parametern **ParameterName** för att avgöra vilka kommandon som har en **computername** -parameter.</span><span class="sxs-lookup"><span data-stu-id="62dba-107">As shown in the following example, `Get-Command` can be used with the **ParameterName** parameter to determine what commands have a **ComputerName** parameter.</span></span>

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

<span data-ttu-id="62dba-108">Kommandon som `Get-Process` och `Get-Hotfix` har en **computername** -parameter.</span><span class="sxs-lookup"><span data-stu-id="62dba-108">Commands such as `Get-Process` and `Get-Hotfix` have a **ComputerName** parameter.</span></span> <span data-ttu-id="62dba-109">Detta är inte den långsiktiga riktningen som Microsoft är rubrik för att köra kommandon mot fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="62dba-109">This isn't the long-term direction that Microsoft is heading for running commands against remote computers.</span></span> <span data-ttu-id="62dba-110">Även om du hittar ett kommando som har en **computername** -parameter, är det möjligt att du behöver ange alternativa autentiseringsuppgifter och att den inte har någon **Credential** -parameter.</span><span class="sxs-lookup"><span data-stu-id="62dba-110">Even if you find a command that has a **ComputerName** parameter, chances are that you'll need to specify alternate credentials and it won't have a **Credential** parameter.</span></span> <span data-ttu-id="62dba-111">Om du har valt att köra PowerShell från ett förhöjt konto kan en brand vägg mellan dig och fjärrdatorn blockera begäran.</span><span class="sxs-lookup"><span data-stu-id="62dba-111">And if you decided to run PowerShell from an elevated account, a firewall between you and the remote computer can block the request.</span></span>

<span data-ttu-id="62dba-112">Om du vill använda PowerShell-fjärrkommandon som visas i det här kapitlet måste PowerShell-fjärrkommunikation vara aktiverat på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="62dba-112">To use the PowerShell remoting commands that are demonstrated in this chapter, PowerShell remoting must be enabled on the remote computer.</span></span> <span data-ttu-id="62dba-113">Använd `Enable-PSRemoting` cmdleten för att aktivera PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="62dba-113">Use the `Enable-PSRemoting` cmdlet to enable PowerShell remoting.</span></span>

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

## <a name="one-to-one-remoting"></a><span data-ttu-id="62dba-114">En-till-en-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="62dba-114">One-To-One Remoting</span></span>

<span data-ttu-id="62dba-115">Om du vill att fjärrsessionen ska vara interaktiv, är en-till-en-fjärr kommunikation vad du vill ha.</span><span class="sxs-lookup"><span data-stu-id="62dba-115">If you want your remote session to be interactive, then one-to-one remoting is what you want.</span></span>
<span data-ttu-id="62dba-116">Den här typen av fjärr kommunikation tillhandahålls via `Enter-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="62dba-116">This type of remoting is provided via the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="62dba-117">I det sista kapitlet sparade jag autentiseringsuppgifterna för domän administratören i en variabel med namnet `$Cred` .</span><span class="sxs-lookup"><span data-stu-id="62dba-117">In the last chapter, I stored my domain admin credentials in a variable named `$Cred`.</span></span> <span data-ttu-id="62dba-118">Om du inte redan har gjort det kan du gå vidare och spara dina autentiseringsuppgifter för domän administratören i `$Cred` variabeln.</span><span class="sxs-lookup"><span data-stu-id="62dba-118">If you haven't already done so, go ahead and store your domain admin credentials in the `$Cred` variable.</span></span>

<span data-ttu-id="62dba-119">På så sätt kan du ange autentiseringsuppgifterna en gång och använda dem på per kommando så länge den aktuella PowerShell-sessionen är aktiv.</span><span class="sxs-lookup"><span data-stu-id="62dba-119">This allows you to enter the credentials once and use them on a per command basis as long as your current PowerShell session is active.</span></span>

```powershell
$Cred = Get-Credential
```

<span data-ttu-id="62dba-120">Skapa en en-till-en PowerShell-fjärrsession till domänkontrollanten med namnet dc01.</span><span class="sxs-lookup"><span data-stu-id="62dba-120">Create a one-to-one PowerShell remoting session to the domain controller named dc01.</span></span>

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

<span data-ttu-id="62dba-121">Observera att PowerShell-prompten föregås av i föregående exempel `[dc01]` .</span><span class="sxs-lookup"><span data-stu-id="62dba-121">Notice that in the previous example that the PowerShell prompt is preceded by `[dc01]`.</span></span> <span data-ttu-id="62dba-122">Det innebär att du befinner dig i en interaktiv PowerShell-session till fjärrdatorn med namnet dc01.</span><span class="sxs-lookup"><span data-stu-id="62dba-122">This means you're in an interactive PowerShell session to the remote computer named dc01.</span></span> <span data-ttu-id="62dba-123">Alla kommandon som du kör på dc01, inte på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="62dba-123">Any commands you execute run on dc01, not on your local computer.</span></span> <span data-ttu-id="62dba-124">Tänk också på att du bara har åtkomst till PowerShell-kommandon som finns på fjärrdatorn och inte på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="62dba-124">Also, keep in mind that you only have access to the PowerShell commands that exist on the remote computer and not the ones on your local computer.</span></span> <span data-ttu-id="62dba-125">Om du har installerat ytterligare moduler på datorn är det med andra ord inte tillgängligt på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="62dba-125">In other words, if you've installed additional modules on your computer, they aren't accessible on the remote computer.</span></span>

<span data-ttu-id="62dba-126">När du är ansluten till en fjärrdator via en en-till-en interaktiv PowerShell-fjärrsession, sitter du effektivt på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="62dba-126">When you're connected to a remote computer via a one-to-one interactive PowerShell remoting session, you're effectively sitting at the remote computer.</span></span> <span data-ttu-id="62dba-127">Objekten är normala objekt precis som de som du har arbetat med i hela boken.</span><span class="sxs-lookup"><span data-stu-id="62dba-127">The objects are normal objects just like the ones you've been working with throughout this entire book.</span></span>

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

<span data-ttu-id="62dba-128">När du är klar med fjärrdatorn avslutar du en-till-en-fjärrsession med hjälp av `Exit-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="62dba-128">When you're done working with the remote computer, exit the one-to-one remoting session by using the `Exit-PSSession` cmdlet.</span></span>

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a><span data-ttu-id="62dba-129">En-till-många-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="62dba-129">One-To-Many Remoting</span></span>

<span data-ttu-id="62dba-130">Ibland kan du behöva utföra en aktivitet interaktivt på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="62dba-130">Sometimes you may need to perform a task interactively on a remote computer.</span></span> <span data-ttu-id="62dba-131">Men fjärr kommunikation är mycket mer kraftfullt när du utför en aktivitet på flera fjärrdatorer samtidigt.</span><span class="sxs-lookup"><span data-stu-id="62dba-131">But remoting is much more powerful when performing a task on multiple remote computers at the same time.</span></span> <span data-ttu-id="62dba-132">Använd `Invoke-Command` cmdleten för att köra ett kommando mot en eller flera fjärranslutna datorer samtidigt.</span><span class="sxs-lookup"><span data-stu-id="62dba-132">Use the `Invoke-Command` cmdlet to run a command against one or more remote computers at the same time.</span></span>

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

<span data-ttu-id="62dba-133">I föregående exempel frågades tre servrar om status för Windows tids tjänst.</span><span class="sxs-lookup"><span data-stu-id="62dba-133">In the previous example, three servers were queried for the status of the Windows Time service.</span></span> <span data-ttu-id="62dba-134">`Get-Service`Cmdleten placerades inuti skript blocket för `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="62dba-134">The `Get-Service` cmdlet was placed inside the script block of `Invoke-Command`.</span></span> <span data-ttu-id="62dba-135">`Get-Service` körs faktiskt på fjärrdatorn och resultatet returneras till din lokala dator som avserialiserade objekt.</span><span class="sxs-lookup"><span data-stu-id="62dba-135">`Get-Service` actually runs on the remote computer and the results are returned to your local computer as deserialized objects.</span></span>

<span data-ttu-id="62dba-136">Rör föregående kommando för att `Get-Member` Visa att resultaten är deserialiserade objekt.</span><span class="sxs-lookup"><span data-stu-id="62dba-136">Piping the previous command to `Get-Member` shows that the results are indeed deserialized objects.</span></span>

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

<span data-ttu-id="62dba-137">Observera att de flesta metoderna saknas på avserialiserade objekt.</span><span class="sxs-lookup"><span data-stu-id="62dba-137">Notice that the majority of the methods are missing on deserialized objects.</span></span> <span data-ttu-id="62dba-138">Det innebär att de inte är Live-objekt. de är inerta.</span><span class="sxs-lookup"><span data-stu-id="62dba-138">This means they're not live objects; they're inert.</span></span> <span data-ttu-id="62dba-139">Det går inte att starta eller stoppa en tjänst med hjälp av ett avserialiserat objekt eftersom det är en ögonblicks bild av det objektets tillstånd som den tidpunkt då kommandot kördes på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="62dba-139">You can't start or stop a service using a deserialized object because it's a snapshot of the state of that object the point when the command ran on the remote computer.</span></span>

<span data-ttu-id="62dba-140">Det innebär inte att du inte kan starta eller stoppa en tjänst med hjälp av en metod med `Invoke-Command` trots.</span><span class="sxs-lookup"><span data-stu-id="62dba-140">That doesn't mean you can't start or stop a service using a method with `Invoke-Command` though.</span></span> <span data-ttu-id="62dba-141">Det innebär bara att metoden måste anropas i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="62dba-141">It just means that the method has to be called in the remote session.</span></span>

<span data-ttu-id="62dba-142">Jag stoppar Windows tids tjänst på alla tre dessa fjärrservrar med hjälp av metoden **Stop ()** för att bevisa den här punkten.</span><span class="sxs-lookup"><span data-stu-id="62dba-142">I'll stop the Windows Time service on all three of those remote servers using the **Stop()** method to prove this point.</span></span>

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

<span data-ttu-id="62dba-143">Som vi nämnt i föregående kapitel, om det finns en cmdlet för att utföra en uppgift rekommenderar vi att du använder den i stället för att använda en metod.</span><span class="sxs-lookup"><span data-stu-id="62dba-143">As mentioned in a previous chapter, if a cmdlet exists for accomplishing a task, I recommend using it instead of using a method.</span></span> <span data-ttu-id="62dba-144">I föregående scenario rekommenderar vi att du använder `Stop-Service` cmdleten i stället för metoden Stop.</span><span class="sxs-lookup"><span data-stu-id="62dba-144">In the previous scenario, I recommend using the `Stop-Service` cmdlet instead of the stop method.</span></span> <span data-ttu-id="62dba-145">Jag valde att använda metoden **Stop ()** för att bevisa en punkt eftersom många personer är under den fel begreppen att metoder inte kan anropas när PowerShell-fjärrkommunikation används.</span><span class="sxs-lookup"><span data-stu-id="62dba-145">I chose to use the **Stop()** method to prove a point since many people are under the misconception that methods can't be called when using PowerShell remoting.</span></span> <span data-ttu-id="62dba-146">De kan inte anropas för det objekt som returneras eftersom det har deserialiserats, men de kan anropas i själva fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="62dba-146">They can't be called on the object that's returned because it's deserialized, but they can be called in the remote session itself.</span></span>

## <a name="powershell-sessions"></a><span data-ttu-id="62dba-147">PowerShell-sessioner</span><span class="sxs-lookup"><span data-stu-id="62dba-147">PowerShell Sessions</span></span>

<span data-ttu-id="62dba-148">I det sista exemplet i föregående avsnitt körde jag två kommandon med hjälp av `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="62dba-148">In the last example in the previous section, I ran two commands using the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="62dba-149">Det innebär att två separata sessioner måste konfigureras och avgränsas för att köra dessa två kommandon.</span><span class="sxs-lookup"><span data-stu-id="62dba-149">That means two separate sessions had to be set up and torn down to run those two commands.</span></span>

<span data-ttu-id="62dba-150">Precis som i de CIM-sessioner som diskuteras i kapitel 7, kan en PowerShell-session till en fjärrdator användas för att köra flera kommandon mot fjärrdatorn utan att du behöver göra en ny session för varje enskilt kommando.</span><span class="sxs-lookup"><span data-stu-id="62dba-150">Similar to the CIM sessions discussed in Chapter 7, a PowerShell session to a remote computer can be used to run multiple commands against the remote computer without the overhead of a new session for each individual command.</span></span>

<span data-ttu-id="62dba-151">Skapa en PowerShell-session för var och en av de tre datorerna som vi har arbetat med i det här kapitlet, DC01, SQL02 och WEB01.</span><span class="sxs-lookup"><span data-stu-id="62dba-151">Create a PowerShell session to each of the three computers we've been working with in this chapter, DC01, SQL02, and WEB01.</span></span>

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

<span data-ttu-id="62dba-152">Använd nu variabeln `$Session` som heter för att starta Windows tids tjänst med en metod och kontrol lera tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="62dba-152">Now use the variable named `$Session` to start the Windows Time service using a method and check the status of the service.</span></span>

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

<span data-ttu-id="62dba-153">När sessionen har skapats med alternativa autentiseringsuppgifter, behöver du inte längre ange autentiseringsuppgifterna varje gång ett kommando körs.</span><span class="sxs-lookup"><span data-stu-id="62dba-153">Once the session is created using alternate credentials, it's no longer necessary to specify the credentials each time a command is run.</span></span>

<span data-ttu-id="62dba-154">När du är klar med att använda sessionerna måste du ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="62dba-154">When you're finished using the sessions, be sure to remove them.</span></span>

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a><span data-ttu-id="62dba-155">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="62dba-155">Summary</span></span>

<span data-ttu-id="62dba-156">I det här kapitlet har du lärt dig om PowerShell-fjärrkommunikation, hur du kör kommandon i en interaktiv session med en fjärran sluten dator och hur du kör kommandon mot flera datorer med en-till-många-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="62dba-156">In this chapter you've learned about PowerShell remoting, how to run commands in an interactive session with one remote computer, and how to run commands against multiple computers using one-to-many remoting.</span></span> <span data-ttu-id="62dba-157">Du har också lärt dig fördelarna med att använda en PowerShell-session när du kör flera kommandon mot samma fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="62dba-157">You've also learned the benefits of using a PowerShell session when running multiple commands against the same remote computer.</span></span>

## <a name="review"></a><span data-ttu-id="62dba-158">Genomgång</span><span class="sxs-lookup"><span data-stu-id="62dba-158">Review</span></span>

1. <span data-ttu-id="62dba-159">Hur aktiverar jag PowerShell-fjärrkommunikation?</span><span class="sxs-lookup"><span data-stu-id="62dba-159">How do you enable PowerShell remoting?</span></span>
1. <span data-ttu-id="62dba-160">Vad är PowerShell-kommandot för att starta en interaktiv session med en fjärran sluten dator?</span><span class="sxs-lookup"><span data-stu-id="62dba-160">What is the PowerShell command for starting an interactive session with a remote computer?</span></span>
1. <span data-ttu-id="62dba-161">Vad är en fördel med att använda en PowerShell-fjärrsession jämfört med att bara ange dator namnet med varje kommando?</span><span class="sxs-lookup"><span data-stu-id="62dba-161">What is a benefit of using a PowerShell remoting session versus just specifying the computer name with each command?</span></span>
1. <span data-ttu-id="62dba-162">Kan en PowerShell-fjärrsession användas med en en-till-en-fjärrsession?</span><span class="sxs-lookup"><span data-stu-id="62dba-162">Can a PowerShell remoting session be used with a one-to-one remoting session?</span></span>
1. <span data-ttu-id="62dba-163">Vad är skillnaden i den typ av objekt som returneras av cmdletar jämfört med de som returneras när du kör samma cmdlets mot fjärrdatorer med `Invoke-Command` ?</span><span class="sxs-lookup"><span data-stu-id="62dba-163">What is the difference in the type of objects that are returned by cmdlets versus those returned when running those same cmdlets against remote computers with `Invoke-Command`?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="62dba-164">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="62dba-164">Recommended Reading</span></span>

- <span data-ttu-id="62dba-165">[about_Remote][]</span><span class="sxs-lookup"><span data-stu-id="62dba-165">[about_Remote][]</span></span>
- <span data-ttu-id="62dba-166">[about_Remote_FAQ][]</span><span class="sxs-lookup"><span data-stu-id="62dba-166">[about_Remote_FAQ][]</span></span>
- <span data-ttu-id="62dba-167">[about_Remote_Output][]</span><span class="sxs-lookup"><span data-stu-id="62dba-167">[about_Remote_Output][]</span></span>
- <span data-ttu-id="62dba-168">[about_Remote_Requirements][]</span><span class="sxs-lookup"><span data-stu-id="62dba-168">[about_Remote_Requirements][]</span></span>
- <span data-ttu-id="62dba-169">[about_Remote_Troubleshooting][]</span><span class="sxs-lookup"><span data-stu-id="62dba-169">[about_Remote_Troubleshooting][]</span></span>
- <span data-ttu-id="62dba-170">[about_Remote_Variables][]</span><span class="sxs-lookup"><span data-stu-id="62dba-170">[about_Remote_Variables][]</span></span>

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
