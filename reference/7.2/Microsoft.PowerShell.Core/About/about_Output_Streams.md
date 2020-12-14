---
description: Förklarar tillgängligheten och syftet med utgående strömmar i PowerShell.
Locale: en-US
ms.date: 10/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_output_streams?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Output_Streams
ms.openlocfilehash: 1dd6424ea14aa241b084a0a2c97a7e9bf6927518
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710578"
---
# <a name="about-output-streams"></a>Om utgående strömmar

## <a name="short-description"></a>Kort beskrivning
Förklarar tillgängligheten och syftet med utgående strömmar i PowerShell.

## <a name="long-description"></a>Lång beskrivning

PowerShell tillhandahåller flera utgående data strömmar. Strömmarna tillhandahåller kanaler för olika typer av meddelanden. Du kan skriva till dessa strömmar med tillhör ande cmdlet eller omdirigering. Mer information finns i [about_Redirection](about_Redirection.md).

PowerShell stöder följande utgående strömmar.

| Skicka # |      Beskrivning       | Infört i  |    Skriv cmdlet     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **Lyckad** ström     | PowerShell 2,0 | `Write-Output`      |
| 2        | **Fel** ström       | PowerShell 2,0 | `Write-Error`       |
| 3        | **Varnings** ström     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **Utförlig** data ström     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **Fel söknings** ström       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **Informations** ström | PowerShell 5.0 | `Write-Information` |
| saknas      | **Förlopps** ström    | PowerShell 3.0 | `Write-Progress`    |

> [!NOTE]
> **Förlopps** data strömmen har inte stöd för omdirigering.

## <a name="success-stream"></a>Lyckad ström

Strömmen som **lyckades** är standard strömmen för normala, lyckade resultat.
Använd `Write-Output` cmdleten för att explicit skriva objekt till den här data strömmen. Den här data strömmen används för att skicka objekt via PowerShell-pipeline. Den **framgångs rik** data strömmen är ansluten till **STDOUT** -dataströmmen för interna program.

## <a name="error-stream"></a>Fel ström

**Fel** data strömmen är standard strömmen för fel resultat. Använd `Write-Error` cmdleten för att explicit skriva till den här data strömmen. **Fel** data strömmen är ansluten till **stderr** -dataströmmen för interna program. I de flesta fall kan de här felen avsluta pipelinen för körning. Fel som skrivs till den här data strömmen läggs också till i den `$Error` automatiska variabeln. Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).

## <a name="warning-stream"></a>Varnings ström

**Varnings** strömmen är avsedd för fel villkor som är mindre allvarliga än fel som skrivs till **fel** strömmen. Under normala förhållanden avslutar de här varningarna inte körningen. Varningar skrivs inte till den `$Error` automatiska variabeln. Använd `Write-Warning` cmdleten för att explicit skriva till den här data strömmen.

## <a name="verbose-stream"></a>Utförlig data ström

**Utförlig** data ström är avsedd för meddelanden som hjälper användare att felsöka kommandon när de körs interaktivt eller från ett skript. Använd `Write-Verbose` cmdleten för att explicit skriva meddelanden till den här data strömmen. Många cmdletar ger utförliga utdata som är användbara för att förstå de interna arbetsflödena för cmdleten. Utförliga meddelanden är bara utdata när du använder den `-Verbose` gemensamma parametern. Mer information finns i [about_CommonParameters](about_CommonParameters.md).

## <a name="debug-stream"></a>Fel söknings ström

**Fel söknings** strömmen används för meddelanden som hjälper skriptare att förstå varför koden inte fungerar. Använd `Write-Debug` cmdleten för att explicit skriva till den här data strömmen. Fel söknings meddelanden visas bara när du använder den `-Debug` gemensamma parametern. Mer information finns i [about_CommonParameters](about_CommonParameters.md).

Fel söknings meddelanden är avsedda för skript och cmdlet-utvecklare som är mer än slutanvändare. Dessa fel söknings meddelanden kan innehålla intern information som krävs för djup fel sökning.

## <a name="information-stream"></a>Informations ström

**Informations** strömmen är avsedd att tillhandahålla ett meddelande som hjälper en användare att förstå vad ett skript gör. Den kan också användas av utvecklare som en ytterligare ström som används för att skicka information via PowerShell. Utvecklaren kan tagga ström data och ha en speciell hantering för den data strömmen. Använd `Write-Information` cmdleten för att explicit skriva till den här data strömmen.

## <a name="progress-stream"></a>Förlopps ström

**Förlopps** data strömmen används för meddelanden som kommunicerar förloppet i längre köra kommandon och skript. Använd `Write-Progress` cmdleten för att explicit skriva meddelanden till den här data strömmen. **Förlopps** data strömmen har inte stöd för omdirigering.

## <a name="see-also"></a>Se även

- [Skriv-debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Skriv-fel](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Skriv värd](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Skriv information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Skriva-utdata](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Skriv förlopp](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Skriv-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Skriv varning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_CommonParameters](about_CommonParameters.md)
- [about_Redirection](about_Redirection.md)
