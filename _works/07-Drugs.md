---
title: Аналіз популярності психоактивних речовин та психологічних характеристик респондентів.
---
Дослідницькі питання дашборду:
Які психоактивні речовини є найбільш і найменш поширеними серед чоловіків?
Які психоактивні речовини є найбільш і найменш поширеними серед жінок?
Як змінюються психологічні характеристики респондентів залежно від віку?


```vega-lite
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",

  "title": "Дашборд: Демографічні характеристики, особистісні риси та вживання психоактивних речовин",

  "vconcat": [

    {
      "title": "Фільтр: оберіть вікову групу",

      "width": 800,
      "height": 120,

      "data": {
        "url": "https://raw.githubusercontent.com/Sachucha-pan/dataviz-portfolio/main/specs/Drug_Consumption.csv"
      },

      "params": [
        {
          "name": "ageSelect",
          "select": {
            "type": "point",
            "fields": ["Age"]
          }
        }
      ],

      "mark": {
        "type": "bar",
        "cornerRadiusTopLeft": 4,
        "cornerRadiusTopRight": 4
      },

      "encoding": {
        "x": {
          "field": "Age",
          "type": "ordinal",
          "sort": [
            "18-24",
            "25-34",
            "35-44",
            "45-54",
            "55-64",
            "65+"
          ],
          "title": "Вікова група"
        },

        "y": {
          "aggregate": "count",
          "type": "quantitative",
          "title": "Кількість респондентів"
        },

        "color": {
          "condition": {
            "param": "ageSelect",
            "value": "#2563EB"
          },
          "value": "#D1D5DB"
        },

        "tooltip": [
          {
            "field": "Age",
            "title": "Вікова група"
          },
          {
            "aggregate": "count",
            "title": "Кількість респондентів"
          }
        ]
      }
    },

    {
      "title": "Розподіл респондентів за рівнем освіти",

      "width": 800,
      "height": 300,

      "data": {
        "url": "https://raw.githubusercontent.com/Sachucha-pan/dataviz-portfolio/main/specs/Drug_Consumption.csv"
      },

      "transform": [
        {
          "filter": {
            "param": "ageSelect"
          }
        }
      ],

      "mark": {
        "type": "arc",
        "innerRadius": 70
      },

      "encoding": {
        "theta": {
          "aggregate": "count"
        },

        "color": {
          "field": "Education",
          "type": "nominal",
          "title": "Освіта"
        },

        "tooltip": [
          {
            "field": "Education",
            "title": "Рівень освіти"
          },
          {
            "aggregate": "count",
            "title": "Кількість"
          }
        ]
      }
    },

    {
      "title": "Відкритість до нового досвіду та рівень вживання LSD",

      "width": 800,
      "height": 320,

      "data": {
        "url": "https://raw.githubusercontent.com/Sachucha-pan/dataviz-portfolio/main/specs/Drug_Consumption.csv"
      },

      "transform": [
        {
          "filter": {
            "param": "ageSelect"
          }
        }
      ],

      "mark": {
        "type": "line",
        "point": {
          "filled": true,
          "size": 100
        },
        "strokeWidth": 3
      },

      "encoding": {
        "x": {
          "field": "LSD",
          "type": "ordinal",
          "sort": [
            "CL0",
            "CL1",
            "CL2",
            "CL3",
            "CL4",
            "CL5",
            "CL6"
          ],
          "title": "Рівень вживання LSD"
        },

        "y": {
          "aggregate": "mean",
          "field": "Oscore",
          "type": "quantitative",
          "title": "Середній Oscore"
        },

        "color": {
          "field": "Gender",
          "type": "nominal",
          "title": "Стать",
          "scale": {
            "domain": ["M", "F"],
            "range": ["#2563EB", "#DC2626"]
          }
        },

        "tooltip": [
          {
            "field": "Gender",
            "title": "Стать"
          },
          {
            "field": "LSD",
            "title": "Рівень LSD"
          },
          {
            "aggregate": "mean",
            "field": "Oscore",
            "format": ".2f",
            "title": "Середній Oscore"
          }
        ]
      }
    }
  ],

  "resolve": {
    "scale": {
      "color": "independent"
    }
  },

  "config": {
    "view": {
      "stroke": null
    }
  }
}
```
Дашборд поєднує аналіз популярності психоактивних речовин та психологічних характеристик респондентів. Перші дві візуалізації демонструють структуру споживання речовин серед чоловіків і жінок та дозволяють виявити гендерні відмінності. Третя інтерактивна візуалізація дає можливість дослідити зв'язок між віком респондентів і ключовими психологічними характеристиками.

Результати показують, що найбільш поширеними в обох групах є кофеїн, шоколад та алкоголь, тоді як важкі наркотики мають найнижчу популярність. Одночасно аналіз психологічних показників свідчить, що молодші респонденти характеризуються вищою відкритістю до нового досвіду, імпульсивністю та прагненням до нових відчуттів, а зі збільшенням віку ці показники поступово знижуються.

Таким чином дашборд дозволяє комплексно дослідити як особливості споживання психоактивних речовин, так і психологічний профіль різних груп респондентів.

Завдяки можливості самостійно обирати показник для аналізу користувач отримує гнучкий інструмент дослідження даних та може детальніше вивчити особливості кожної вікової групи.
