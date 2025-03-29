<template>
  <div class="app-container">
    <div class="content">
      <div class="section">
        <div class="section-header" style="text-align: left;font-size: large;color: white;">负荷-气温曲线</div>
        <div class="chart" ref="shortTermChart"></div>
        <div class="section-header" style="text-align: left;font-size: large;color: white;margin-top: 20px;">负荷曲线（表）</div>
        <div class="table-container">
          <table class="load-table">
            <thead>
              <tr>
                <th>日期</th>
                <th v-for="(col, index) in tableHeader.slice(1)" :key="index">{{ col }}</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>负荷</td>
                <td v-for="(data, index) in tableData" :key="index">{{ data }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <!-- 新增温度曲线表格 -->
        <div class="section-header" style="text-align: left;font-size: large;color: white;margin-top: 20px;">温度曲线（表）</div>
        <div class="table-container">
          <table class="temp-table">
            <thead>
              <tr>
                <th>日期</th>
                <th v-for="(col, index) in tempTableHeader.slice(1)" :key="index">{{ col }}</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>温度</td>
                <td v-for="(data, index) in tempTableData" :key="index">{{ data }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>
  <script>
  import * as echarts from 'echarts'
  import { Select, DatePicker } from 'ant-design-vue'

  export default {
    name: 'PowerPredictionUI',
    components: {
      ASelect: Select,
      ADatePicker: DatePicker
    },
    data () {
      return {
        selectedCity: '广州',
        tableHeader: ['日期', '2020-06-01 00:00', '2020-06-01 01:00', '2020-06-01 02:00', '2020-06-01 03:00', '2020-06-01 04:00', '2020-06-01 05:00', '2020-06-01 06:00', '2020-06-01 07:00'],
        tableData: [9495, 9153, 8655, 8074, 7849, 7573, 7756, 8527],
        tempTableHeader: ['日期', '2020-06-01 00:00', '2020-06-01 01:00', '2020-06-01 02:00', '2020-06-01 03:00', '2020-06-01 04:00', '2020-06-01 05:00', '2020-06-01 06:00', '2020-06-01 07:00'],
        tempTableData: [26.5, 26.2, 26.0, 25.8, 25.7, 26.0, 26.2, 26.8]
      }
    },
    mounted () {
      this.initShortTermChart()
      window.addEventListener('resize', () => {
        if (this.$refs.shortTermChart) {
          echarts.getInstanceByDom(this.$refs.shortTermChart).resize()
        }
      })
    },
    methods: {
      initShortTermChart () {
        const chartDom = this.$refs.shortTermChart
        const myChart = echarts.init(chartDom)

        // 静态数据
        const LoadData = [
        ['2021-01-25 00:00', 11402, 31.4],
['2021-02-08 00:00', 12854, 31.0],
['2021-02-10 00:00', 16284, 34.0],
['2021-02-11 00:00', 17509, 36.1],
['2021-03-25 00:00', 17979, 35.2],
['2021-04-14 00:00', 16632, 37.3],
['2021-05-21 00:00', 17021, 35.6],
['2021-05-28 00:00', 16696, 35.9],
['2021-06-10 00:00', 15291, 34.1],
['2021-06-30 00:00', 14275, 30.8],
['2021-07-21 00:00', 13045, 30.3],
['2021-07-22 00:00', 10394, 27.1],
['2021-07-28 00:00', 10153, 25.3],
['2021-07-30 00:00', 7489, 26.6],
['2021-09-01 00:00', 8150, 23.5],
['2021-09-05 00:00', 7984, 25.4],
['2021-09-07 00:00', 8601, 26.3],
['2021-09-11 00:00', 7450, 26.9],
['2021-09-12 00:00', 8732, 27.1],
['2021-11-23 00:00', 10039, 27.5],
['2021-11-29 00:00', 13091, 31.2],
['2021-12-04 00:00', 13309, 31.7],
['2021-12-16 00:00', 14898, 34.1],
['2022-01-13 00:00', 17730, 35.5],
['2022-01-25 00:00', 16736, 37.2],
['2022-02-06 00:00', 17397, 35.9],
['2022-02-17 00:00', 16296, 37.5],
['2022-02-19 00:00', 15596, 34.5],
['2022-03-19 00:00', 15603, 34.4],
['2022-03-29 00:00', 14556, 32.6],
['2022-04-03 00:00', 12151, 30.1],
['2022-04-07 00:00', 11414, 28.3],
['2022-05-19 00:00', 10070, 27.6],
['2022-06-04 00:00', 8594, 24.0],
['2022-06-07 00:00', 6495, 24.3],
['2022-07-02 00:00', 7766, 24.1],
['2022-07-21 00:00', 7399, 24.8],
['2022-07-26 00:00', 9170, 25.1],
['2022-08-23 00:00', 9761, 26.4],
['2022-08-25 00:00', 11253, 30.9],
['2022-09-11 00:00', 13896, 32.5],
['2022-09-17 00:00', 13807, 33.6],
['2022-09-22 00:00', 15951, 34.2],
['2022-10-08 00:00', 16553, 35.4],
['2022-10-22 00:00', 16136, 37.6],
['2022-10-26 00:00', 17435, 37.6],
['2022-11-14 00:00', 16699, 34.5],
['2022-11-24 00:00', 16559, 36.0],
['2022-11-25 00:00', 14207, 34.3],
['2022-12-06 00:00', 13671, 31.5],
['2022-12-07 00:00', 12415, 28.9],
['2023-01-08 00:00', 10076, 27.7],
['2023-01-19 00:00', 8792, 25.0],
['2023-01-24 00:00', 8586, 23.8],
['2023-02-20 00:00', 6770, 25.0],
['2023-03-29 00:00', 6642, 26.0],
['2023-04-08 00:00', 7985, 25.6],
['2023-04-23 00:00', 8588, 26.8],
['2023-06-09 00:00', 10082, 26.8],
['2023-06-27 00:00', 12226, 30.7],
['2023-07-15 00:00', 12837, 30.5],
['2023-08-06 00:00', 14188, 33.9],
['2023-08-31 00:00', 15025, 33.5],
['2023-09-02 00:00', 16008, 34.7],
['2023-09-17 00:00', 16468, 36.0],
['2023-10-01 00:00', 16840, 36.8],
['2023-10-12 00:00', 17018, 34.3],
['2023-11-15 00:00', 14472, 33.3],
['2023-12-13 00:00', 14548, 32.5],
['2023-12-18 00:00', 13795, 30.3],
['2023-12-29 00:00', 10438, 30.6],
['2024-02-03 00:00', 10176, 28.6],
['2024-02-09 00:00', 8577, 26.8],
['2024-02-21 00:00', 7841, 23.9],
['2024-03-15 00:00', 7003, 23.2],
['2024-03-29 00:00', 7645, 25.4],
['2024-04-17 00:00', 8919, 26.0],
['2024-05-08 00:00', 9518, 27.6],
['2024-05-19 00:00', 11345, 29.6],
['2024-05-24 00:00', 12071, 28.8],
['2024-06-16 00:00', 12836, 32.5],
['2024-06-22 00:00', 13959, 34.6],
['2024-06-29 00:00', 16909, 35.9],
['2024-07-12 00:00', 16677, 35.9],
['2024-08-13 00:00', 18251, 37.8],
['2024-08-14 00:00', 15877, 35.0]
        ]
        const option = {
    tooltip: {
        trigger: 'axis'
    },
    legend: {
        data: ['日负荷曲线', '日温度曲线'],
        top: 10,
        right: 10,
        textStyle: {
            color: 'white'
        },
        itemHeight: 20,
        left: 'center',
        padding: 10
    },
    grid: {
        left: '10%',
        right: '15%',
        bottom: '10%',
        borderColor: 'rgb(158,159,159)',
        backgroundColor: '#000'
    },
    xAxis: {
        type: 'category',
        data: LoadData.map(item => item[0]),
        axisLine: {
            lineStyle: {
                color: 'rgb(158,159,159)'
            }
        },
        splitLine: {
            lineStyle: {
                color: 'rgb(158,159,159)'
            }
        },
        axisLabel: {
            color: 'white'
        }
    },
    yAxis: [
        {
            type: 'value',
            name: 'MW',
            position: 'left',
            min: 5837,
            interval: 2500,
            axisLine: {
                show: true,
                lineStyle: {
                    color: 'rgb(158,159,159)'
                }
            },
            splitLine: {
                lineStyle: {
                    color: 'rgb(158,159,159)'
                }
            },
            axisLabel: {
                color: 'white'
            },
            nameTextStyle: {
                color: 'white'
            }
        },
        {
            type: 'value',
            name: '°C',
            position: 'right',
            axisLine: {
                show: true,
                lineStyle: {
                    color: 'rgb(158,159,159)'
                }
            },
            splitLine: {
                show: false
            },
            axisLabel: {
                color: 'white'
            },
            nameTextStyle: {
                color: 'white'
            }
        }
    ],
    dataZoom: [
        {
            startValue: '2024-01-01',
            type: 'slider',
            bottom: '2%',
            height: 6
        },
        {
            type: 'inside'
        }
    ],
    series: [
        {
            showSymbol: false,
            name: '日负荷曲线',
            type: 'line',
            lineStyle: {
                color: 'rgb(235,157,7)'
            },
            itemStyle: {
                color: 'rgb(235,157,7)'
            },
            data: LoadData.map(item => item[1]),
            yAxisIndex: 0,
            markLine: {
                silent: true,
                data: [
                    {
                        type: 'max',
                        symbol: 'none',
                        label: {
                            show: true,
                            color: 'white',
                            backgroundColor: 'rgb(158,159,159)', // 标签背景颜色
                            borderColor: 'rgb(158,159,159)', // 边框颜色
                            borderWidth: 1, // 边框宽度
                            padding: [2, 5] // 内边距
                        },
                        lineStyle: {
                            type: 'dashed',
                            color: 'rgb(158,159,159)'
                        }
                    }
                ]
            },
            markPoint: {
                data: [
                    {
                        type: 'max',
                        name: '最大值',
                        symbol: 'emptyCircle',
                        symbolSize: 16,
                        symbolBorderColor: 'rgb(235,157,7)',
                        symbolBorderWidth: 2,
                        symbolBorderType: 'solid',
                        label: { show: false }
                    }
                ]
            }
        },
        {
            showSymbol: false,
            name: '日温度曲线',
            type: 'line',
            lineStyle: {
                color: 'rgb(2,182,237)'
            },
            itemStyle: {
                color: 'rgb(2,182,237)'
            },
            data: LoadData.map(item => item[2]),
            yAxisIndex: 1,
            markLine: {
                silent: true,
                data: [
                    {
                        type: 'max',
                        symbol: 'none',
                        label: {
                            show: true,
                            color: 'white',
                            backgroundColor: 'rgb(158,159,159)', // 标签背景颜色
                            borderColor: 'rgb(158,159,159)', // 边框颜色
                            borderWidth: 1, // 边框宽度
                            padding: [2, 5] // 内边距
                        },
                        lineStyle: {
                            type: 'dashed',
                            color: 'rgb(158,159,159)'
                        }
                    }
                ]
            },
            markPoint: {
                data: [
                    {
                        type: 'max',
                        name: '最大值',
                        symbol: 'emptyCircle',
                        symbolSize: 16,
                        symbolBorderColor: 'rgb(2,182,237)',
                        symbolBorderWidth: 2,
                        symbolBorderType: 'solid',
                        label: { show: false }
                    }
                ]
            }
        }
    ]
}

        myChart.setOption(option)
      }
    }
  }
  </script>

  <style scoped>
  .app-container {
    background-color: #0a1d4d;
    color: #1890ff;
    font-family: Arial, sans-serif;
    min-height: 100vh;
    overflow-y: auto;
  }
  .content {
    align-self: center;
    max-width: 1325px;
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;
    margin: 20px;
  }

  .section {
    background-color: #0a1d4d;
    border: 2px solid #00aaff;
    border-radius: 8px;
    padding: 15px;
    color: #ffffff;
    font-family: Arial, sans-serif;
  }

  .chart {
    height: 500px;
    background-color: #0a1d4d;
    border: 1px solid #d9d9d9;
    border-radius: 5px;
    margin-top: 10px;
    align-self: center;
  }

  .card-title {
    background-color: #1890ff;
    color: #ffffff;
    text-align: center;
    padding: 10px;
    border-top-left-radius: 6px;
    border-top-right-radius: 6px;
    font-size: large;
    font-weight: bold;
  }

  .stats-table {
    margin: 20px;
    width: 100%;
    border-collapse: collapse;
    margin-top: 10px;
  }

  .stats-table td {
    padding: 15px 20px;
    text-align: left;
    font-size: 18px;
    border: none;
  }
  .section-header {
    text-align: center;
    font-size: 18px;
    font-weight: bold;
    padding: 5px 0;
    border-bottom: 2px solid #00aaff;
    margin-bottom: 10px;
    color: rgb(27,243,248);
  }
  .table-container {
  background-color: #0a1d4d;
  border: 1px solid #00aaff;
  border-radius: 8px;
  padding: 15px;
  margin-top: 15px;
}

.load-table {
  width: 100%;
  border-collapse: collapse;
}

.load-table th,
.load-table td {
  padding: 10px;
  text-align: left;
  color: white;
  border: 1px solid #333;
}

.load-table th {
  background-color: #002d66;
}
.temp-table {
  width: 100%;
  border-collapse: collapse;
}

.temp-table th,
.temp-table td {
  padding: 10px;
  text-align: left;
  color: white;
  border: 1px solid #333;
}

.temp-table th {
  background-color: #002d66;
}
</style>
