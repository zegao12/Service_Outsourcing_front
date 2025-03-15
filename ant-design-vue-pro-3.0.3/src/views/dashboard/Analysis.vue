<template>
  <div class="app-container">
    <div class="header">
      <div class="header-item">返回首页</div>
      <div class="header-title">安科瑞功率预测系统</div>
      <div class="header-item">注销</div>
    </div>

    <div class="content">
      <div class="section" width="100px">
        <h3>短时功率预测曲线 (3天)</h3>
        <div class="chart"></div>
      </div>
      <div class="section">
        <h3>预测误差 (3天)</h3>
        <div class="stats">
          <div>均方根: 0.16</div>
          <div>平均绝对误差: 0.1</div>
          <div>相关性系数: -0.04</div>
          <div>最大预测误差: 44.9</div>
          <div>合格率: 83.15%</div>
        </div>
      </div>

      <div class="section">
        <h3>超短时功率预测曲线 (4小时)</h3>
        <div class="chart"></div>
      </div>

      <div class="section">
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
.app-container { background-color: #f5f7fa; color: #003a8c; font-family: Arial, sans-serif; min-height: 100vh; padding: 20px; box-sizing: border-box; }
.header { display: flex; justify-content: space-around; background-color: #003a8c; color: #ffffff; padding: 15px 0; border-radius: 12px; margin-bottom: 20px; }
.header-item, .header-title { flex: 1; text-align: center; font-weight: bold; }
.content { display: flex; flex-wrap: wrap; gap: 20px;width:100%; }
.section {flex: 1 1 calc(50% - 10px); background-color: #ffffff; border: 2px solid #003a8c; border-radius: 12px; padding: 20px; box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); }
.chart { height: 300px; background-color: #f0f2f5; border: 1px solid #d9d9d9; border-radius: 8px; }
.stats { display: flex; flex-direction: column; gap: 8px; padding: 10px; }
</style>
