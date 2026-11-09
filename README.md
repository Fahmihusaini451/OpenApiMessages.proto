
{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 0,
  "id": null,
  "links": [],
  "liveNow": false,
  "panels": [
    {
      "collapsed": false,
      "gridPos": {
        "h": 4,
        "w": 24,
        "x": 0,
        "y": 0
      },
      "id": 1,
      "title": "Crypto Portfolio Overview",
      "type": "row"
    },
    {
      "datasource": {
        "type": "prometheus",
        "uid": "prometheus"
      },
      "fieldConfig": {
        "defaults": {
          "color": {
            "mode": "thresholds"
          },
          "mappings": [],
          "thresholds": {
            "mode": "absolute",
            "steps": [
              {
                "color": "green",
                "value": null
              }
            ]
          },
          "unit": "currencyUSD"
        },
        "overrides": []
      },
      "gridPos": {
        "h": 6,
        "w": 8,
        "x": 0,
        "y": 4
      },
      "id": 2,
      "options": {
        "colorMode": "value",
        "graphMode": "area",
        "justifyMode": "center",
        "orientation": "auto",
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "textMode": "auto"
      },
      "pluginVersion": "10.0.0",
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "prometheus"
          },
          "editorMode": "code",
          "expr": "portfolio_current_value_usd",
          "legendFormat": "Total Value",
          "range": true,
          "refId": "A"
        }
      ],
      "title": "Total Portfolio Value (USD)",
      "type": "stat"
    },
    {
      "datasource": {
        "type": "prometheus",
        "uid": "prometheus"
      },
      "fieldConfig": {
        "defaults": {
          "color": {
            "mode": "palette-classic"
          },
          "custom": {
            "hideFrom": {
              "legend": false,
              "tooltip": false,
              "viz": false
            }
          },
          "mappings": []
        },
        "overrides": []
      },
      "gridPos": {
        "h": 6,
        "w": 16,
        "x": 8,
        "y": 4
      },
      "id": 3,
      "options": {
        "displayLabels": [
          "percent",
          "value"
        ],
        "legend": {
          "displayMode": "list",
          "placement": "right",
          "showLegend": true
        },
        "pieType": "donut",
        "reduceOptions": {
          "calcs": [
            "lastNotNull"
          ],
          "fields": "",
          "values": false
        },
        "tooltip": {
          "mode": "single",
          "sort": "none"
        }
      },
      "pluginVersion": "10.0.0",
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "prometheus"
          },
          "editorMode": "code",
          "expr": "crypto_asset_value_usd > 0",
          "legendFormat": "{{symbol}}",
          "range": true,
          "refId": "A"
        }
      ],
      "title": "Asset Allocation",
      "type": "piechart"
    },
    {
      "collapsed": false,
      "gridPos": {
        "h": 4,
        "w": 24,
        "x": 0,
        "y": 10
      },
      "id": 4,
      "title": "System Performance & Messaging Queue",
      "type": "row"
    },
    {
      "datasource": {
        "type": "prometheus",
        "uid": "prometheus"
      },
      "fieldConfig": {
        "defaults": {
          "custom": {
            "drawStyle": "line",
            "lineInterpolation": "smooth"
          },
          "unit": "events/sec"
        }
      },
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 0,
        "y": 14
      },
      "id": 5,
      "targets": [
        {
          "expr": "rate(wallet_events_processed_total[1m])",
          "legendFormat": "Processing Speed",
          "refId": "A"
        }
      ],
      "title": "Balance Update Processing Rate",
      "type": "timeseries"
    },
    {
      "datasource": {
        "type": "prometheus",
        "uid": "prometheus"
      },
      "fieldConfig": {
        "defaults": {
          "custom": {
            "drawStyle": "line"
          },
          "unit": "short"
        }
      },
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 12,
        "y": 14
      },
      "id": 6,
      "targets": [
        {
          "expr": "kafka_consumergroup_lag{topic=\"wallet-balance-updates\"}",
          "legendFormat": "Messages Behind",
          "refId": "A"
        }
      ],
      "title": "Kafka Consumer Group Lag",
      "type": "timeseries"
    }
  ],
  "refresh": "5s",
  "schemaVersion": 38,
  "style": "dark",
  "tags": ["crypto", "husainiexchange"],
  "time": {
    "from": "now-1h",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "Husainiexchange - Portfolio & Infrastructure",
  "version": 1
}
