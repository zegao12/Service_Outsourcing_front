<template>
  <div class="app-container">
    <div class="header">
      <div class="header2">返回首页</div>
      <div class="header2">注销</div>
    </div>

    <div class="content">
      <div class="section left">
        <div class="section-header ">超短时功率预测曲线 (3天)</div>
        <div class="chart" ref="shortTermChart"></div>
      </div>

      <div class="section right">
        <div class="section-header ">预测误差 (3天)</div>
        <table class="stats-table">
          <tr><td>均方根</td><td style="color: rgb(27,243,248);">0.16</td></tr>
          <tr><td>平均绝对误差</td><td style="color: rgb(27,243,248);">0.1</td></tr>
          <tr><td>相关性系数</td><td style="color: rgb(27,243,248);">-0.04</td></tr>
          <tr><td>最大预测误差</td><td style="color: rgb(27,243,248);">44.9</td></tr>
          <tr><td>合格率</td><td style="color: rgb(27,243,248);">83.15%</td></tr>
        </table>
      </div>

      <div class="section left" padding="20px">
        <div class="section-header ">超短时功率预测曲线 (4h)</div>
        <div class="chart" ref="ultraShortTermChart"></div>
      </div>

      <div class="section right">
        <div class="section-header ">预测误差(4小时)</div>
        <table class="stats-table" >
          <tr><td>均方根</td><td style="color: rgb(27,243,248);">0.12</td></tr>
          <tr><td>平均绝对误差</td><td style="color: rgb(27,243,248);">0.09</td></tr>
          <tr><td>相关性系数</td><td style="color: rgb(27,243,248);">0.01</td></tr>
          <tr><td>最大预测误差</td><td style="color: rgb(27,243,248);">49.1</td></tr>
          <tr><td>合格率</td><td style="color: rgb(27,243,248);">90.15%</td></tr>
        </table>
      </div>
    </div>
  </div>
