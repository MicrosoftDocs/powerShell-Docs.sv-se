---
title: Dynamiska parametrar för providern cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080976"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Dynamiska cmdlet-parametrar för providers

Leverantörer kan definiera dynamiska parametrar som läggs till en provider-cmdlet när användaren anger ett visst värde för en statisk parametrarna för cmdleten. Till exempel en provider kan lägga till olika dynamiska parametrar, baserat på vilken sökväg användaren anger när de anropar den `Get-Item` eller `Set-Item` cmdlets provider.

## <a name="dynamic-parameter-methods"></a>Dynamisk Parameter-metoder

Dynamiska parametrar definieras genom att implementera en dynamisk parameter-metoder, till exempel den [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) och [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s metoder. Dessa metoder returnerar ett objekt som har offentliga egenskaper som dekorerad med attribut som liknar fristående cmdletar. Här är ett exempel på en implementering av den [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metod som kommer från certifikatleverantör:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Du kan ange egenskaperna för dessa parametrar på samma sätt som att parametrar definieras i fristående cmdlet: ar till skillnad från statisk parametrarna för cmdlets provider. Här är ett exempel på en dynamisk parameter-klass som kommer från certifikatleverantör:

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

`Clear-Content` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` parametern för cmdlet Clear-Rensa genom att implementera den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) metod.

`Clear-Item` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` -parametern för den `Clear-Item` cmdlet genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metod.

`Clear-ItemProperty` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` -parametern för den `Clear-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metod.

`Copy-Item` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path`, `Destination`, och `Recurse` parametrarna för den `Copy-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metod.

Get-ChildItems cmdlet som du kan definiera dynamiska parametrar som utlöses av den `Path` och `Recurse` parametrarna för den `Get-ChildItem` cmdlet genom att implementera den [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) och [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metoder.

`Get-Content` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` -parametern för den `Get-Content` cmdlet genom att implementera den [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metod.

`Get-Item` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` -parametern för den `Get-Item` cmdlet genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metod.

`Get-ItemProperty` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` och `Name` parametrarna för den `Get-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) metod.

`Invoke-Item` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` -parametern för den `Invoke-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) metod.

`Move-Item` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` och `Destination` parametrarna för den `Move-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) metod.

`New-Item` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path`, `ItemType`, och `Value` parametrarna för den `New-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) metod.

`New-ItemProperty` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path`, `Name`, `PropertyType`, och `Value` parametrarna för den `New-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) metod.

`New-PSDrive` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objektet som returneras av den `New-PSDrive` cmdlet genom att implementera den [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metod.

`Remove-Item` Du kan definiera dynamiska parametrar som utlöses av den `Path` och `Recurse` parametrarna för den `Remove-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metod.

`Remove-ItemProperty` Du kan definiera dynamiska parametrar som utlöses av den `Path` och `Name` parametrarna för den `Remove-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) metod.

`Rename-Item` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` och `NewName` parametrarna för den `Rename-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metod.

`Rename-ItemProperty` Du kan definiera dynamiska parametrar som utlöses av den `Path`, `Name`, och `NewName` parametrarna för den `Rename-ItemProperty` cmdlet genom att implementera den [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) metod.

`Set-Content` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` -parametern för den `Set-Content` cmdlet genom att implementera den [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metod.

`Set-Item` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` och `Value` parametrarna för den `Set-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metod.

`Set-ItemProperty` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` och `Value` parametrarna för den `Set-Item` cmdlet genom att implementera den [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) metod.

`Test-Path` cmdlet: en som du kan definiera dynamiska parametrar som utlöses av den `Path` -parametern för den `Test-Path` cmdlet genom att implementera den [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) metod.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-providern](./writing-a-windows-powershell-provider.md)