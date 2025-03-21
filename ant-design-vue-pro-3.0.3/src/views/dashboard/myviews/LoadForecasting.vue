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
        <div class="section-header ">超短时功率预测曲线 (4小时)</div>
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
          xAxis: { splitLine: { show: false, width: 1 } },
          yAxis: { splitLine: { show: true, lineStyle: { type: 'dashed' } } },
          series: [{
            data: [[0, -1.96], [12, 82.85], [18, -2], [24, 1], [30, 2], [36, 54.76], [42, 0], [48, 0], [54, 38.55], [60, 60], [66, 22.22], [72, 0]],
            type: 'line',
            lineStyle: {
        normal: {
          color: 'rgb(223,126,133)'
        }
      },
            smooth: true
          }]
        }
        myChart.setOption(option)
      },
      initUltraShortTermChart () {
        const chartDom = this.$refs.ultraShortTermChart
        const myChart = echarts.init(chartDom)
        const option = {
          xAxis: { splitLine: { show: false, width: 1 } },
          yAxis: { splitLine: { show: true, lineStyle: { type: 'dashed' } } },
          series: [{
            data: [[50, 80], [70, 90], [120, 85], [150, 75], [180, 60], [200, 45], [220, 30], [240, 15], [230, 20], [210, 35], [190, 50], [170, 65], [140, 70], [110, 80], [90, 40], [60, 55], [40, 60], [20, 70]],
            type: 'line',
            lineStyle: {
        normal: {
          color: 'rgb(223,126,133)'
        }
      },
            smooth: true
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
