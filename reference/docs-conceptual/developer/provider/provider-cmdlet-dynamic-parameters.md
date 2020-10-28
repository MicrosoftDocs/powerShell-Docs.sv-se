---
ms.date: 09/13/2016
ms.topic: reference
title: Dynamiska cmdlet-parametrar för providers
description: Dynamiska cmdlet-parametrar för providers
ms.openlocfilehash: ac05a847afb0729c34d733fa4ba8da11f46746fe
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662981"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Dynamiska cmdlet-parametrar för providers

Leverantörer kan definiera dynamiska parametrar som läggs till i en providers-cmdlet när användaren anger ett visst värde för en av de statiska parametrarna för cmdleten. En provider kan till exempel lägga till olika dynamiska parametrar baserat på vilken sökväg användaren anger när de anropar- `Get-Item` eller- `Set-Item` Provider-cmdletarna.

## <a name="dynamic-parameter-methods"></a>Dynamiska parameter metoder

Dynamiska parametrar definieras genom att implementera en av de dynamiska parameter metoderna, till exempel [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) och [system. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s metoder. Dessa metoder returnerar ett objekt som har offentliga egenskaper som innehåller attribut som liknar dem i fristående cmdlets. Här är ett exempel på en implementering av metoden [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) som tas från certifikat leverantören:

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

`Clear-Content` cmdlet du kan definiera dynamiska parametrar som utlöses av `Path` parametern för Clear-Clear cmdlet genom att implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

`Clear-Item` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` parametern genom att `Clear-Item` implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

`Clear-ItemProperty` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` parametern genom att `Clear-ItemProperty` implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

`Copy-Item` cmdlet kan du definiera dynamiska parametrar som utlöses av `Path` `Destination` parametrarna, och `Recurse` för `Copy-Item` cmdleten genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

Get-ChildItems cmdleten kan du definiera dynamiska parametrar som utlöses av `Path` cmdlet- `Recurse` parametrarna och, `Get-ChildItem` genom att implementera parametrarna [system. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) och [system. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) .

`Get-Content` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` parametern genom att `Get-Content` implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) .

`Get-Item` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` parametern genom att `Get-Item` implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

`Get-ItemProperty` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` `Name` parametrarna och genom att `Get-ItemProperty` implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

`Invoke-Item` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` parametern genom att `Invoke-Item` implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

`Move-Item` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` `Destination` parametrarna och genom att `Move-Item` implementera metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) .

`New-Item` cmdlet kan du definiera dynamiska parametrar som utlöses av `Path` `ItemType` parametrarna, och `Value` för `New-Item` cmdleten genom att implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) .

`New-ItemProperty` cmdlet kan du definiera dynamiska parametrar som utlöses av `Path` `Name` cmdleten,, `PropertyType` och `Value` för `New-ItemProperty` cmdleten genom att implementera metoden [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

`New-PSDrive` cmdlet kan du definiera dynamiska parametrar som utlöses av [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -objektet som returneras av `New-PSDrive` cmdleten genom att implementera metoden [system. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

`Remove-Item` Du kan definiera dynamiska parametrar som utlöses av cmdlet- `Path` `Recurse` parametrarna och genom att `Remove-Item` implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

`Remove-ItemProperty` Du kan definiera dynamiska parametrar som utlöses av cmdlet- `Path` `Name` parametrarna och genom att `Remove-ItemProperty` implementera metoden [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

`Rename-Item` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` `NewName` parametrarna och genom att `Rename-Item` implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

`Rename-ItemProperty` Du kan definiera dynamiska parametrar som utlöses av `Path` `Name` parametrarna, och `NewName` för `Rename-ItemProperty` cmdleten genom att implementera metoden [system. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

`Set-Content` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` parametern genom att `Set-Content` implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) .

`Set-Item` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` `Value` parametrarna och genom att `Set-Item` implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

`Set-ItemProperty` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` `Value` parametrarna och genom att `Set-Item` implementera metoden [system. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

`Test-Path` cmdlet kan du definiera dynamiska parametrar som utlöses av cmdlet- `Path` parametern genom att `Test-Path` implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-provider](./writing-a-windows-powershell-provider.md)
