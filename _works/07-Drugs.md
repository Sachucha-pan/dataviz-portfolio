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

  "title": "Дашборд аналізу психоактивних речовин та психологічних характеристик",

  "vconcat": [

    {
      "hconcat": [

        {
          "title": "Популярність серед чоловіків",

          "width": 300,
          "height": 350,

          "data": {
            "url": "https://raw.githubusercontent.com/Sachucha-pan/dataviz-portfolio/main/specs/Drug_Consumption.csv"
          },

          "transform": [
            {
              "filter": "datum.Gender == 'M'"
            },
            {
              "fold": [
                "Alcohol",
                "Amphet",
                "Amyl",
                "Benzos",
                "Caff",
                "Cannabis",
                "Choc",
                "Coke",
                "Crack",
                "Ecstasy",
                "Heroin",
                "Ketamine",
                "Legalh",
                "LSD",
                "Meth",
                "Mushrooms",
                "Nicotine",
                "VSA"
              ],
              "as": ["Drug", "Usage"]
            },
            {
              "calculate": "datum.Usage == 'CL0' ? 0 : 1",
              "as": "User"
            }
          ],

          "mark": {
            "type": "bar",
            "cornerRadiusEnd": 5,
            "color": "#2563EB"
          },

          "encoding": {
            "y": {
              "field": "Drug",
              "type": "nominal",
              "sort": "-x",
              "title": "Речовина"
            },

            "x": {
              "aggregate": "mean",
              "field": "User",
              "type": "quantitative",
              "title": "Частка користувачів",
              "axis": {
                "format": ".0%"
              }
            },

            "tooltip": [
              {
                "field": "Drug",
                "title": "Речовина"
              },
              {
                "aggregate": "mean",
                "field": "User",
                "format": ".1%",
                "title": "Частка користувачів"
              }
            ]
          }
        },

        {
          "title": "Популярність серед жінок",

          "width": 300,
          "height": 350,

          "data": {
            "url": "https://raw.githubusercontent.com/Sachucha-pan/dataviz-portfolio/main/specs/Drug_Consumption.csv"
          },

          "transform": [
            {
              "filter": "datum.Gender == 'F'"
            },
            {
              "fold": [
                "Alcohol",
                "Amphet",
                "Amyl",
                "Benzos",
                "Caff",
                "Cannabis",
                "Choc",
                "Coke",
                "Crack",
                "Ecstasy",
                "Heroin",
                "Ketamine",
                "Legalh",
                "LSD",
                "Meth",
                "Mushrooms",
                "Nicotine",
                "VSA"
              ],
              "as": ["Drug", "Usage"]
            },
            {
              "calculate": "datum.Usage == 'CL0' ? 0 : 1",
              "as": "User"
            }
          ],

          "mark": {
            "type": "bar",
            "cornerRadiusEnd": 5,
            "color": "#DC2626"
          },

          "encoding": {
            "y": {
              "field": "Drug",
              "type": "nominal",
              "sort": "-x",
              "title": "Речовина"
            },

            "x": {
              "aggregate": "mean",
              "field": "User",
              "type": "quantitative",
              "title": "Частка користувачів",
              "axis": {
                "format": ".0%"
              }
            },

            "tooltip": [
              {
                "field": "Drug",
                "title": "Речовина"
              },
              {
                "aggregate": "mean",
                "field": "User",
                "format": ".1%",
                "title": "Частка користувачів"
              }
            ]
          }
        }
      ]
    },

    {
      "title": "Психологічні характеристики за віковими групами",

      "width": 700,
      "height": 350,

      "data": {
        "url": "https://raw.githubusercontent.com/Sachucha-pan/dataviz-portfolio/main/specs/Drug_Consumption.csv"
      },

      "transform": [
        {
          "fold": [
            "Ascore",
            "Cscore",
            "Escore",
            "Impulsive",
            "Nscore",
            "Oscore",
            "SS"
          ],
          "as": ["Metric", "Value"]
        }
      ],

      "mark": {
        "type": "line",
        "point": true,
        "strokeWidth": 3
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
          "aggregate": "mean",
          "field": "Value",
          "type": "quantitative",
          "title": "Середнє значення"
        },

        "color": {
          "field": "Metric",
          "type": "nominal",
          "title": "Показник"
        },

        "tooltip": [
          {
            "field": "Age",
            "title": "Вік"
          },
          {
            "field": "Metric",
            "title": "Показник"
          },
          {
            "aggregate": "mean",
            "field": "Value",
            "format": ".2f",
            "title": "Середнє значення"
          }
        ]
      }
    }
  ],

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
