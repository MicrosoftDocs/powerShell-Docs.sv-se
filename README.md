# <a name="microsoft-open-source-code-of-conduct"></a>Microsofts regler för uppförande för öppen källkod

Det här projektet har antagit [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) (Microsofts regler för uppförande för öppen källkod).
Mer information finns i [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) (Vanliga frågor och svar om regler för uppförande), eller kontakta [opencode@microsoft.com](mailto:opencode@microsoft.com) med ytterligare frågor eller kommentarer.

[![Skapa status](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>PowerShell-dokumentation

Välkommen till PowerShell-Docs-lagringsplatsen, där den officiella PowerShell-dokumentationen.

## <a name="repository-structure"></a>Struktur för databasen

Var och en av följande översta mappar i den här lagringsplatsen innehåller en dokumentuppsättning som publiceras till [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/Developer/](https://docs.microsoft.com/powershell/developer/) är framtida hem för PowerShell SDK-dokumentation
  - Vi håller på att migrera det här innehållet från MSDN
- [/DSC/](https://docs.microsoft.com/powershell/dsc/) är för funktionen Desired State Configuration
- [/Gallery/](https://docs.microsoft.com/powershell/gallery) avser den [PowerShell-galleriet](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) är för funktionen Just Enough Administration
- [/Reference/](https://docs.microsoft.com/powershell/scripting/) är för PowerShell-konceptuella artiklar och modulreferens för version 3.0, 4.0, 5.0, 5.1 och 6.0
  - Det här innehållet är också källan till hjälpinnehåll som hämtas av den `Get-Help` cmdlet
- [/WMF](https://docs.microsoft.com/powershell/wmf/readme) innehåller viktig information för Windows Management Framework paketet används för att distribuera nya versioner av PowerShell tidigare versioner av Windows.

## <a name="contributing"></a>Bidra

Vi aktivt sammanfoga bidrag till den här databasen via [pull-begäran](https://help.github.com/articles/using-pull-requests/) till den *mellanlagring* gren.
Observera att innan du skickar en pullbegäran måste du [logga ett licensavtal för bidrag](https://cla.microsoft.com/) så att communityn är kostnadsfritt att använda dina bidrag.

Mer information om bidrag till våra [bidragsgivarguide](CONTRIBUTING.md).
Den deltagarguiden innehåller detaljerad information om hur du kan bidra dokumentation, föreslagna verktyg och stil och formateringskrav.
Använd mallar för problem och Pull-begäran för att hålla dokumentationen konsekvent mellan olika versioner.

## <a name="licenses"></a>Licenser

Det finns två licensfiler för det här projektet.
MIT-licensen gäller för koden i den här lagringsplatsen.
Creative Commons-licens gäller för dokumentationen.