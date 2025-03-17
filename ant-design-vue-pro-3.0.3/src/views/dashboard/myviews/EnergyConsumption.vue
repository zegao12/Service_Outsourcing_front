<template>
  <div class="dashboard">
    <header class="header">
      <h1 style="color: white;">AcrelEMS企业微电网能效管理平台</h1>
    </header>

    <div class="content">
      <!-- 企业信息和能耗概览 -->
      <section class="info-overview">
        <!-- 企业信息 -->
        <div class="company-info">
          <div class="new-info-box">
            <div class="title-row">
              <i class="icon-enterprise"></i>
              <h3 style="color: white;">企业信息</h3>
            </div>
            <!-- <div class="info-row">
              <i class="icon-platform"></i>
              <span class="info-label">企业</span>
              <a-input v-model="Enterprise" placeholder="平台机构" class="custom-input"/>
            </div> -->
            <div class="info-row">
              <i class="icon-code"></i>
              <span>信用编码: xxxx-xxxx-xxxx-xxxx</span>
            </div>
            <div class="info-row">
              <i class="icon-location"></i>
              <span>地址: 上海市嘉定区育绿路253号安科瑞电气</span>
            </div>
            <div class="stats-row">
              <div class="stat-item">
                <div class="stat-circle purple">
                  <span class="stat-value">103</span>
                  <span class="stat-label">能源站点</span>
                </div>
              </div>
              <div class="stat-item">
                <div class="stat-circle blue">
                  <span class="stat-value">341<span class="red-text">(226)</span></span>
                  <span class="stat-label">网关</span>
                </div>
              </div>
              <div class="stat-item">
                <div class="stat-circle green">
                  <span class="stat-value">45<span class="red-text">(34)</span></span>
                  <span class="stat-label">监测点</span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- 能耗概览 -->
        <div class="energy-overview">
          <div class="title-row">
            <i class="icon-category-energy"></i>
            <h3 style="color: white;">分类能耗</h3>
          </div>
          <div class="energy-items">
            <div class="energy-item electrical">
              <div class="icon-and-data">
                <div class="icon-box">
                  <i class="icon-electricity"></i>
                </div>
                <div class="data-box">
                  <div class="energy-details">
                    <h3 style="font-size: 24px; color: #00bfff; text-align: left;">电</h3>
                    <div class="daily-data">
                      <span style="color: rgba(255, 255, 255, 0.6);">当日 </span>
                      <span style="color: white; font-size: 20px;">6404.0 kW·h</span>
                    </div>
                    <div class="daily-data">
                      <span style="color: rgba(255, 255, 255, 0.6);">昨日 </span>
                      <span style="color: white; font-size: 20px;">3393.2 kW·h</span>
                    </div>
                    <div class="trend-indicator">
                      <div class="change-column">
                        <span class="change-icon" style="color: red;">↑</span>
                        <span class="change-value" style="color: red;">88.7%</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="compare-data electrical-compare">
                <div class="data-group">
                  <span class="data-title">当月</span>
                  <div class="progress-bar">
                    <div class="progress" style="width: 30%; background-color: #00bfff;"></div>
                  </div>
                  <span class="data-value">293714.46kW·h</span>
                </div>
                <div class="data-group">
                  <span class="data-title">上月</span>
                  <div class="progress-bar">
                    <div class="progress" style="width: 32%; background-color: #00bfff;"></div>
                  </div>
                  <span class="data-value">294943.38kW·h</span>
                  <div class="change-column"></div>
                </div>
                <div class="change-column">
                  <span class="change-icon" style="color: green;">↓</span>
                  <span class="change-value" style="color: green;">-0.4%</span>
                </div>
                <div class="data-group">
                  <span class="data-title">今年</span>
                  <div class="progress-bar">
                    <div class="progress" style="width: 35%; background-color: #00bfff;"></div>
                  </div>
                  <span class="data-value">602807.04kW·h</span>
                </div>
                <div class="data-group">
                  <span class="data-title">去年</span>
                  <div class="progress-bar">
                    <div class="progress" style="width: 28%; background-color: #00bfff;"></div>
                  </div>
                  <span class="data-value">501615.5kW·h</span>
                  <div class="change-column"></div>
                </div>
                <div class="change-column">
                  <span class="change-icon" style="color: red;">↑</span>
                  <span class="change-value" style="color: red;">20.2%</span>
                </div>
              </div>
            </div>
            <div class="energy-item water">
              <div class="icon-and-data">
                <div class="icon-box">
                  <i class="icon-water"></i>
                </div>
                <div class="data-box">
                  <div class="energy-details">
                    <h3 style="font-size: 24px; color: #00bfff; text-align: left;">水</h3>
                    <div class="daily-data">
                      <span style="color: rgba(255, 255, 255, 0.6);">当日 </span>
                      <span style="color: white; font-size: 20px;">2411.5 m³</span>
                    </div>
                    <div class="daily-data">
                      <span style="color: rgba(255, 255, 255, 0.6);">昨日 </span>
                      <span style="color: white; font-size: 20px;">1532.5 m³</span>
                    </div>
                    <div class="trend-indicator">
                      <div class="change-column">
                        <span class="change-icon" style="color: red;">↑</span>
                        <span class="change-value" style="color: red;">57.4%</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="compare-data water-compare">
                <div class="data-group">
                  <span class="data-title">当月</span>
                  <div class="progress-bar">
                    <div class="progress" style="width: 10%; background-color: #00ff7f;"></div>
                  </div>
                  <span class="data-value">113546.5m³</span>
                </div>
                <div class="data-group">
                  <span class="data-title">上月</span>
                  <div class="progress-bar">
                    <div class="progress" style="width: 90%; background-color: #00ff7f;"></div>
                  </div>
                  <span class="data-value">4611142m³</span>
                  <div class="change-column"></div>
                </div>
                <div class="change-column">
                  <span class="change-icon" style="color: green;">↓</span>
                  <span class="change-value" style="color: green;">-97.5%</span>
                </div>
                <div class="data-group">
                  <span class="data-title">今年</span>
                  <div class="progress-bar">
                    <div class="progress" style="width: 20%; background-color: #00ff7f;"></div>
                  </div>
                  <span class="data-value">4731924m³</span>
                  <div class="change-column"></div>
                </div>
                <div class="data-group">
                  <span class="data-title">去年</span>
                  <div class="progress-bar">
                    <div class="progress" style="width: 0%; background-color: #00ff7f;"></div>
                  </div>
                  <span class="data-value">-</span>
                  <div class="change-column"></div>
                </div>
                <div class="change-column">
                  <span class="change-icon" style="color: red;"></span>
                  <span class="change-value" style="color: red;">--%</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- 统计图表 -->
      <div class="charts">
        <div class="title-row">
          <i class="icon-trend"></i>
          <h3 style="color: white;">用能趋势</h3>
        </div>
        <div class="content1">
          <div class="section left">
            <div class="section-header ">超短时功率预测曲线 (4小时)</div>
            <div class="chart" ref="shortTermChart"></div>
          </div>
          <div class="section right" padding="20px">
            <div class="section-header ">超短时功率预测曲线 (4小时)</div>
            <div class="chart" ref="ultraShortTermChart"></div>
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
.dashboard {
  font-family: Arial, sans-serif;
  background: #0a1f44;
  color: white;
  padding: 10px;
}
.title-row {
  font-size: 20px;
  color: white;
}
.header {
  text-align: center;
  padding: 10px;
  color:white;
  font-size:25px;
  font-weight: bold;
}
.content {
  display: grid;
  gap: 20px;
  grid-template-columns: 1fr;
}
.info-overview {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}
.company-info,
.energy-overview {
  background: #0a1d4d;
  padding: 20px;
  border-radius: 10px;
}
.chart-placeholder {
  background: #555;
}
.horizontal-chart {
  height: 40px;
  width: 200px;
  margin-top: 10px;
}

