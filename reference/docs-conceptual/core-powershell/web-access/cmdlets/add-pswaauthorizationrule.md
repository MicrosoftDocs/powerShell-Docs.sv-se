---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: "Lägg till pswaauthorizationrule"
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 18422f71b2a5f9af07af94e4324d3c7774f1d5ea
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SAMMANFATTNING

Lägger till en ny auktoriseringsregel regeluppsättningen för auktorisering av Windows PowerShell® Web Access.

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

Du måste ange användare, datorer och Windows PowerShell-slutpunkter för den här regeln. Du kan ange både användare och datorer genom enskilda användarkonton och datornamn eller genom att ange grupper.

För en dator som är ansluten till en Active Directory-domän, använder cmdlet säkerhetsidentifierare (SID) för datorn för att skapa regeln.
Detta gör att du kan använda ett kort namn, ett fullständigt kvalificerat domännamn (FQDN) eller en IP-adress för den **datornamn** på sidan logga in.

För en dator som inte är ansluten till en Active Directory-domän, skapar cmdleten regeln med hjälp av namnet på datorn som tillhandahålls av administratören. Om du vill ansluta till den här datorn, måste användaren ange datornamnet exakt som det visas i regeln.

Om det finns flera datorer med samma namn i nätverket kan lösas kort namn till mer än en dator. Detta kan leda till tvetydighet när en anslutning upprättas. Till exempel om det finns en regel för arbetsgruppsdator med namnet ”*Server1*” och en ny dator med namnet *server1.contoso.com* är ansluten till nätverket med hjälp av auktoriseringsregler lyckas och Windows PowerShell Web Access försöker upprätta en anslutning till datorn med namnet ”*Server1*”. Det är inte säkert att ansluta till den angivna arbetsgrupp-datorn. Försök kan göras på arbetsgruppen eller domän datorn med namnet ”*Server1*”. Det rekommenderas att du använder det fullständiga Domännamnet för måldatorn när det är möjligt att skapa en auktoriseringsregel för att undvika tvetydighet.

Auktoriseringsregler utvärdera primära inloggning inloggningsuppgifterna för Windows PowerShell Web Access-användare, inte de alternativa autentiseringsuppgifterna (den andra uppsättningen av autentiseringsuppgifter finns i den **valfria anslutningsinställningar** avsnitt i den inloggningssidan). Ett exempel på detta finns i exempel 6.

## <a name="parameters"></a>Parametrar

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;sträng&gt;

Anger namnet på en datorgrupp i Active Directory Domain Services (AD DS) eller lokala grupper som den här regeln beviljar åtkomst.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;sträng&gt;

Anger namnet på datorn som den här regeln beviljar åtkomst.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;sträng&gt;

Anger namnet på sessionskonfigurationen för Windows PowerShell, även kallat runspace, som den här regeln beviljar åtkomst.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att ändra auktoriseringsregler för Windows PowerShell Web Access. Om du inte lägga till den här parametern används cmdlet det inloggade användarkontot. Få en **PSCredential** -objektet, vilket krävs för att lägga till auktoriseringsregler från en fjärrdator genom att köra den [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-force"></a>-Force

Tvingar kommandot att köras utan bekräftelse från användaren. \
Dessutom kan uppmanas den också att bekräfta när du anger ett enkelt eller kort datornamn (till exempel ett namn som inte är ett domännamn eller är inte fullständigt kvalificerad). Bekräftelse har begärts av säkerhetsskäl så att du kan använda enkla namn till bara lägga till en dator om datorn är i en arbetsgrupp.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | falskt                                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;sträng&gt;

Anger det egna namnet för den här regeln.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | falskt                                |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;sträng\[\]&gt;

Anger namnet på en eller flera användargrupper i AD DS eller grupper som den här regeln beviljar åtkomst.

|||  
|-|-|
| Alias                              | inget                                 |
| Obligatorisk?                            | SANT                                 |
| Placering?                            | Med namnet                                |
| Standardvärde                        | inget                                 |
| Acceptera pipelineindata?               | True (ByPropertyName)                |
| Acceptera jokertecken?          | falskt                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;sträng\[\]&gt;

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

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.
Mer information finns i [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>INDATA

### <a name="string"></a>Sträng

Denna cmdlet accepterar en sträng eller en matris med strängar som indata.

### <a name="string"></a>Sträng\[\]

Denna cmdlet accepterar en sträng eller en matris med strängar som indata.

## <a name="outputs"></a>Utdata:

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Denna cmdlet returnerar den ett authorization-regelobjekt.

## <a name="examples"></a>EXEMPEL

### <a name="example-1"></a>EXEMPEL 1

Det här exemplet ger åtkomst till sessionskonfigurationen *PSWAEndpoint*, ett begränsat körningsutrymme på *srv2* för användare i den *SMAdmins* grupp. \
**Obs**: datornamnet måste vara ett fullständigt kvalificerat domännamn (FQDN). Administratörer definiera en begränsad sessionskonfiguration eller körningsutrymmen, vilket är ett begränsat antal cmdletar och uppgifter som slutanvändarna kan köras. Definiera ett begränsat körningsutrymme kan hindra användare från att komma åt andra datorer som inte i det tillåtna Windows PowerShell® runspace, vilket ger en säker anslutning. Mer information om sessionskonfigurationer finns [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) eller [installera och använda Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>EXEMPEL 2

Det här exemplet ger åtkomst till Windows PowerShell-session standardkonfigurationen `Microsoft.PowerShell`på *srv2* för användare i användare med namnet contoso\\Användare1, contoso\\användare2, och contoso\\user3. Denna cmdlet skapar tre regler (1 per person).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>EXEMPEL 3

Det här exemplet illustrerar hur du indatavärden user name via pipeline.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>EXEMPEL 4

Det här exemplet illustrerar hur alla parametrar tar värden från pipeline genom egenskapsnamn.

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>EXEMPEL 5

Det här exemplet lägger till en regel för att tillåta lokala användare med namnet *PswaServer\\ChrisLocal* åtkomst till servern med namnet *srv1.contoso.com*.

Det här exemplet illustrerar ett scenario där gatewayen är i en arbetsgrupp och måldatorn finns i en domän. Regeln gäller för lokala användare på gateway. På sidan Windows PowerShell Web Access-inloggning för att kunna autentisera användaren måste ange en annan uppsättning autentiseringsuppgifter i den **valfria anslutningsinställningar** område. Gateway-servern använder denna ytterligare uppsättning autentiseringsuppgifter för att autentisera användaren på måldatorn, en server med namnet *srv1.contoso.com*.

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>EXEMPEL 6

Det här exemplet tillåter alla användare åtkomst till alla slutpunkter på alla datorer.
Detta i praktiken inaktiverar auktoriseringsregler. \
**Obs**: användning av den `*` jokertecken rekommenderas inte för känsliga distributioner och bör endast för testmiljöer eller användas i distributioner där säkerhet kan mjukas upp.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Se även

- [Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)
- [Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)
- [Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)
- [Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)
- [Lägg till medlem](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [Nytt objekt](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)
