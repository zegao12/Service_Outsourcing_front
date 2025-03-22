<template>
  <div class="dashboard">
    <header class="header">
      <h1 style="color: white;">A企业微电网能效管理平台</h1>
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
              <span>地址: 杭州市下沙区学源街xxx号</span>
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
            <div
              style=" text-align: center;
              font-size: 18px;
              font-weight: bold;
              padding: 5px 0;margin-bottom: 0px;font-weight: 1000;font-size: 22px;" >
              当日逐时趋势
            </div>
            <!-- <div class="section-header" style="text-align: left;font-size: large;color: white;">负荷-气温曲线</div> -->
            <div class="chart" ref="shortTermChart" ></div>

          </div>
          <div class="section right" padding="20px">
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
    window.addEventListener('resize', this.resizeCharts)
  },
  beforeDestroy () {
    window.removeEventListener('resize', this.resizeCharts)
  },
  methods: {
    initShortTermChart () {
      const chartDom = this.$refs.shortTermChart
      const myChart = echarts.init(chartDom, { height: 400 })
      const option = {
        tooltip: {
    trigger: 'axis'
  },
  toolbox: {
                show: true,
                feature: {
                    dataZoom: {
                        yAxisIndex: 'none'
                    },
                    dataView: { readOnly: false },
                    magicType: { type: ['line', 'bar'] },
                    restore: {},
                    saveAsImage: {}
                }
            },
        grid: {
            left: '3%',
            right: '4%',
            bottom: '15%',
            containLabel: true
        },
        legend: {
          data: [
        {
            name: '今日',
             icon: 'path://M2,2 h20 a5,5 0 0 1 5,5 v10 a5,5 0 0 1 -5,5 h-20 a5,5 0 0 1 -5,-5 v-10 a5,5 0 0 1 5,-5 z',
            itemStyle: {
                color: 'rgba(174,164,231,1)',
                width: 20
            }
        },
        {
            name: '昨日',
            icon: 'path://M2,2 h20 a5,5 0 0 1 5,5 v10 a5,5 0 0 1 -5,5 h-20 a5,5 0 0 1 -5,-5 v-10 a5,5 0 0 1 5,-5 z',
            itemStyle: {
                color: 'rgb(24, 225, 230)',
                width: 20,
                borderRadius: 8
            }
        }
    ],
            textStyle: {
              color: 'white'
            },
            bottom: '0%',
            left: 'center',
            orient: 'horizontal', // 水平排列
            icon: 'rect',
            itemStyle: {
                borderRadius: 8
            }
        },
        xAxis: { splitLine: { show: false },
        axisLabel: {
                    textStyle: {
                        color: 'white'
                    },
                    formatter: function (value) {
                        return value + '时'
                    }
                },
                data: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24]
      },
        yAxis: { splitLine: { show: true, lineStyle: { type: 'solid', color: 'rgba(128,128,128,0.5)' } },
name: 'kw·h',
nameLocation: 'end',
      nameGap: 30,
      nameTextStyle: {
        color: 'white',
        fontSize: 14
      },
textStyle: { color: 'white' } },
        series: [{
          name: '今日',
          data: [
                        100, 150, 200, 300, 450, 550, 580, 520, 450, 350, 250, 180, 120
                    ],
          type: 'line',
          areaStyle: {
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                        offset: 0,
                        color: 'rgba(174,164,231,1)'
                    },
                    {
                        offset: 1,
                        color: 'rgba(174,164,231, 0)'
                    }
                ])
            },
          lineStyle: {
        color: 'rgba(174,164,231,1)'
    },
          smooth: true
        },
        {
          name: '昨日',
          data: [
                        120, 130, 140, 160, 180, 200, 220, 240, 230, 210, 190, 170, 150
                    ],
          type: 'line',
          areaStyle: {
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                        offset: 0,
                        color: 'rgba(24, 225, 230, 1)'
                    },
                    {
                        offset: 1,
                        color: 'rgba(24, 225, 230, 0)'
                    }
                ])
            },
          lineStyle: {
        color: 'rgb(24, 225, 230)'
    },
          smooth: true
        }
      ]
      }
      myChart.setOption(option)
      this.shortTermChart = myChart
    },
    initUltraShortTermChart () {
      const chartDom = this.$refs.ultraShortTermChart
      const myChart = echarts.init(chartDom, { height: 400 })
      const option = {
  tooltip: {
    trigger: 'axis'
  },
  legend: {
    data: ['当月', '上月'],
    textStyle: {
      color: 'white'
    }
  },
  toolbox: {
    show: true,
    feature: {
      dataView: { show: true, readOnly: false },
      magicType: { show: true, type: ['line', 'bar'] },
      restore: { show: true },
      saveAsImage: { show: true }
    }
  },
  calculable: true,
  xAxis: [
    {
      type: 'category',
      data: ['1日', '3日', '5日', '7日', '9日', '11日', '13日', '15日', '17日', '19日', '21日', '23日', '25日', '27日', '29日', '31日'],
      axisLabel: {
        color: 'white'
    }
  }
  ],
  yAxis: [
    {
      type: 'value',
      name: 'kw·h',
      nameLocation: 'end',
      nameGap: 30,
      nameTextStyle: {
        color: 'white',
        fontSize: 14
      },
      splitLine: {
                show: true, // 是否显示分隔线，默认为 true
                lineStyle: {
                    color: 'rgba(128,128,128,0.5)',
                    width: 1, // 分隔线宽度
                    type: 'solid' // 分隔线样式，'solid' 为实线，'dashed' 为虚线
                }
            }
    }
  ],
  series: [
    {
      name: '当月',
      type: 'bar',
      data: [
5200, 12800, 3400, 16500, 4100, 14300, 7800, 17900, 3200, 15600, 6700, 13200, 9100, 17100, 4500, 16200,
8300, 11800, 12400, 17600, 3900, 13700, 7400, 15900, 5800, 18100, 4900, 14700, 8600, 16300, 6100
],
      lineStyle: {
        color: 'rgb(46,200,206)'
      },
      itemStyle: {
        color: 'rgb(46,200,206)'
      }
    },
    {
      name: '上月',
      type: 'bar',
      data: [
3600, 14900, 5300, 16800, 3900, 12100, 8700, 17300, 4400, 15200, 7200, 13900, 10200, 16600, 4700, 15800,
9500, 11400, 13100, 17800, 3700, 14200, 7900, 16400, 6300, 18300, 5100, 15100, 9300, 16700, 6600
],

      lineStyle: {
        color: 'rgb(174,164,231)'
      },
      itemStyle: {
        color: 'rgb(174,164,231)'
      }
    }
  ]
}
      myChart.setOption(option)
      this.ultraShortTermChart = myChart
    },
    resizeCharts () {
      if (this.shortTermChart) {
        const chartDom = this.$refs.shortTermChart
        // 获取容器的实际宽度和高度
        const width = chartDom.offsetWidth
        const height = chartDom.offsetHeight
        this.shortTermChart.resize({ width, height })
      }
      if (this.ultraShortTermChart) {
        const chartDom = this.$refs.ultraShortTermChart
        const width = chartDom.offsetWidth
        const height = chartDom.offsetHeight
        this.ultraShortTermChart.resize({ width, height })
      }
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
  padding: 15px; /* 内边距与右侧盒子统一 */
  color: #ffffff; /* 文字颜色与右侧盒子统一 */
  font-family: Arial, sans-serif;
}
.chart {
  /* display: absolute;
  bottom: 0px; */
  height: 500px;
  margin-top: 10px; /* 与标题的间距 */
  align-self: center;
  width: 100%;
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
