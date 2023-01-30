```jsonc
{
  "data": {"name": "dataset"},
  "params": [
    {"name": "bwActual", "value": 0.9},
    {"name": "bwBudget", "value": 0.6}
  ],
  "description": "formattingTransforms",
  "transform": [
   
    {
      
      "calculate": "datum.Sales >= datum.Budget",
      "as": "Pos"
    },
    {
      "calculate": "datum.Pos ? '#83C798' : '#8D1D1C'",
      "as": "DeltaColour"
    },
    {
      "calculate": "datum.Pos ? 0 : 11",
      "as": "newDeltaPos"
    },
    {
      "calculate": "datum.Pos ? 'bottom' : 'top'",
      "as": "ActualLabel"
    },
    {
      "calculate": "datum.Pos ? 'black' : 'white'",
      "as": "LabelColour"
    },
    {
      "description": "LabelTextPadding",
      "calculate": "datum.Pos ? -2 : 3",
      "as": "LabelPad"
    },
    {
      "description": "DeltaTextPadding",
      "calculate": "datum.Pos ? -3 : 3",
      "as": "DeltaPad"
    },
    {
      "calculate": "round(datum.Sales - datum.Budget)",
      "as": "DeltaText"
    },
    {
      "calculate": "!datum.Pos ? 'bottom' : 'top'",
      "as": "deltaTextBaseline"
    },
    {
      "calculate": "!datum.Pos ? 'black' : 'white'",
      "as": "deltaTextColour"
    },
    {
      "calculate": "!datum.Pos ? -2 : 3",
      "as": "deltaTextOffset"
    }
  ],
  "layer": [
    {
      "transform": [
        {"filter": "datum.isMonthComplete==1"}
      ],
      "description": "ActualBar",
      "mark": {
        "type": "bar",
        "tooltip": true,
        "width": {
          "expr": "bandwidth('x') * bwActual"
        },
        "style": "barActual"
      }
    },
    
    {
      "transform": [
        {"filter": "datum.isMonthComplete==0"}
      ],
      "description": "ActualBar2",
      "mark": {
        "type": "bar",
"fill": {
      "expr": "pbiPatternSVG('diagonal-stripe-3', 'white', 'darkGrey')"
    },
    "stroke": "black",
        "tooltip": true,
        "width": {
          "expr": "bandwidth('x') * bwActual"
        },
        "style": "barBudget"
      }
    },
    
    {
      "description": "encodeDelta",
      "mark": {
        "type": "bar",
        "tooltip": true,
        "width": {
          "expr": "bandwidth('x') * bwBudget"
        },
        "xOffset": {
          "expr": "(bandwidth('x') * (bwActual - bwBudget))/2"
        },
        "color": {
          "expr": "datum.DeltaColour"
        }
      },
      "encoding": {
        "y2": {"field": "Budget"}
      }
    },
    {
      "description": "ActualLabel",
      "mark": {
        "type": "text",
        "baseline": {
          "expr": "datum.ActualLabel"
        },
        "color": {
          "expr": "datum.LabelColour"
        },
        "font": "arial black",
        "fontSize": 8,
        "yOffset": {
          "expr": "datum.LabelPad"
        }
      },
      "encoding": {
        "text": {
          "field": "Sales",
          "format": "#,0,.",
          "formatType": "pbiFormat"
        }
      }
    },
    {
      "description": "DeltaLabel",
      "mark": {
        "type": "text",
        "baseline": {
          "expr": "datum.deltaTextBaseline"
        },
        "color": {
          "expr": "datum.deltaTextColour"
        },
        "font": "arial black",
        "fontSize": 8,
        "color": {
          "expr": "datum.DeltaColour"
        },
        "yOffset": {
          "expr": "datum.deltaTextOffset"
        },
        "xOffset": {
          "expr": "datum.newDeltaPos"
        }
      },
      "encoding": {
        "y": {"field": "Budget"},
        "text": {
          "field": "DeltaText",
          "format": "+#,##0,.;-#,##0,.",
          "formatType": "pbiFormat"
        }
      }
    }
  ],
  "description": "encodeActualBarMark",
  "encoding": {
    "tooltip": [
      {"field": "Dates"},
      {
        "field": "Sales",
        "title": "AC",
        "format": "£#,##0",
        "formatType": "pbiFormat"
      },
      {
        "field": "Budget",
        "title": "PL",
        "format": "£#,##0",
        "formatType": "pbiFormat"
      },
      {
        "field": "DeltaText",
        "title": "\u0394Diff",
        "format": "£#,##0",
        "formatType": "pbiFormat"
      }
    ],
    "x": {
      "field": "Dates",
      "type": "nominal",
      "axis": {
        "labelExpr": "pbiFormat(datum['value'], 'MMM')"
      },
      "sort": null
    },
    "y": {
      "field": "Sales",
      "type": "quantitative"
    },
    "opacity": {
      "condition": {
        "test": {
          "field": "__selected__",
          "equal": "off"
        },
        "value": 0.3
      },
      "value": 1
    }
  }
}
```
