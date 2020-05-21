---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda konfigurations data
ms.openlocfilehash: 5eb7fedec9a0abece1068496cdf5cb940eae3340
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557047"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="1fb52-103">Använda konfigurations data i DSC</span><span class="sxs-lookup"><span data-stu-id="1fb52-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="1fb52-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="1fb52-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1fb52-105">Med hjälp av den inbyggda DSC **ConfigurationData** -parametern kan du definiera data som kan användas i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="1fb52-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="1fb52-106">På så sätt kan du skapa en enda konfiguration som kan användas för flera noder eller för olika miljöer.</span><span class="sxs-lookup"><span data-stu-id="1fb52-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="1fb52-107">Om du till exempel utvecklar ett program kan du använda en konfiguration för både utvecklings-och produktions miljöer och använda konfigurations data för att ange data för varje miljö.</span><span class="sxs-lookup"><span data-stu-id="1fb52-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="1fb52-108">I det här avsnittet beskrivs strukturen för **ConfigurationData** -hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="1fb52-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="1fb52-109">Exempel på hur du använder konfigurations data finns i [avgränsa konfigurations-och miljö data](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="1fb52-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="1fb52-110">Den gemensamma ConfigurationData-parametern</span><span class="sxs-lookup"><span data-stu-id="1fb52-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="1fb52-111">En DSC-konfiguration använder en gemensam parameter, **ConfigurationData**, som du anger när du kompilerar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="1fb52-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="1fb52-112">Information om hur du kompilerar konfigurationer finns i [DSC-konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="1fb52-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="1fb52-113">Parametern **ConfigurationData** är en hash som måste ha minst en nyckel med namnet **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="1fb52-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="1fb52-114">Den kan också ha en eller flera andra nycklar.</span><span class="sxs-lookup"><span data-stu-id="1fb52-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="1fb52-115">I exemplen i det här avsnittet används en enda ytterligare nyckel (förutom den namngivna **AllNodes** -nyckeln) med namnet `NonNodeData` , men du kan ta med valfritt antal ytterligare nycklar och ge dem de namn du vill.</span><span class="sxs-lookup"><span data-stu-id="1fb52-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="1fb52-116">Värdet för **AllNodes** -nyckeln är en matris.</span><span class="sxs-lookup"><span data-stu-id="1fb52-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="1fb52-117">Varje element i matrisen är också en hash-tabell som måste ha minst en nyckel med namnet **nodnamn**:</span><span class="sxs-lookup"><span data-stu-id="1fb52-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="1fb52-118">Du kan också lägga till andra nycklar till varje hash-tabell:</span><span class="sxs-lookup"><span data-stu-id="1fb52-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="1fb52-119">Om du vill tillämpa en egenskap på alla noder kan du skapa en medlem i **AllNodes** -matrisen som har en **nodnamn** av `*` .</span><span class="sxs-lookup"><span data-stu-id="1fb52-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="1fb52-120">Om du till exempel vill ge varje nod en `LogPath` egenskap kan du göra följande:</span><span class="sxs-lookup"><span data-stu-id="1fb52-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="1fb52-121">Detta är detsamma som att lägga till en egenskap med namnet `LogPath` med ett värde för `"C:\Logs"` varje av de andra blocken ( `VM-1` , `VM-2` och `VM-3` ).</span><span class="sxs-lookup"><span data-stu-id="1fb52-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="1fb52-122">Definiera ConfigurationData-hash</span><span class="sxs-lookup"><span data-stu-id="1fb52-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="1fb52-123">Du kan definiera **ConfigurationData** antingen som en variabel i samma skript fil som en konfiguration (som i våra tidigare exempel) eller i en separat `.psd1` fil.</span><span class="sxs-lookup"><span data-stu-id="1fb52-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="1fb52-124">Om du vill definiera **ConfigurationData** i en `.psd1` fil skapar du en fil som bara innehåller den hash som representerar konfigurations data.</span><span class="sxs-lookup"><span data-stu-id="1fb52-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="1fb52-125">Du kan till exempel skapa en fil med namnet `MyData.psd1` med följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="1fb52-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="1fb52-126">Kompilera en konfiguration med konfigurations data</span><span class="sxs-lookup"><span data-stu-id="1fb52-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="1fb52-127">Om du vill kompilera en konfiguration för vilken du har definierat konfigurations data skickar du konfigurations data som värdet för parametern **ConfigurationData** .</span><span class="sxs-lookup"><span data-stu-id="1fb52-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="1fb52-128">Då skapas en MOF-fil för varje post i **AllNodes** -matrisen.</span><span class="sxs-lookup"><span data-stu-id="1fb52-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="1fb52-129">Varje MOF-fil får namnet med `NodeName` egenskapen för motsvarande mat ris post.</span><span class="sxs-lookup"><span data-stu-id="1fb52-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="1fb52-130">Om du till exempel definierar konfigurations data som i `MyData.psd1` filen ovan skapas både och filer när du kompilerar en konfiguration `VM-1.mof` `VM-2.mof` .</span><span class="sxs-lookup"><span data-stu-id="1fb52-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="1fb52-131">Kompilera en konfiguration med konfigurations data med en variabel</span><span class="sxs-lookup"><span data-stu-id="1fb52-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="1fb52-132">Om du vill använda konfigurations data som har definierats som en variabel i samma `.ps1` fil som konfigurationen skickar du variabel namnet som värde för parametern **ConfigurationData** när du kompilerar konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="1fb52-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="1fb52-133">Kompilera en konfiguration med konfigurations data med hjälp av en datafil</span><span class="sxs-lookup"><span data-stu-id="1fb52-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="1fb52-134">Om du vill använda konfigurations data som har definierats i en. psd1-fil skickar du sökvägen och namnet på filen som värdet för parametern **ConfigurationData** när du kompilerar konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="1fb52-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="1fb52-135">Använda ConfigurationData-variabler i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="1fb52-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="1fb52-136">DSC tillhandahåller följande särskilda variabler som kan användas i ett konfigurations skript:</span><span class="sxs-lookup"><span data-stu-id="1fb52-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="1fb52-137">**$AllNodes** refererar till hela samlingen av noder som definierats i **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="1fb52-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="1fb52-138">Du kan filtrera **AllNodes** -samlingen med hjälp av **. Där ()** och **. ()**.</span><span class="sxs-lookup"><span data-stu-id="1fb52-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="1fb52-139">**ConfigurationData** refererar till hela hash-tabellen som skickas som parameter när en konfiguration kompileras.</span><span class="sxs-lookup"><span data-stu-id="1fb52-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="1fb52-140">**TypeName** innehåller [konfigurations](configurations.md) namnet som variabeln används i.</span><span class="sxs-lookup"><span data-stu-id="1fb52-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="1fb52-141">I-konfigurationen har till exempel `MyDscConfiguration` `$MyTypeName` värdet `MyDscConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1fb52-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="1fb52-142">**Node** refererar till en viss post i **AllNodes** -samlingen när den filtreras med hjälp av **. Där ()** eller **. ()**.</span><span class="sxs-lookup"><span data-stu-id="1fb52-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="1fb52-143">Du kan läsa mer om de här metoderna i [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span><span class="sxs-lookup"><span data-stu-id="1fb52-143">You can read more about these methods in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="1fb52-144">Använda data som inte är noder</span><span class="sxs-lookup"><span data-stu-id="1fb52-144">Using non-node data</span></span>

<span data-ttu-id="1fb52-145">Som vi har sett i föregående exempel kan **ConfigurationData** hash-tabellen ha en eller flera nycklar utöver den nödvändiga **AllNodes** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="1fb52-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="1fb52-146">I exemplen i det här avsnittet har vi bara använt en enda nod och namngett den `NonNodeData` .</span><span class="sxs-lookup"><span data-stu-id="1fb52-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="1fb52-147">Du kan dock definiera valfritt antal ytterligare nycklar och ge dem namn som du vill.</span><span class="sxs-lookup"><span data-stu-id="1fb52-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="1fb52-148">Ett exempel på hur du använder data som inte finns på en nod finns i [avgränsa konfigurations-och miljö data](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="1fb52-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1fb52-149">Se även</span><span class="sxs-lookup"><span data-stu-id="1fb52-149">See Also</span></span>

- [<span data-ttu-id="1fb52-150">Alternativ för autentiseringsuppgifter i konfigurations data</span><span class="sxs-lookup"><span data-stu-id="1fb52-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="1fb52-151">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="1fb52-151">DSC Configurations</span></span>](configurations.md)
