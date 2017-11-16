---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: f3c218fc668e35fa50047459d8031d77cdf985a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="reporting-on-jea"></a>Rapportering av JEA
Du kan använda för att rapportera om konfigurationen av JEA tillstånd:
1.  **Get-PSSessionConfiguration** returnera en lista över alla registrerade slutpunkter på en viss dator.
2.  **Get-PSSessionCapability** för att rapportera om funktionerna som har en viss användare på en viss slutpunkt.

Här är ett exempel på **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Rapportera om den _åtgärder_ användare tog under en session JEA, kan du:
1. Aktivera ”over-det axel” betyg för denna JEA slutpunkt och se katalogen betyg för en fullständig logg över åtgärder för varje användare
2. Aktivera loggning för PowerShell-modulen och inspektera händelseloggarna PowerShell.

