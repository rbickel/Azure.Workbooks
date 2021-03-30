```json
{
  "version": "Notebook/1.0",
  "items": [
    {
      "type": 9,
      "content": {
        "version": "KqlParameterItem/1.0",
        "crossComponentResources": [
          "value::all"
        ],
        "parameters": [
          {
            "id": "c51741d7-5c82-457b-a658-d072a9a8aa0e",
            "version": "KqlParameterItem/1.0",
            "name": "Databases",
            "label": "DTU Databases",
            "type": 5,
            "description": "Standard and Premium DTU databases",
            "isRequired": true,
            "multiSelect": true,
            "quote": "'",
            "delimiter": ",",
            "query": "\r\nwhere type =~ 'microsoft.sql/servers/databases'\r\n| where properties.currentSku.name in ('Standard', 'Premium')\r\n| project id, name\r\n| order by name desc",
            "crossComponentResources": [
              "value::all"
            ],
            "value": [
              "value::all"
            ],
            "typeSettings": {
              "resourceTypeFilter": {
                "microsoft.sql/servers/databases": true
              },
              "additionalResourceOptions": [
                "value::all"
              ],
              "showDefault": false
            },
            "timeContext": {
              "durationMs": 86400000
            },
            "queryType": 1,
            "resourceType": "microsoft.resourcegraph/resources"
          },
          {
            "id": "12df6d2a-696d-4cd8-a384-5fca8efb5ae8",
            "version": "KqlParameterItem/1.0",
            "name": "Duration",
            "type": 4,
            "isRequired": true,
            "value": {
              "durationMs": 172800000
            },
            "typeSettings": {
              "selectableValues": [
                {
                  "durationMs": 86400000
                },
                {
                  "durationMs": 172800000
                },
                {
                  "durationMs": 259200000
                },
                {
                  "durationMs": 604800000
                },
                {
                  "durationMs": 1209600000
                }
              ]
            },
            "timeContext": {
              "durationMs": 86400000
            }
          }
        ],
        "style": "pills",
        "queryType": 1,
        "resourceType": "microsoft.resourcegraph/resources"
      },
      "name": "parameters - 1"
    },
    {
      "type": 10,
      "content": {
        "chartId": "workbookd65dc4fa-8f86-4cf1-a978-ef6659aed155",
        "version": "MetricsItem/2.0",
        "size": 0,
        "chartType": 0,
        "resourceType": "microsoft.sql/servers/databases",
        "metricScope": 0,
        "resourceParameter": "Databases",
        "resourceIds": [
          "{Databases}"
        ],
        "timeContextFromParameter": "Duration",
        "timeContext": {
          "durationMs": 0
        },
        "metrics": [
          {
            "namespace": "microsoft.sql/servers/databases",
            "metric": "microsoft.sql/servers/databases-Basic-dtu_used",
            "aggregation": 3,
            "columnName": "Max DTU"
          },
          {
            "namespace": "microsoft.sql/servers/databases",
            "metric": "microsoft.sql/servers/databases-Basic-dtu_used",
            "aggregation": 4,
            "columnName": "Average DTU"
          },
          {
            "namespace": "microsoft.sql/servers/databases",
            "metric": "microsoft.sql/servers/databases-Basic-dtu_limit",
            "aggregation": 3,
            "columnName": "Max Limit DTU"
          }
        ],
        "gridSettings": {
          "formatters": [
            {
              "columnMatch": "Subscription",
              "formatter": 5
            },
            {
              "columnMatch": "Name",
              "formatter": 13,
              "formatOptions": {
                "linkTarget": "Resource"
              }
            },
            {
              "columnMatch": "microsoft.sql/servers/databases-Basic-dtu_used Timeline",
              "formatter": 5
            },
            {
              "columnMatch": "microsoft.sql/servers/databases-Basic-dtu_limit Timeline",
              "formatter": 5
            },
            {
              "columnMatch": "microsoft.sql/servers/databases-Basic-dtu_limit",
              "formatter": 1,
              "numberFormat": {
                "unit": 0,
                "options": null
              }
            },
            {
              "columnMatch": "microsoft.sql/servers/databases-Basic-dtu_used",
              "formatter": 1,
              "numberFormat": {
                "unit": 0,
                "options": null
              }
            },
            {
              "columnMatch": "Max DTU Timeline",
              "formatter": 5
            },
            {
              "columnMatch": "Average DTU Timeline",
              "formatter": 5
            },
            {
              "columnMatch": "Limit DTU Timeline",
              "formatter": 5
            }
          ],
          "rowLimit": 10000
        }
      },
      "name": "metric - 1"
    }
  ],
  "fallbackResourceIds": [
    "Azure Monitor"
  ],
  "$schema": "https://github.com/Microsoft/Application-Insights-Workbooks/blob/master/schema/workbook.json"
}

```