# 3-Line LineGraph
a template for Actual, Forecast, Allocation

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "usermeta": {
    "deneb": {
      "build": "1.1.0.0",
      "metaVersion": 1,
      "provider": "vegaLite",
      "providerVersion": "5.2.0"
    },
    "interactivity": {
      "tooltip": true,
      "contextMenu": true,
      "selection": true,
      "dataPointLimit": 50
    },
    "information": {
      "name": "3-line Actual vs Forecast vs Budget",
      "description": "[No Description Provided]",
      "author": "PBIQueryous",
      "uuid": "a5214d46-f1be-4ec7-ab11-d56ee77c12d3",
      "generated": "2022-02-09T21:06:57.846Z"
    },
    "dataset": [
      {
        "key": "__0__",
        "name": "Fiscal Year",
        "description": "Date axis",
        "type": "text",
        "kind": "column",
        "namePlaceholder": "Fiscal Year"
      },
      {
        "key": "__1__",
        "name": "Funding Stream",
        "description": "Series (optional)",
        "type": "text",
        "kind": "column",
        "namePlaceholder": "Funding Stream"
      },
      {
        "key": "__2__",
        "name": "£ In Delivery | Total",
        "description": "Allocation",
        "type": "numeric",
        "kind": "measure",
        "namePlaceholder": "£ In Delivery | Total"
      },
      {
        "key": "__3__",
        "name": "£ In Delivery | Spent",
        "description": "Actual",
        "type": "numeric",
        "kind": "measure",
        "namePlaceholder": "£ In Delivery | Spent"
      },
      {
        "key": "__4__",
        "name": "£ In Delivery | Unspent",
        "description": "Forecast",
        "type": "numeric",
        "kind": "measure",
        "namePlaceholder": "£ In Delivery | Unspent"
      }
    ]
  },
  "config": {
    "autosize": {
      "type": "fit",
      "contains": "padding"
    },
    "view": {"stroke": "transparent"},
    "font": "Segoe UI",
    "arc": {},
    "area": {
      "line": true,
      "opacity": 0.6
    },
    "bar": {},
    "line": {
      "strokeWidth": 3,
      "strokeCap": "round",
      "strokeJoin": "round"
    },
    "path": {},
    "point": {
      "filled": true,
      "size": 75
    },
    "rect": {},
    "shape": {},
    "symbol": {
      "strokeWidth": 1,
      "size": 50
    },
    "text": {
      "font": "Segoe UI",
      "fontSize": 12,
      "fill": "#605E5C"
    },
    "axis": {
      "ticks": false,
      "grid": false,
      "domain": false,
      "labelColor": "#605E5C",
      "labelFontSize": 12,
      "titleFont": "wf_standard-font, helvetica, arial, sans-serif",
      "titleColor": "#252423",
      "titleFontSize": 16,
      "titleFontWeight": "normal"
    },
    "axisQuantitative": {
      "tickCount": 3,
      "grid": true,
      "gridColor": "#C8C6C4",
      "gridDash": [1, 5],
      "labelFlush": false
    },
    "axisBand": {"tickExtra": true},
    "axisX": {"labelPadding": 5},
    "axisY": {"labelPadding": 10},
    "header": {
      "titleFont": "wf_standard-font, helvetica, arial, sans-serif",
      "titleFontSize": 16,
      "titleColor": "#252423",
      "labelFont": "Segoe UI",
      "labelFontSize": 13.333333333333332,
      "labelColor": "#605E5C"
    },
    "legend": {
      "titleFont": "Segoe UI",
      "titleFontWeight": "bold",
      "titleColor": "#605E5C",
      "labelFont": "Segoe UI",
      "labelFontSize": 13.333333333333332,
      "labelColor": "#605E5C",
      "symbolType": "circle",
      "symbolSize": 75
    }
  },
  "data": {"name": "dataset"},
  "layer": [
    {
      "mark": {
        "type": "line",
        "interpolate": "catmull-rom",
        "point": false,
        "color": "darkgrey",
        "strokeWidth": 1
      },
      "encoding": {
        "x": {
          "field": "__0__",
          "type": "nominal",
          "axis": null
        },
        "y": {
          "field": "__2__",
          "aggregate": "sum",
          "type": "quantitative",
          "axis": null
        }
      }
    },
    {
      "mark": {
        "type": "line",
        "point": false,
        "color": "blue",
        "interpolate": "catmull-rom",
        "strokeWidth": 1
      },
      "encoding": {
        "x": {
          "field": "__0__",
          "type": "nominal",
          "axis": null
        },
        "y": {
          "field": "__3__",
          "aggregate": "sum",
          "type": "quantitative",
          "axis": null
        }
      }
    },
    {
      "mark": {
        "type": "line",
        "point": false,
        "color": "teal",
        "interpolate": "catmull-rom",
        "strokeWidth": 1
      },
      "encoding": {
        "x": {
          "field": "__0__",
          "type": "nominal",
          "axis": null
        },
        "y": {
          "field": "__4__",
          "aggregate": "sum",
          "type": "quantitative",
          "axis": null
        }
      }
    }
  ]
}
```
