---
ms.topic: reference
keywords: PowerShell cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094236"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SAMMANFATTNING

Lägger till en ny auktoriseringsregel till Windows PowerShell® Web Access auktoriseringsregeluppsättningen.

## <a name="syntax"></a>Syntax

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>BESKRIVNING

Den **Add-PswaAuthorizationRule** cmdlet lägger till en ny auktoriseringsregel till Windows PowerShell® Web Access auktoriseringsregeluppsättningen.

Du måste ange användare, datorer och Windows PowerShell-slutpunkter för den här regeln. Du kan ange både användare och datorer genom att enskilda användarkonton och datornamn, eller genom att ange grupper.

För en dator som är ansluten till en Active Directory-domän, använder cmdlet: en säkerhetsidentifierare (SID) för datorn för att skapa regeln.
På så sätt kan du använda ett kort namn, ett fullständigt kvalificerat domännamn (FQDN) eller en IP-adress för den **datornamn** på sidan logga in.

Cmdleten skapar regeln med namnet på datorn som tillhandahålls av administratören för en dator som inte är ansluten till en Active Directory-domän. För att ansluta till den här datorn, måste användaren ange datornamnet exakt som det visas i regeln.

Om det finns flera datorer med samma namn i nätverket, kan kort namn matcha till flera datorer. Detta kan leda till tvetydighet när en anslutning upprättas. Exempel: om det finns en regel för den arbetsgruppsdator med namnet ”*Server1*” och en ny dator med namnet *server1.contoso.com* är ansluten till nätverket med hjälp av auktoriseringsreglerna lyckas och Windows PowerShell-webbåtkomst försöker upprätta en anslutning till datorn med namnet ”*Server1*”. Det är inte säkert att anslutningen har upprättats med den angivna arbetsgrupp-datorn. försöket kan göras på arbetsgruppen eller domän datorn med namnet ”*Server1*”. Du rekommenderas att du använder det fullständiga Domännamnet för måldatorn när det är möjligt att skapa en auktoriseringsregel för att minska tvetydighet.

Auktoriseringsreglerna utvärdera den primära logga in autentiseringsuppgifterna för Windows PowerShell Web Access-användare, inte de alternativa autentiseringsuppgifterna (den andra uppsättningen av autentiseringsuppgifter finns i den **valfria anslutningsinställningar** delen av den på inloggningssidan). Ett exempel på detta finns i exemplet 6.

## <a name="parameters"></a>Parametrar

### <a name="-computergroupname-string"></a>-ComputerGroupName \<sträng\>

Anger namnet på en datorgrupp i Active Directory Domain Services (AD DS) eller lokala grupper som den här regeln beviljar åtkomst.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-computername-string"></a>-ComputerName \<sträng\>

Anger namnet på datorn som den här regeln beviljar åtkomst.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-configurationname-string"></a>-ConfigurationName \<sträng\>

Anger namnet på sessionskonfigurationen för Windows PowerShell, även kallat körningsutrymme, som den här regeln beviljar åtkomst.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-credential--pscredential"></a>-Credential \<PSCredential\>

Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att ändra regler för Windows PowerShell Web Access. Om du inte lägga till den här parametern använder cmdlet: en för tillfället inloggade användarkontot. Att hämta en **PSCredential** -objektet, vilket krävs för att lägga till auktoriseringsregler via fjärranslutning genom att köra den [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-force"></a>-Force

Tvingar kommandot att köras utan att användaren ombeds bekräfta. \
Dessutom kan uppmanas den också att bekräfta när du anger ett enkelt eller korta datornamn (till exempel ett namn som inte är ett domännamn eller inte är fullständigt kvalificerad). Bekräftelse begärs av säkerhetsskäl så att du kan använda enkla namnet för att lägga till en dator endast om datorn är i en arbetsgrupp.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-rulename-string"></a>-RuleName \<sträng\>

Anger det egna namnet för den här regeln.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<sträng\[\]\>

Anger namnet på en eller flera användargrupper i AD DS eller lokala grupper som den här regeln beviljar åtkomst.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-username-string"></a>-UserName \<sträng\[\]\>

Anger en eller flera användare som den här regeln beviljar åtkomst. Användarnamnet kan vara ett lokalt användarkonto på gateway-datorn eller en användare i AD DS.
Formatet är `domain\user` eller `computer\user`.

|||
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | 1                                    |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByValue, ByPropertyName)       |
| Acceptera jokertecken?          | falskt                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

Denna cmdlet har stöd för parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.
Mer information finns i [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>INDATA

### <a name="string"></a>Sträng

Denna cmdlet accepterar en sträng eller en matris med strängar som indata.

### <a name="string"></a>Sträng\[\]

Denna cmdlet accepterar en sträng eller en matris med strängar som indata.

## <a name="outputs"></a>Utdata:

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Denna cmdlet returnerar den ett auktorisering regelobjekt.

## <a name="examples"></a>EXEMPEL

### <a name="example-1"></a>EXEMPEL 1

Det här exemplet tilldelar åtkomst till sessionskonfigurationen _PSWAEndpoint_, ett begränsat körningsutrymme på _srv2_ för användare i den _SMAdmins_ grupp.

> [!NOTE]
> Datornamnet måste vara ett fullständigt kvalificerat domännamn (FQDN). Administratörer definiera ett begränsat sessionskonfiguration eller körningsutrymmen, vilket är ett begränsat antal cmdletar och uppgifter som slutanvändarna kan köras. Definiera ett begränsat körningsutrymme kan förhindra användare från att komma åt andra datorer som inte i den tillåtna Windows PowerShell® körningsutrymmen, vilket ger en säkrare anslutning. Mer information om sessionskonfigurationer finns i [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) eller [installera och använda Windows PowerShell-webbåtkomst](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>EXEMPEL 2

Det här exemplet tilldelar åtkomst till Windows PowerShell-session standardkonfigurationen `Microsoft.PowerShell`på *srv2* för användare i de användare som heter `contoso\user1`, `contoso\user2`, och `contoso\user3`. Denna cmdlet skapar tre regler (1 per person).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>EXEMPEL 3

Det här exemplet illustrerar hur du kan ange värden för användaren via pipelinen.

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>EXEMPEL 4

Det här exemplet illustrerar hur alla parametrar tar värden från pipeline efter egenskapsnamn.

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>EXEMPEL 5

Det här exemplet lägger till en regel som tillåter lokal användare med namnet `PswaServer\ChrisLocal` åtkomst till servern med namnet **srv1.contoso.com**.

Det här exemplet illustrerar ett scenario där gatewayen är i en arbetsgrupp och måldatorn finns i en domän. Regeln gäller för lokala användare på gatewayen. I Windows PowerShell-webbåtkomst på inloggningssidan, för att kunna autentisera användaren måste ange en annan uppsättning autentiseringsuppgifter i den **valfria anslutningsinställningar** området. Gateway-servern använder denna ytterligare uppsättning autentiseringsuppgifter för att autentisera användaren på måldatorn, en server med namnet *srv1.contoso.com*.

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>EXEMPEL 6

Det här exemplet tillåter alla användare åtkomst till alla slutpunkter på alla datorer.
Detta inaktiverar i stort sett regler.

> [!NOTE]
> Användning av den `*` jokertecknet rekommenderas inte för distributioner av känsliga och bör endast för testmiljöer eller används i distributioner där säkerheten minskas.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Se även

[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)

[Lägg till medlem](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[Nytt objekt](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)