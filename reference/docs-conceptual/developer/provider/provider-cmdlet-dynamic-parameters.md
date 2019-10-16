---
title: Dynamiska parametrar för provider-cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352383"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Dynamiska cmdlet-parametrar för providers

Leverantörer kan definiera dynamiska parametrar som läggs till i en providers-cmdlet när användaren anger ett visst värde för en av de statiska parametrarna för cmdleten. En provider kan till exempel lägga till olika dynamiska parametrar baserat på vilken sökväg användaren anger när de anropar cmdletarna `Get-Item` eller `Set-Item`-Provider.

## <a name="dynamic-parameter-methods"></a>Dynamiska parameter metoder

Dynamiska parametrar definieras genom att implementera en av de dynamiska parameter metoderna, till exempel [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) och [ Metoderna system. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s. Dessa metoder returnerar ett objekt som har offentliga egenskaper som innehåller attribut som liknar dem i fristående cmdlets. Här är ett exempel på en implementering av metoden [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) som tas från certifikat leverantören:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Till skillnad från de statiska parametrarna för provider-cmdletar kan du ange egenskaperna för dessa parametrar på samma sätt som parametrarna definieras i fristående cmdlets. Här är ett exempel på en dynamisk parameter klass som tas från certifikat leverantören:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Här är en lista över de statiska parametrar som kan användas för att lägga till dynamiska parametrar.

`Clear-Content`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametern `Path` för cmdleten Clear-Clear genom att implementera [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) metodsignatur.

`Clear-Item`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametern `Path` för cmdleten `Clear-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

`Clear-ItemProperty`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametern `Path` för cmdleten `Clear-ItemProperty` genom att implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

`Copy-Item`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path`, `Destination` och `Recurse` i `Copy-Item`-cmdleten genom att implementera [ Metoden system. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

Get-ChildItems-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path` och `Recurse` för cmdleten `Get-ChildItem` genom att implementera [ System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) och [system. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metoder.

`Get-Content`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametern `Path` för cmdleten `Get-Content` genom att implementera [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metodsignatur.

`Get-Item`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametern `Path` för cmdleten `Get-Item` genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

`Get-ItemProperty`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path` och `Name` för cmdleten `Get-ItemProperty` genom att implementera [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters * ](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)metoden.

`Invoke-Item`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametern `Path` för cmdleten `Invoke-Item` genom att implementera [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) metodsignatur.

`Move-Item`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path` och `Destination` för cmdleten `Move-Item` genom att implementera [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters * ](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)metoden.

`New-Item`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path`, `ItemType` och `Value` i `New-Item`-cmdleten genom att implementera [ Metoden system. Management. Automation. Provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) .

`New-ItemProperty`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path`, `Name`, `PropertyType` och `Value` i cmdleten `New-ItemProperty` genom att implementera [ Metoden system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

`New-PSDrive`-cmdlet kan du definiera dynamiska parametrar som utlöses av objektet [system. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) som returnerades av `New-PSDrive`-cmdleten genom att implementera [ Metoden system. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

`Remove-Item` du kan definiera dynamiska parametrar som utlöses av `Path`-och `Recurse`-parametrarna i `Remove-Item`-cmdleten genom att implementera [system. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metodsignatur.

`Remove-ItemProperty` du kan definiera dynamiska parametrar som utlöses av `Path`-och `Name`-parametrarna i `Remove-ItemProperty`-cmdleten genom att [implementera Metoden system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

`Rename-Item`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path` och `NewName` för cmdleten `Rename-Item` genom att implementera [system. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters * ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)metoden.

`Rename-ItemProperty` du kan definiera dynamiska parametrar som utlöses av parametrarna `Path`, `Name` och `NewName` i `Rename-ItemProperty`-cmdleten genom att implementera [ Metoden system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

`Set-Content`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametern `Path` för cmdleten `Set-Content` genom att implementera [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metodsignatur.

`Set-Item`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path` och `Value` för cmdleten `Set-Item` genom att implementera [system. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metodsignatur.

`Set-ItemProperty`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametrarna `Path` och `Value` för cmdleten `Set-Item` genom att implementera [system. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters * ](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)metoden.

`Test-Path`-cmdlet du kan definiera dynamiska parametrar som utlöses av parametern `Path` för cmdleten `Test-Path` genom att implementera [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) metodsignatur.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)