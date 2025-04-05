<template>
  <div class="app-container">
    <div class="header">
      <div class="header2">返回首页</div>
      <div class="header2">注销</div>
    </div>

    <div class="content">
      <!-- 左侧容器：包含两个曲线图 -->
      <div class="left-container">
        <div class="section">
          <div class="section-header">优化曲线</div>
          <div class="chart" ref="shortTermChart"></div>
        </div>
        <div class="section">
          <div class="section-header">负荷预测曲线</div>
          <div class="chart" ref="ultraShortTermChart"></div>
        </div>
      </div>

      <!-- 右侧容器：包含所有误差统计 -->
      <div class="right-container">
        <div class="station-info-box">
          <div class="station-header">站点信息</div>
          <div class="station-content">
            <div class="station-row">
              <i class="icon-home"></i>
              <span class="label">站点名称</span>
              <span class="value">A电气股份有限公司</span>
            </div>
            <div class="station-row">
              <i class="icon-location"></i>
              <span class="label">经纬度</span>
              <span class="value">北纬31°14′，东经121°39′</span>
            </div>
            <div class="station-row">
              <i class="icon-altitude"></i>
              <span class="label">海拔高度</span>
              <span class="value">300米</span>
            </div>
          </div>
        </div>

        <div class="install-info-box">
          <div class="install-header">装机信息</div>
          <div class="install-grid">
            <div class="install-item">
              <i class="icon-capacity"></i>
              <div>
                <div class="install-label">装机容量</div>
                <div class="install-value">300 kW</div>
              </div>
            </div>
            <div class="install-item">
              <i class="icon-tracking"></i>
              <div>
                <div class="install-label">跟踪方式</div>
                <div class="install-value">最大功率点跟踪</div>
              </div>
            </div>
            <div class="install-item">
              <i class="icon-inverter"></i>
              <div>
                <div class="install-label">逆变器数量</div>
                <div class="install-value">5 台</div>
              </div>
            </div>
            <div class="install-item">
              <i class="icon-module"></i>
              <div>
                <div class="install-label">组件类型</div>
                <div class="install-value">A 类</div>
              </div>
            </div>
            <div class="install-item">
              <i class="icon-type"></i>
              <div>
                <div class="install-label">装机类型</div>
                <div class="install-value">分布式光伏</div>
              </div>
            </div>
            <div class="install-item">
              <i class="icon-tilt"></i>
              <div>
                <div class="install-label">安装倾角</div>
                <div class="install-value">30°</div>
              </div>
            </div>
          </div>
        </div>

        <div class="error-box">
          <div class="error-header">气象信息</div>
          <div class="error-grid">
            <div class="error-item">
              <i class="icon-light"></i>
              <div>
                <div class="error-label">光照</div>
                <div class="error-value">208.0 lx</div>
              </div>
            </div>
            <div class="error-item">
              <i class="icon-wind"></i>
              <div>
                <div class="error-label">风速</div>
                <div class="error-value">1.5 m/s</div>
              </div>
            </div>
            <div class="error-item">
              <i class="icon-humidity"></i>
              <div>
                <div class="error-label">湿度</div>
                <div class="error-value">82.8 %</div>
              </div>
            </div>
            <div class="error-item">
              <i class="icon-temperature"></i>
              <div>
                <div class="error-label">温度</div>
                <div class="error-value">23.2 ℃</div>
              </div>
            </div>
          </div>
        </div>
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
      var datax = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24]

      const option = {
    legend: {
        data: ['优化前', '优化后'],
        top: 'top',
        left: 'left',
        icon: 'rect',
        padding: 20,
        textStyle: {
          color: 'white'
        }
    },
        xAxis: {
          data: datax,
          axisTick:
          {
            show: false
          },
          name: '(h)',
          nameLocation: 'end',
          nameTextStyle: {
            color: 'white',
            padding: 10
          },
         splitLine: { show: false, width: 1 },
         axisLabel: { show: true, textStyle: { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' } }
        },
        yAxis: {
          type: 'value',
          min: 0,
          max: 1,
          interval: 0.15,
          axisLine: { show: false },
          axisTick:
          {
            show: false
          },
          name: '出力/p.u.',
          nameLocation: 'center',
          nameTextStyle: {
            color: 'white',
            padding: 20
          },
          splitLine: { show: true, lineStyle: { type: 'solid', color: 'rgba(140,140,206,0.7)' } },
axisLabel: { show: true, textStyle: { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' } }
        },

        series: [
          {
            showSymbol: false,
            name: '优化前',
            data: [[0, 0.63], [1, 0.64], [2, 0.66], [3, 0.69], [4, 0.71],
[5, 0.73], [6, 0.75], [7, 0.76], [8, 0.76], [9, 0.73],
[10, 0.68], [11, 0.61], [12, 0.53], [13, 0.46], [14, 0.39],
[15, 0.34], [16, 0.31], [17, 0.28], [18, 0.26], [19, 0.24],
[20, 0.23], [21, 0.25], [22, 0.29], [23, 0.33], [24, 0.36]
],
            type: 'line',
            smooth: true,
            color: '#ffc800',
            lineStyle:
            {
              width: 1
            }
          },
          {
            showSymbol: false,
            name: '优化后',
            data: [[0, 0.79], [1, 0.77], [2, 0.74], [3, 0.71], [4, 0.68],
[5, 0.64], [6, 0.59], [7, 0.54], [8, 0.48], [9, 0.41],
[10, 0.34], [11, 0.28], [12, 0.25], [13, 0.25], [14, 0.28],
[15, 0.33], [16, 0.4], [17, 0.46], [18, 0.51], [19, 0.57],
[20, 0.63], [21, 0.7], [22, 0.75], [23, 0.8], [24, 0.82]
],
            type: 'line',
            smooth: true,
            lineStyle:
            {
              width: 1
            },
            color: 'rgb(0, 255, 200) '
          }
        ]
      }

      myChart.setOption(option)
    },
    initUltraShortTermChart () {
      const chartDom = this.$refs.ultraShortTermChart
      const myChart = echarts.init(chartDom)
      var datax = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24]

      const option = {
        grid:
          {
            show: true,
            borderColor: 'rgba(48,113,169,1)',
            borderWidth: 2
          },
        legend: {
        data: ['预测负荷', '实时负荷'],
        top: 'top',
        left: 'left',
        icon: 'rect',
        padding: 20,
        textStyle: {
          color: 'white'
        }
    },
        xAxis: {
          data: datax,
          axisTick:
          {
            show: false
          },
          name: '(h)',
          nameLocation: 'end',
          nameTextStyle: {
            color: 'white',
            padding: 10
          },
         splitLine: { show: false, width: 1 },
         axisLabel: { show: true, textStyle: { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' } }

        },
        yAxis: {
          type: 'value',
          min: 200,
          max: 305,
          interval: 15,
          axisTick:
          {
            show: false
          },
          nameLocation: 'center',
          nameTextStyle: {
            color: 'white',
            padding: 20
          },
          splitLine: { show: true, lineStyle: { type: 'solid', color: 'rgba(140,140,206,0.7)' } },
          axisLabel: { show: true, textStyle: { color: 'white', fontFamily: 'SimSun', fontWeight: 'bolder' } }

        },
        series: [
        {
          showSymbol: false,
          name: '预测负荷',
            data: [[0, 260.9], [1, 267.2], [2, 267.2], [3, 279.8], [4, 273.5],
[5, 271.4], [6, 284.0], [7, 272.45], [8, 296.6], [9, 281.9],
[10, 278.75], [11, 258.8], [12, 264.05], [13, 236.75], [14, 240.95],
[15, 224.15], [16, 240.95], [17, 224.15], [18, 233.6], [19, 208.4],
[20, 238.85], [21, 206.3], [22, 222.05], [23, 234.65], [24, 257.75]],
            type: 'line',
            color: '#ffc800',
            lineStyle:
            {
              width: 1
            }
          },
          {
          showSymbol: false,
            name: '实时负荷',
            lineStyle:
            {
              width: 1
            },
            data: [[0, 282.95], [1, 297.65], [2, 270.35], [3, 263.0], [4, 280.85],
[5, 271.4], [6, 263.0], [7, 249.35], [8, 260.9], [9, 246.2],
[10, 231.5], [11, 221.0], [12, 209.45], [13, 228.35], [14, 226.25],
[15, 225.2], [16, 244.1], [17, 259.85], [18, 252.5], [19, 248.3],
[20, 268.25], [21, 284.0], [22, 265.1], [23, 305.0], [24, 286.1]],
            type: 'line',
            color: 'rgb(0, 255, 200) '
          }
        ]
      }

      myChart.setOption(option)
    }
  }
}
</script>
a
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
/* 主布局：左右对齐 */
.content {
  display: flex;
  justify-content: space-between;
  gap: 20px;
  margin: 20px;
  align-items: stretch; /* 让左右两部分等高 */
}

/* 左侧容器（曲线图） */
.left-container {
  flex: 6;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* 右侧容器（误差统计） */
.right-container {
  flex: 4;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* 通用样式 */
.section, .error-box {
  padding: 20px;
  background-color: #f0f2f5;
  border-radius: 8px;
  border: 2px solid #1890ff;
  flex: 1; /* 让所有盒子填充满容器 */
}
.stats {
  display: flex;
  flex-direction: column;
  gap: 5px;
  padding: 5px;
}

/* 误差统计盒子 */
.error-box {
  background-color: #ffffff;
  border: 2px solid #1890ff;
  padding: 15px;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.station-info-box {
  background-color: #0a1d4d;
  border: 2px solid #00aaff;
  border-radius: 8px;
  width: 100%;
  padding: 15px;
  color: #ffffff;
  font-family: Arial, sans-serif;
}

.station-header {
  text-align: center;
  font-size: 18px;
  font-weight: bold;
  padding: 5px 0;
  border-bottom: 2px solid #00aaff;
  margin-bottom: 10px;
  color: rgb(27,243,248);;
}

.station-content {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.station-row {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 16px;
}

.label {
  min-width: 80px;
  color: #00c3ff;
}

.value {
  flex-grow: 1;
  color: #ffffff;
}

.icon-home::before {
  content: "🏠";
}

.icon-location::before {
  content: "📍";
}

.icon-altitude::before {
  content: "📏";
}

.install-info-box {
  background-color: #0a1d4d;
  border: 2px solid #00aaff;
  border-radius: 8px;
  padding: 15px;
  color: #ffffff;
}

.install-header {
  text-align: center;
  font-size: 18px;
  font-weight: bold;
  padding: 5px 0;
  border-bottom: 2px solid #00aaff;
  margin-bottom: 10px;
  color: rgb(27,243,248);
}

.install-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr); /* 2 列布局 */
  gap: 10px;
}

.install-item {
  display: flex;
  align-items: center;
  gap: 10px;
  background-color: rgba(255, 255, 255, 0.1);
  padding: 10px;
  border-radius: 5px;
}

.install-label {
  font-size: 14px;
  color: #00c3ff;
}

.install-value {
  font-size: 16px;
  font-weight: bold;
  color: #ffffff;
}

/* 图标模拟 */
.icon-capacity::before { content: "📅"; }
.icon-tracking::before { content: "⚙️"; }
.icon-inverter::before { content: "🔋"; }
.icon-module::before { content: "📦"; }
.icon-type::before { content: "🏢"; }
.icon-tilt::before { content: "📐"; }

.error-box {
  background-color: #0a1d4d; /* 与 install-info-box 统一 */
  border: 2px solid #00aaff; /* 与 install-info-box 统一 */
  border-radius: 8px;
  padding: 15px;
  color: #ffffff; /* 文字颜色统一 */
  font-family: Arial, sans-serif;
}

.error-header {
  text-align: center;
  font-size: 18px;
  font-weight: bold;
  padding: 5px 0;
  border-bottom: 2px solid #00aaff; /* 与 install-info-box 统一 */
  margin-bottom: 10px;
  color: #00aaff; /* 标题颜色统一 */
}

.error-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr); /* 2 列布局，与 install-info-box 统一 */
  gap: 10px; /* 间距与 install-info-box 统一 */
}

.error-item {
  display: flex;
  align-items: center;
  gap: 10px;
  background-color: rgba(255, 255, 255, 0.1); /* 背景色与 install-info-box 统一 */
  padding: 10px;
  border-radius: 5px; /* 圆角与 install-info-box 统一 */
}

.error-label {
  font-size: 14px;
  color: #00c3ff; /* 标签颜色与 install-info-box 统一 */
}

.error-value {
  font-size: 16px;
  font-weight: bold;
  color: #ffffff; /* 值颜色与 install-info-box 统一 */
}

/* 图标模拟 */
.icon-light::before { content: "☀️"; } /* 光照图标 */
.icon-wind::before { content: "🌬️"; } /* 风速图标 */
.icon-humidity::before { content: "💧"; } /* 湿度图标 */
.icon-temperature::before { content: "🌡️"; } /* 温度图标 */

.left-container {
  flex: 6;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.section {
  background-color: #0a1d4d; /* 背景色与右侧盒子统一 */
  border: 2px solid #00aaff; /* 边框颜色与右侧盒子统一 */
  border-radius: 8px; /* 圆角与右侧盒子统一 */
  padding: 15px; /* 内边距与右侧盒子统一 */
  color: #ffffff; /* 文字颜色与右侧盒子统一 */
  font-family: Arial, sans-serif;
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

.chart {
  height: 300px;
  background-color: #0a1d4d; /* 图表背景色 */
  border: 1px solid #d9d9d9; /* 图表边框 */
  border-radius: 5px; /* 图表圆角 */
  margin-top: 10px; /* 与标题的间距 */
}
</style>
