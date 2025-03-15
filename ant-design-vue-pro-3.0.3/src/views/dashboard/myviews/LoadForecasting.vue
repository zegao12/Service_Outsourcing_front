<template>
  <div class="app-container">
    <div class="header">
      <div>返回首页</div>
      <div>安科瑞功率预测系统</div>
      <div>注销</div>
    </div>

    <div class="content">
      <div class="section left">
        <h3>短时功率预测曲线 (3天)</h3>
        <div class="chart"></div>
      </div>

      <div class="section right">
        <h3>预测误差 (3天)</h3>
        <div class="stats">
          <div>均方根: 0.16</div>
          <div>平均绝对误差: 0.1</div>
          <div>相关性系数: -0.04</div>
          <div>最大预测误差: 44.9</div>
          <div>合格率: 83.15%</div>
        </div>
      </div>

      <div class="section left">
        <h3>超短时功率预测曲线 (4小时)</h3>
        <div class="chart"></div>
      </div>

      <div class="section right">
        <h3>预测误差 (4小时)</h3>
        <div class="stats">
          <div>均方根: 0.12</div>
          <div>平均绝对误差: 0.09</div>
          <div>相关性系数: 0.01</div>
          <div>最大预测误差: 49.1</div>
          <div>合格率: 90.15%</div>
        </div>
      </div>
    </div>
  </div>
</template>

  <script>
  export default {
    name: 'PowerPredictionUI'
  }
  </script>

  <style scoped>
  .app-container { background-color: #e6f7ff; color: #1890ff; font-family: Arial, sans-serif; min-height: 100vh; overflow-y: auto; }
  .header { display: flex; justify-content: space-between; background-color: #1890ff; color: #ffffff; padding: 10px; }
  .content { display: grid; grid-template-columns: 7fr 3fr; gap: 20px; margin: 20px; }
  .section { padding: 20px; background-color: #f0f2f5; border-radius: 8px; border: 2px solid #1890ff; }
  .chart { height: 300px; background-color: #ffffff; border: 1px solid #d9d9d9; }
  .stats { display: flex; flex-direction: column; gap: 5px; padding: 5px; }
  </style>
