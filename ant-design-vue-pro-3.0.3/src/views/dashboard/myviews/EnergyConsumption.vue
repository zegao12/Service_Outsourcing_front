<template>
  <div class="dashboard">
    <header class="header">
      <h1>AcrelEMS企业微电网能效管理平台</h1>
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
            <div class="info-row">
              <i class="icon-code"></i>
              <span>信用编码: xxxx-xxxx-xxxx-xxxx</span>
            </div>
            <div class="info-row">
              <i class="icon-location"></i>
              <span>地址: 上海市嘉定区育绿路253号安科瑞电气</span>
            </div>
            <!-- 新增能源站点、网关、监测点展示 -->
            <div class="stats-row">
              <div class="stat-item">
                <div class="stat-circle purple">
                  <span class="stat-value">103</span>
                  <span class="stat-label">能源站点</span>
                </div>
              </div>
              <div class="stat-item">
                <div class="stat-circle blue">
                  <span class="stat-value">341(226)</span>
                  <span class="stat-label">网关</span>
                </div>
              </div>
              <div class="stat-item">
                <div class="stat-circle green">
                  <span class="stat-value">45(34)</span>
                  <span class="stat-label">监测点</span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- 能耗概览 -->
        <div class="energy-overview">
          <div class="overview-box">
            <h3 style="color: white;">电</h3>
            <p>当日: 6404.0 kW·h</p>
            <p>昨日: 3393.2 kW·h</p>
          </div>
          <div class="overview-box">
            <h3 style="color: white;">水</h3>
            <p>当日: 2411.5 m³</p>
            <p>昨日: 1532.5 m³</p>
          </div>
        </div>
      </section>

      <!-- 统计图表 -->
      <section class="charts">
        <img src="/placeholder.png" alt="当日用能趋势" class="chart-placeholder" />
        <img src="/placeholder.png" alt="月度用能分析" class="chart-placeholder" />
      </section>
    </div>
  </div>
</template>

  <script>
  export default {
    name: 'EnergyConsumption'
  }
  </script>

  <style scoped>
  .dashboard {
    font-family: Arial, sans-serif;
    background: #0a1f44;
    color: white;
    padding: 20px;
  }
  .title-row {
    font-size: 20px;
    color: white;
  }
  .header {
    text-align: center;
    padding: 10px;
  }
  .content {
    display: grid;
    gap: 20px;
    grid-template-columns: 1fr;
  }
  .info-overview {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
  .company-info,
  .energy-overview {
    background: #0a1d4d;
    padding: 20px;
    border-radius: 10px;
  }
  .overview-box {
    margin-bottom: 10px;
  }
  .chart-placeholder {
    width: 100%;
    height: 200px;
    background: #ddd;
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
      background: linear-gradient(to bottom, rgba(138, 43, 226, 0) 0%, #883dd4 83%, white 100%);
      border-color: #883dd4;
      box-shadow: 0 0 10px rgba(142, 40, 236, 0.5);
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
  </style>
