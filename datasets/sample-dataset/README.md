# Data

This is the README.md this project.

## Table 

<FlatUiTable url="https://raw.githubusercontent.com/luccasmmg/test-data-repo-1/main/data_2.csv" />
 
## LineChart from URL 

<Vega
  data={{
    table: [
      {
        x: 1890,
        y: -0.418
      },
      {
        x: 2021,
        y: 0.923
      }
    ]
  }}
  spec={{
    $schema: 'https://vega.github.io/schema/vega-lite/v4.json',
    data: {
      name: 'table'
    },
    encoding: {
      x: {
        field: 'x',
        type: 'ordinal'
      },
      y: {
        field: 'y',
        type: 'quantitative'
      }
    },
    mark: 'bar'
  }}
/>
