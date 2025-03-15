<template>
  <div class="app-container">
    <div class="header">
      <div>返回首页</div>
      <div>安科瑞功率预测系统</div>
      <div>注销</div>
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
              <span class="value">安科瑞电气股份有限公司</span>
            </div>
            <div class="station-row">
              <i class="icon-location"></i>
              <span class="label">经纬度</span>
              <span class="value">北纬31°14′，东经121°39′</span>
            </div>
            <div class="station-row">
              <i class="icon-altitude"></i>
              <span class="label">海拔高度</span>
              <span class="value">2.19米</span>
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

      const option = {
        xAxis: {
          type: 'category',
          data: ['0', '12', '24', '36', '48', '60', '72']
        },
        yAxis: {
          type: 'value'
        },
        series: [
          {
            data: [120, 200, 150, 80, 70, 110, 130, 100],
            type: 'line',
            smooth: true
          }
        ]
      }

      myChart.setOption(option)
    },
    initUltraShortTermChart () {
      const chartDom = this.$refs.ultraShortTermChart
      const myChart = echarts.init(chartDom)

      const option = {
        xAxis: {
          type: 'category',
          data: ['Hour 1', 'Hour 2', 'Hour 3', 'Hour 4']
        },
        yAxis: {
          type: 'value'
        },
        series: [
          {
            data: [30, 50, 40, 60, 55, 45, 35],
            type: 'line',
            smooth: true
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
  background-color: #e6f7ff;
  color: #1890ff;
  font-family: Arial, sans-serif;
  min-height: 100vh;
  overflow-y: auto;
}
.header {
  display: flex;
  justify-content: space-between;
  background-color: #1890ff;
  color: #ffffff;
  padding: 10px;
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
  flex: 7;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* 右侧容器（误差统计） */
.right-container {
  flex: 3;
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

.chart {
  height: 300px;
  background-color: #ffffff;
  border: 1px solid #d9d9d9;
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
  color: #00aaff;
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
  color: #00aaff;
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
  flex: 7;
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
  color: #00aaff; /* 标题颜色与右侧盒子统一 */
}

.chart {
  height: 300px;
  background-color: #ffffff; /* 图表背景色 */
  border: 1px solid #d9d9d9; /* 图表边框 */
  border-radius: 5px; /* 图表圆角 */
  margin-top: 10px; /* 与标题的间距 */
}
</style>