</template>

  <script>
  import * as echarts from 'echarts'

  export default {
    name: 'PowerPredictionUI',
    mounted () {
      this.initShortTermChart()
      this.initUltraShortTermChart()
    },
    methods: {
      initShortTermChart () {
        const chartDom = this.$refs.shortTermChart
        const myChart = echarts.init(chartDom)
        const option = {
          legend: {
        data: ['预测功率', '实际功率'],
        top: 'top',
        left: 'left',
        icon: 'rect',
        padding: 20,
        textStyle: {
          color: 'white'
        }
    },
          xAxis: { splitLine: { show: false, width: 1 }, name: '(h)', nameTextStyle: { color: 'white' }, axisLabel: { show: true, textStyle: { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' } } },
          yAxis: { splitLine: { show: true, lineStyle: { type: 'solid', color: 'rgba(140,140,206,0.5)' } }, axisLabel: { show: true, textStyle: { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' } } },
          grid:
          {
            show: true,
            borderColor: 'rgba(48,113,169,1)',
            borderWidth: 2
          },
          series: [{
            name: '实际功率',
            showSymbol: false,
            data: [ [0.0, 44.3], [0.73, 40.12], [1.45, 52.2], [2.18, 68.99], [2.91, 64.21], [3.64, 76.78], [4.36, 73.02], [5.09, 87.81], [5.82, 81.23], [6.55, 89.32],
    [7.27, 80.11], [8.0, 74.65], [8.73, 79.99], [9.45, 66.12], [10.18, 55.34], [10.91, 59.01], [11.64, 33.78], [12.36, 41.23], [13.09, 15.34], [13.82, 25.98],
    [14.55, 1.23], [15.27, -4.56], [16.0, 5.67], [16.73, -12.34], [17.45, -10.12], [18.18, -15.67], [18.91, -2.34], [19.64, -8.9], [20.36, -1.23], [21.09, 4.56],
    [21.82, 12.34], [22.55, 25.67], [23.27, 18.9], [24.0, 40.12], [24.73, 33.78], [25.45, 60.98], [26.18, 55.34], [26.91, 78.9], [27.64, 66.12], [28.36, 88.76],
    [29.09, 77.45], [29.82, 86.34], [30.55, 72.12], [31.27, 89.87], [32.0, 66.54], [32.73, 80.34], [33.45, 50.12], [34.18, 70.67], [34.91, 44.3], [35.64, 55.89],
    [36.36, 25.67], [37.09, 33.45], [37.82, 11.23], [38.55, 28.9], [39.27, -2.34], [40.0, -5.67], [40.73, -8.9], [41.45, -15.67], [42.18, -8.9], [42.91, -18.9],
    [43.64, -3.45], [44.36, 2.34], [45.09, -4.56], [45.82, 10.12], [46.55, 22.34], [47.27, 35.67], [48.0, 23.45], [48.73, 44.3], [49.45, 50.12], [50.18, 66.54],
    [50.91, 55.34], [51.64, 79.87], [52.36, 72.12], [53.09, 89.87], [53.82, 77.45], [54.55, 86.34], [55.27, 72.12], [56.0, 90.23], [56.73, 60.12], [57.45, 77.45],
    [58.18, 50.67], [58.91, 44.3], [59.64, 33.45], [60.36, 22.34], [61.09, 15.67], [61.82, 28.9], [62.55, 5.67], [63.27, 18.9], [64.0, -5.67], [64.73, -12.34],
    [65.45, -8.9], [66.18, -15.67], [66.91, -10.12], [67.64, -6.54], [68.36, -3.45], [69.09, 8.9], [69.82, 6.54], [70.55, 12.34], [71.27, 26.9], [72.0, 22.34]],
            type: 'line',
            lineStyle: {
        normal: {
          color: 'rgb(84,112,198)',
          width: 1
        }
      },
            smooth: false,
            markLine: {
            symbol: 'none',
            silent: true,
            lineStyle: {
                color: 'rgba(140,140,206,0.9)',
                type: 'solid'
            },
            label:
            {
              textStyle:
              { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' }
            },
            data: [
                { yAxis: 80.96,
                 name: 'Bottom Line'
                }, // 最底部的线
                { yAxis: -10.59,
                name: 'Top Line'
               } // 最顶部的线
            ]
        }
          },
          {
            name: '预测功率',
            showSymbol: false,
            data: [[0.0, 41.47], [0.73, 46.66], [1.45, 59.39], [2.18, 65.24], [2.91, 66.02], [3.64, 70.67], [4.36, 74.83], [5.09, 80.28], [5.82, 87.31], [6.55, 82.63],
[7.27, 81.07], [8.0, 76.32], [8.73, 78.14], [9.45, 65.86], [10.18, 65.37], [10.91, 48.71], [11.64, 44.68], [12.36, 30.47], [13.09, 26.28], [13.82, 19.94],
[14.55, 10.92], [15.27, -2.64], [16.0, -0.31], [16.73, -5.54], [17.45, -6.05], [18.18, -12.03], [18.91, -10.57], [19.64, -8.05], [20.36, -3.71], [21.09, 2.46],
[21.82, 4.38], [22.55, 15.83], [23.27, 24.85], [24.0, 30.48], [24.73, 44.61], [25.45, 54.17], [26.18, 63.65], [26.91, 64.17], [27.64, 74.88], [28.36, 83.52],
[29.09, 84.26], [29.82, 83.54], [30.55, 83.49], [31.27, 83.41], [32.0, 76.79], [32.73, 70.06], [33.45, 66.17], [34.18, 65.71], [34.91, 53.02], [35.64, 40.04],
[36.36, 34.97], [37.09, 31.62], [37.82, 25.96], [38.55, 15.25], [39.27, 4.81], [40.0, -3.87], [40.73, -4.92], [41.45, -4.21], [42.18, -14.42], [42.91, -12.67],
[43.64, -4.99], [44.36, -3.88], [45.09, -4.27], [45.82, 8.98], [46.55, 11.74], [47.27, 24.75], [48.0, 26.17], [48.73, 34.18], [49.45, 44.87], [50.18, 55.67],
[50.91, 61.47], [51.64, 75.86], [52.36, 74.44], [53.09, 84.82], [53.82, 83.92], [54.55, 83.71], [55.27, 82.36], [56.0, 80.94], [56.73, 77.65], [57.45, 70.03],
[58.18, 60.21], [58.91, 54.32], [59.64, 44.67], [60.36, 35.48], [61.09, 28.27], [61.82, 23.66], [62.55, 10.04], [63.27, 12.46], [64.0, 1.58], [64.73, -8.21],
[65.45, -6.14], [66.18, -11.79], [66.91, -9.55], [67.64, -5.37], [68.36, -8.47], [69.09, 3.81], [69.82, 1.52], [70.55, 6.66], [71.27, 20.13], [72.0, 28.17]],
            type: 'line',
            lineStyle: {
        normal: {
          color: 'rgb(134,215,47)',
          width: 1
        }
      },
            smooth: true,
            markLine: {
            symbol: 'none',
            silent: true,
            lineStyle: {
                color: 'rgba(140,140,206,0.9)',
                type: 'solid'
            },
            label:
            {
              textStyle:
              { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' }
            },
            data: [
                { yAxis: 80.96,
                 name: 'Bottom Line'
                }, // 最底部的线
                { yAxis: -10.59,
                name: 'Top Line'
               } // 最顶部的线
            ]
        }
          }

        ]
        }
        myChart.setOption(option)
      },
      initUltraShortTermChart () {
        const chartDom = this.$refs.ultraShortTermChart
        const myChart = echarts.init(chartDom)
        const option = {
          legend: {
        data: ['实际功率', '预测功率'],
        top: 'top',
        left: 'left',
        icon: 'rect',
        padding: 20,
        textStyle: {
          color: 'white'
        }
    },
          grid:
          {
            show: true,
            borderColor: 'rgba(48,113,169,1)',
            borderWidth: 2
          },
          xAxis: { splitLine: { show: false, width: 1 }, name: '(min)', nameTextStyle: { color: 'white' }, axisLabel: { show: true, textStyle: { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' } } },
          yAxis: { splitLine: { show: true, lineStyle: { type: 'solid', color: 'rgba(140,140,206,0.5)' } }, nameTextStyle: { color: 'white' }, axisLabel: { show: true, textStyle: { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' } } },
          series: [{
            name: '实际功率',
            showSymbol: false,
            data: [[0, -1.95], [2, -1.87], [5, -2.15], [7, -2.32], [10, -2.05], [12, -1.78], [15, -1.92], [17, -2.25], [20, -2.45], [22, -2.15], [24, -1.85], [27, -1.68], [30, -1.75], [32, -2.10], [35, -1.95], [37, -1.65], [40, -1.82], [42, -2.18], [45, -2.35], [47, -2.05], [50, -1.75], [52, -1.85], [55, -2.20], [57, -2.45], [60, -2.25], [62, -1.95], [65, -1.68], [67, -1.85], [70, -2.10], [72, -1.90], [75, 5.25], [77, 10.85], [80, 18.45], [82, 25.65], [85, 32.80], [87, 39.45], [90, 45.75], [92, 52.40], [95, 58.65], [97, 64.20], [100, 69.80], [102, 74.35], [105, 78.65], [107, 81.25], [110, 82.85], [112, 83.10], [115, 82.75], [117, 81.45], [120, 79.85], [122, 77.25], [125, 74.65], [127, 71.20], [130, 67.45], [132, 63.25], [135, 58.75], [137, 53.45], [140, 47.85], [142, 41.65], [145, 35.25], [147, 28.85], [150, 22.45], [152, 16.25], [155, 10.15], [157, 4.25], [160, -0.45], [162, -1.35], [165, -1.75], [167, -1.85], [170, -2.45], [172, -2.75], [175, -2.25], [177, -1.85], [180, -1.45], [182, -1.95], [185, -2.65], [187, -2.85], [190, -2.35], [192, -1.85], [195, -1.45], [197, -1.95], [200, -2.55], [202, -2.85], [205, -2.35], [207, -1.75], [210, -1.25], [212, -1.85], [215, -2.45], [217, -2.85], [220, -2.35], [222, -1.75], [225, -1.35], [227, -1.85], [230, -2.45], [232, -2.75], [235, -2.25], [237, -1.65], [240, -1.85]],
            type: 'line',
            lineStyle: {
        normal: {
          color: 'rgb(134,215,47)',
          width: 1
        }
      },
            smooth: true
          },
          {
            name: '预测功率',
            showSymbol: false,
            data: [[0, 1.85], [2, -3.18], [5, -6.05], [7, -2.55], [10, -6.18], [12, 2.65], [15, -0.22], [17, 2.35], [20, -1.02], [22, 1.02],
    [24, -0.95], [27, 2.92], [30, -1.14], [32, 2.65], [35, -5.33], [37, 1.78], [40, -5.56], [42, -1.15], [45, -5.15], [47, -2.85],
    [50, -5.18], [52, 0.38], [55, -4.76], [57, -3.25], [60, -4.48], [62, 0.25], [65, -4.38], [67, 2.25], [70, -5.15], [72, 0.08],
    [75, 12.05], [77, 9.05], [80, 26.35], [82, 22.55], [85, 41.05], [87, 37.55], [90, 55.75], [92, 49.65], [95, 69.65], [97, 61.55],
    [100, 78.65], [102, 69.74], [105, 88.45], [107, 79.05], [110, 92.25], [112, 77.68], [115, 91.16], [117, 76.65], [120, 89.66], [122, 71.65],
    [125, 86.34], [127, 66.26], [130, 79.05], [132, 58.78], [135, 69.65], [137, 48.92], [140, 58.86], [142, 37.95], [145, 46.75], [147, 25.12],
    [150, 34.26], [152, 12.65], [155, 20.95], [157, 3.15], [160, -5.05], [162, 3.15], [165, -4.65], [167, 2.45], [170, -4.15], [172, 0.35],
    [175, -2.98], [177, 3.65], [180, -0.75], [182, 1.75], [185, -1.85], [187, 1.15], [190, -1.65], [192, 4.15], [195, -0.65], [197, 2.58],
    [200, -2.65], [202, 2.05], [205, -1.45], [207, 4.45], [210, -0.65], [212, 2.55], [215, -1.45], [217, 0.45], [220, -0.45], [222, 3.05],
    [225, -0.55], [227, 2.65], [230, -1.75], [232, 2.05], [235, -1.65], [237, 3.05], [240, -0.35]],
            type: 'line',
            lineStyle: {
        normal: {
          color: 'rgb(84,112,198)',
          width: 1
        }
      },
            smooth: false
          }]
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
.header {
  display: flex;
  justify-content: space-between;
  background-color: #0a1d4d;
  color: rgb(27,243,248);
  padding: 10px;
  font-weight: bold;
  border-bottom: 2px solid #00aaff;
  font-size: 18px;
}

.header1 {
  font-size: 25px;
}

.header2 {
  margin-top: 6px;
}

  .content {
    display: grid;
    grid-template-columns: 7fr 3fr;
    gap: 20px;
    margin: 20px;
  }

  .section {
  background-color: #0a1d4d; /* 背景色与右侧盒子统一 */
  border: 2px solid #00aaff; /* 边框颜色与右侧盒子统一 */
  border-radius: 8px; /* 圆角与右侧盒子统一 */
  padding: 15px; /* 内边距与右侧盒子统一 */
  color: #ffffff; /* 文字颜色与右侧盒子统一 */
  font-family: Arial, sans-serif;
}

.chart {
  height: 300px;
  background-color: #0a1d4d;/* 图表背景色 */
  border: 1px solid #d9d9d9; /* 图表边框 */
  border-radius: 5px; /* 图表圆角 */
  margin-top: 10px; /* 与标题的间距 */
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
  border-bottom: 2px solid #00aaff; /* 标题下划线与右侧盒子统一 */
  margin-bottom: 10px;
  color: rgb(27,243,248); /* 标题颜色与右侧盒子统一 */
}
  </style>
