---
description: Beskriver grupprincip inställningarna för PowerShell
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: c247feb5b7c604e3e1d0442a9aa142e5eb25ec08
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271232"
---
# <a name="about-group-policy-settings"></a>Om grupprincip inställningar

## <a name="short-description"></a>Kort beskrivning
Beskriver grupprincip inställningarna för PowerShell

## <a name="long-description"></a>Lång beskrivning

PowerShell innehåller grupprincip inställningar som hjälper dig att definiera konsekventa konfigurations värden för Windows-datorer i en företags miljö.

Inställningarna för PowerShell-grupprincip finns i följande grupprincip sökvägar:

```
Computer Configuration\
  Administrative Templates\
    PowerShell Core

User Configuration\
  Administrative Templates\
    PowerShell Core
```

Grup princip inställningar i användar konfigurations Sök vägen har företräde framför grupprincip inställningar i datorns konfigurations Sök väg.

PowerShell 7 innehåller grupprincip mallar och ett installations skript i `$PSHOME` .

Grupprincip verktyg använder administrativa mallfiler ( `.admx` , `.adml` ) för att fylla i princip inställningar i användar gränssnittet. Detta gör det möjligt för administratörer att hantera registerbaserade princip inställningar. `InstallPSCorePolicyDefinitions.ps1`Skriptet installerar **PowerShell Core administrativa mallar** på den lokala datorn.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode       LastWriteTime         Length Name
----       -------------         ------ ----
-a---      2/27/2020 12:38 AM     15861 InstallPSCorePolicyDefinitions.ps1
-a---      2/27/2020 12:28 AM      9675 PowerShellCoreExecutionPolicy.adml
-a---      2/27/2020 12:28 AM      6201 PowerShellCoreExecutionPolicy.admx
```

När du har installerat mallarna kan du redigera inställningarna i grupprincip-redigeraren ( `gpedit.msc` ).

Principerna är följande:

- Konfiguration av konsolsession: anger en konfigurations slut punkt där PowerShell körs.
- Aktivera modul loggning: anger **LogPipelineExecutionDetails** -egenskapen för moduler.
- Aktivera loggning av PowerShell-skript block: aktiverar detaljerad loggning av alla PowerShell-skript.
- Aktivera skript körning: ställer in PowerShell-körnings principen.
- Aktivera PowerShell-avskrift: aktiverar insamling av indata och utdata från PowerShell-kommandon i textbaserade avskrifter.
- Ange standard käll Sök väg för `Update-Help` : Anger källan för uppdaterbar hjälp till en katalog, inte Internet.

Varje PowerShell-grupprincip inställning har ett alternativ ("Använd Windows PowerShell princip inställnings fält") för att använda värdet från en liknande Windows PowerShell grupprincip-inställning som finns i följande grupprincip sökvägar:

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

> [!NOTE]
> Dessa **PowerShell-administrativa mallar** innehåller inte inställningar för Windows PowerShell. Mer information om hur du hämtar andra mallar och konfigurerar grup principer finns i [så här skapar och hanterar du den centrala butiken för grupprincip administrativa mallar i Windows][gpstore].

## <a name="console-session-configuration"></a>Konfiguration av konsolsession

**Konfigurations** princip inställningen för konsolsessionen anger en konfigurations slut punkt där PowerShell körs. Detta kan vara vilken slut punkt som helst som är registrerad på den lokala datorn, inklusive standard slut punkter för PowerShell-fjärrkommunikation eller en anpassad slut punkt med vissa användar roll funktioner.

## <a name="turn-on-module-logging"></a>Aktivera modul loggning

Princip inställningen Aktivera loggning av **modul** aktiverar loggning för valda PowerShell-moduler. Inställningen gäller alla sessioner på alla berörda datorer.

Om du aktiverar den här policy inställningen och anger en eller flera moduler, registreras pipeline-körningar för de angivna modulerna i Windows PowerShell-loggen i Loggboken.

Om du inaktiverar den här inställningen inaktive ras loggning av körnings händelser för alla PowerShell-moduler.

Om den här inställningen inte konfigureras bestämmer egenskapen **LogPipelineExecutionDetails** för varje modul om körnings händelserna i en modul loggas. Som standard har egenskapen **LogPipelineExecutionDetails** för alla moduler angetts till false.

Använd följande kommando format om du vill aktivera en moduls loggning för en modul. Modulen måste importeras till sessionen och inställningen är endast effektiv i den aktuella sessionen.

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

Om du vill aktivera module-loggning för alla sessioner på en viss dator lägger du till föregående kommandon i PowerShell-profilen "alla användare" ( `$Profile.AllUsersAllHosts` ).

Mer information om module-loggning finns [about_Modules](about_Modules.md).

## <a name="turn-on-powershell-script-block-logging"></a>Aktivera loggning av PowerShell-skriptkommando

Princip inställningen **Aktivera PowerShell-skript block loggning** aktiverar loggning av alla PowerShell-skriptfiler till händelse loggen Microsoft-Windows-PowerShell/Operational. Om du aktiverar den här policy inställningen loggar PowerShell Core bearbetningen av kommandon, skript block, funktioner och skript – oavsett om de anropas interaktivt eller via Automation.

Om du inaktiverar den här principinställningen inaktiveras loggning av PowerShell-skriptindata. Om du aktiverar loggning av indata av skriptblock loggar PowerShell även händelser om anrop av ett kommando, skriptblock, funktion eller skript startar eller stoppar. Om du aktiverar loggning av anrop genereras ett stort antal händelseloggar.

## <a name="turn-on-script-execution"></a>Aktivera skript körning

Inställningen **Aktivera princip för skript körning** anger körnings principen för datorer och användare, vilket avgör vilka skript som tillåts köra.

Om du aktiverar princip inställningen kan du välja bland följande princip inställningar.

- **Tillåt endast signerade skript** tillåter att skript endast körs om de är signerade av en betrodd utgivare. Den här inställningen motsvarar körnings principen för AllSigned.

- **Tillåt lokala skript och fjärrsignerade skript** tillåter att alla lokala skript körs. Skript som kommer från Internet måste signeras av en betrodd utgivare. Den här inställningen motsvarar körnings principen för RemoteSigned.

- **Tillåt alla skript** att köra alla skript. Den här princip inställningen motsvarar principen för obegränsad körning.

Om du inaktiverar den här inställningen tillåts inga skript att köras. Den här princip inställningen motsvarar principen för begränsad körning.

Om du inaktiverar eller inte konfigurerar den här princip inställningen avgör den körnings princip som har angetts för datorn eller användaren av `Set-ExecutionPolicy` cmdleten om skript tillåts köra. Standardvärdet är begränsat.

Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).

## <a name="turn-on-powershell-transcription"></a>Aktivera PowerShell-avskrift

Med princip inställningen **Aktivera PowerShell-avskrift** kan du samla in indata och utdata för PowerShell Core-kommandon i textbaserade avskrifter. Om du aktiverar den här inställningen aktive ras avskrifts loggning för PowerShell Core och andra program som utnyttjar PowerShell Core-motorn av PowerShell-kärnan. Som standard registrerar PowerShell Core avskrifts-utdata till varje användares Mina dokument katalog, med ett fil namn som innehåller PowerShell_transcript, tillsammans med dator namnet och start tiden.
Att aktivera den här principen motsvarar att anropa Start-Transcript-cmdlet: en på varje PowerShell Core-session.

Om du inaktiverar den här inställningen inaktive ras avskrifts loggningen av PowerShell-baserade program som standard, även om avskriften fortfarande kan aktive ras via Start-Transcript-cmdleten.

Om du använder OutputDirectory-inställningen för att aktivera avskrifts loggning till en delad plats måste du begränsa åtkomsten till katalogen för att hindra användare från att Visa avskrifterna för andra användare eller datorer.

## <a name="set-the-default-source-path-for-update-help"></a>Ange standard käll Sök väg för Update-Help

**Ange standard käll Sök väg för uppdatering – hjälp** princip inställningen anger ett standardvärde för cmdlet: en **SourcePath** -parameter `Update-Help` .
Den här inställningen förhindrar att användare använder `Update-Help` cmdleten för att hämta hjälpfiler från Internet.

> [!NOTE]
> Den här grupprincip inställningen visas under **dator konfiguration** och **användar konfiguration**. Men endast grupprincip-inställningen under **dator konfiguration** är effektiv. Inställningen grupprincip under **användar konfigurationen** ignoreras.

`Update-Help`Cmdlet: en laddar ned och installerar de senaste hjälpfilerna för PowerShell-moduler och installerar dem på datorn. Som standard `Update-Help` hämtar nya hjälpfiler från en Internet plats som anges av modulen.

Du kan dock använda `Save-Help` cmdleten för att ladda ned de senaste hjälpfilerna till en fil system plats, till exempel en nätverks resurs, och sedan använda `Update-Help` cmdleten för att hämta hjälpfilerna från fil system platsen och installera dem på datorn. Parametern **SourcePath** för `Update-Help` cmdleten anger fil system platsen.

Genom att ange ett standardvärde för parametern **SourcePath** lägger den här grupprincip inställningen implicit till parametern **SourcePath** i alla `Update-Help` kommandon. Användare kan åsidosätta den specifika fil system platsen som anges som standardvärde genom att ange en annan plats för fil systemet.
Men de kan inte ta bort **SourcePath** -parametern från `Update-Help` kommandot.

Om du aktiverar den här inställningen kan du ange ett standardvärde för parametern **SourcePath** . Ange en fil system plats.

Om den här inställningen är inaktive rad eller inte konfigurerad, finns det inget standardvärde för cmdlet-parameterns **SourcePath** -parameter `Update-Help` . Användare kan hämta hjälpen från Internet eller från alla fil system platser.

Mer information finns i [about_Updatable_Help](about_Updatable_Help.md).

## <a name="keywords"></a>Nyckelord

about_Group_Policies about_GroupPolicy

## <a name="see-also"></a>Se även

[Princip för PowerShell-kärnan RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/4-Experimental-Accepted/RFC0041-Policy.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Modules](about_Modules.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Hämta modul](xref:Microsoft.PowerShell.Core.Get-Module)

[Uppdatera – hjälp](xref:Microsoft.PowerShell.Core.Update-Help)

[Spara – hjälp](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759
