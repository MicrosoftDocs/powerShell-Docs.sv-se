---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Komma igång med att använda Windows PowerShell"
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: de09c74e938f11a130864b1620d6c169006a27be
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2017
---
# <a name="getting-ready-to-use-windows-powershell"></a>Komma igång med att använda Windows PowerShell
När Windows PowerShell är installerat och igång, Överväg följande alternativ. Du kan utföra dessa uppgifter när som helst.

- **Installera hjälpfiler.** De cmdlets som ingår i Windows PowerShell 3.0 kommer inte med hjälpfiler. Du kan använda den [Update-Help](/powershell/module/microsoft.powershell.core/update-help) för att hämta och installera de senaste hjälpfilerna på datorn. När filerna har installerats kan du använda den [Get-Help](/powershell/module/microsoft.powershell.core/get-help) för att visa dem åt höger på kommandoraden. Mer information finns i [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

    Du kan läsa hjälpavsnitt online även om du inte väljer att installera hjälpfiler. För att hitta onlineversionen av cmdlet-hjälpavsnittet, skriv: `Get-Help <CmdletName> -Online`. Att bläddra i Windows PowerShell hjälpavsnitt finns i [PowerShell dokumentationen](/powershell/scripting).

- **Kör skript.** För att skydda Windows PowerShell, standardprincipen för körning på Windows PowerShell är **begränsad**. Den här principen kan du köra cmdlet: ar, men inte skript. Kör skript genom att använda den [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) för att ändra körningsprincipen till **alla signerade** eller **RemoteSigned**. Endast medlemmar i gruppen Administratörer på datorn kan köra denna cmdlet. Mer information finns i [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Aktivera fjärrkommunikation.** Systemet har redan konfigurerats att köra fjärrkommandon på andra datorer. På Windows Server 2012 R2 och Windows Server 2012 konfigureras också systemet att ta emot fjärrkommandon, det vill säga, så att andra datorer att köra fjärrkommandon på den lokala datorn. För att aktivera datorer som kör andra versioner av Windows för att ta emot fjärrkommandon kör den [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) på datorn som du vill fjärrhantera. Endast medlemmar i gruppen Administratörer på datorn kan köra denna cmdlet. Mer information finns i [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    Obs: Om fjärrkommunikation är aktiverad på en dator som kör Windows PowerShell 2.0, fjärrkommunikation är fortfarande aktiverat när du har installerat Windows Management Framework 3.0. Dock på Windows Server 2008 (inte Windows Server 2008 R2), måste du aktivera fjärrkommunikation när du har installerat Windows Management Framework 3.0.

## <a name="see-also"></a>Se även
- [Installera Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [Starta Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)

