# Site Slot App Settings `[Microsoft.Web/sites/slots/config]`

This module deploys a Site Slot App Setting.

## Navigation

- [Resource Types](#Resource-Types)
- [Parameters](#Parameters)
- [Outputs](#Outputs)
- [Cross-referenced modules](#Cross-referenced-modules)

## Resource Types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Web/sites/slots/config` | [2022-09-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Web/sites) |

## Parameters

**Required parameters**

| Parameter Name | Type | Allowed Values | Description |
| :-- | :-- | :-- | :-- |
| `kind` | string | `[app, functionapp, functionapp,linux, functionapp,workflowapp, functionapp,workflowapp,linux]` | Type of slot to deploy. |
| `slotName` | string |  | Slot name to be configured. |

**Conditional parameters**

| Parameter Name | Type | Description |
| :-- | :-- | :-- |
| `appName` | string | The name of the parent site resource. Required if the template is used in a standalone deployment. |

**Optional parameters**

| Parameter Name | Type | Default Value | Description |
| :-- | :-- | :-- | :-- |
| `appInsightResourceId` | string | `''` | Resource ID of the app insight to leverage for this resource. |
| `appSettingsKeyValuePairs` | object | `{object}` | The app settings key-value pairs except for AzureWebJobsStorage, AzureWebJobsDashboard, APPINSIGHTS_INSTRUMENTATIONKEY and APPLICATIONINSIGHTS_CONNECTION_STRING. |
| `enableDefaultTelemetry` | bool | `True` | Enable telemetry via the Customer Usage Attribution ID (GUID). |
| `setAzureWebJobsDashboard` | bool | `[if(contains(parameters('kind'), 'functionapp'), true(), false())]` | For function apps. If true the app settings "AzureWebJobsDashboard" will be set. If false not. In case you use Application Insights it can make sense to not set it for performance reasons. |
| `storageAccountResourceId` | string | `''` | Required if app of kind functionapp. Resource ID of the storage account to manage triggers and logging function executions. |


### Parameter Usage: `appSettingsKeyValuePairs`

AzureWebJobsStorage, AzureWebJobsDashboard, APPINSIGHTS_INSTRUMENTATIONKEY and APPLICATIONINSIGHTS_CONNECTION_STRING are set separately (check parameters storageAccountId, setAzureWebJobsDashboard, appInsightId).
For all other app settings key-value pairs use this object.

<details>

<summary>Parameter JSON format</summary>

```json
"appSettingsKeyValuePairs": {
    "value": [
        {
            "name": "key1",
            "value": "val1"
        },
        {
            "name": "key2",
            "value": "val2"
        }
    ]
}
```

</details>

<details>

<summary>Bicep format</summary>

```bicep
appSettingsKeyValuePairs: [
    {
        name: 'key1'
        value: 'val1'
    }
    {
        name: 'key2'
        value: 'val2'
    }
]
```

</details>
<p>

## Outputs

| Output Name | Type | Description |
| :-- | :-- | :-- |
| `name` | string | The name of the slot config. |
| `resourceGroupName` | string | The resource group the slot config was deployed into. |
| `resourceId` | string | The resource ID of the slot config. |

## Cross-referenced modules

_None_