/* 新增和修改的样式 */
.new-info-box {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.title-row {
  display: flex;
  align-items: center;
  gap: 5px;
}
.info-row {
  display: flex;
  align-items: center;
  gap: 5px;
  margin-top: 2px;
}
.icon-enterprise::before {
  content: "🏢";
}
.icon-code::before {
  content: "🔢";
}
.icon-location::before {
  content: "📍";
}
.stats-row {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-top: 45px;
}
.stat-item {
  text-align: center;
}
.stat-circle {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  border: 3px solid;
  background-clip: padding-box;
}
.purple {
  background: linear-gradient(to bottom, rgba(138, 43, 226, 0) 0%, #b33fc7 83%, white 100%);
  border-color: #b33fc7;
  box-shadow: 0 0 10px rgba(156, 39, 176, 0.5);
}
.blue {
  background: linear-gradient(to bottom, rgba(3, 169, 244, 0) 0%, #03a9f4 83%, white 100%);
  border-color: #03a9f4;
  box-shadow: 0 0 10px rgba(3, 169, 244, 0.5);
}
.green {
  background: linear-gradient(to bottom, rgba(76, 175, 80, 0) 0%, #4caf50 83%, white 100%);
  border-color: #4caf50;
  box-shadow: 0 0 10px rgba(76, 175, 80, 0.5);
}
.stat-value {
  font-size: 24px;
  font-weight: bold;
}
.stat-label {
  font-size: 14px;
}
.red-text {
  color: red;
}
.custom-input {
  background-color: transparent;
  color: white;
  width: 250px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 5px;
  padding: 5px;
}
.info-label {
  margin-right: 10px;
}

/* 能耗概览样式 */
.energy-overview {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
.energy-items {
  display: flex;
  justify-content: space-between;
  gap: 5px;
}
.energy-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  width: 49%;
}
.icon-and-data {
  display: flex;
  justify-content: space-around;
  width: 100%;
}
.icon-box {
  width: 60px;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.icon-electricity::before {
  content: "⚡";
  font-size: 30px;
}
.icon-water::before {
  content: "💧";
  font-size: 30px;
}
.data-box {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.energy-details {
  margin-bottom: 2px; /* 减小间距 */
  width: 100%;
}
.daily-data {
  margin-bottom: 5px;
}
.trend-indicator {
  color: red;
  margin-bottom: 10px;
  width: 100%; /* 确保宽度占满父元素 */
}
.electrical {
  color: #00bfff;
}
.water {
  color: #00ff7f;
}

.compare-data {
  margin-top: 2px; /* 减小间距 */
  display: flex;
  flex-direction: column;
  width: 100%;
}
.electrical-compare,
.water-compare {
  width: 100%;
  display: flex;
  justify-content: space-around;
  background-color: rgba(255, 255, 255, 0.1);
  padding: 8px;
}
.data-group {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 5px;
  width: 100%;
}
.data-title {
  color: white;
  text-align: left;
  min-width: 60px;
}
.progress-bar {
  width: 80px;
  height: 10px;
  background-color: #555;
  border-radius: 5px;
  overflow: hidden;
}
.progress {
  height: 100%;
  width: 100%;
  box-sizing: border-box;
}
.change-column {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-end;
  flex-grow: 1; /* 占据剩余空间 */
}
.change-icon {
  margin-right: 5px;
}
.change-value {
  margin: 0;
}
.daily-data span:last-child {
  margin-left: 20px; /* 调整数据与前面的文字间距 */
}
.icon-category-energy::before {
  content: "📊"; /* 示例图标，可替换为合适的图标字符或使用字体图标等 */
  margin-right: 5px;
}
.title-row {
  font-size: 20px;
  color: white;
  display: flex;
  align-items: center;
  gap: 5px;
}
.content1 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5px;
    margin-top: 10px;
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
.section-header {
  text-align: center;
  font-size: 18px;
  font-weight: bold;
  padding: 5px 0;
  border-bottom: 2px solid #00aaff; /* 标题下划线与右侧盒子统一 */
  margin-bottom: 10px;
  color: rgb(27,243,248); /* 标题颜色与右侧盒子统一 */
}
.icon-trend::before {
  content: "📈";
  font-size: 20px;
  vertical-align: middle;
}
.charts {
  background: #0a1d4d;
  padding: 20px;
  border-radius: 10px;
}
</style>
