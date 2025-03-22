<template>
  <page-header-wrapper>
    <a-card :bordered="false">
      <!-- 搜索区域 -->
      <div class="table-page-search-wrapper">
        <a-form layout="inline">
          <a-row :gutter="48">
            <a-col :md="8" :sm="24">
              <a-form-item label="日期">
                <a-date-picker v-model="queryParam.date" style="width: 100%" placeholder="请选择日期" />
              </a-form-item>
            </a-col>
            <a-col :md="8" :sm="24">
              <a-form-item label="时间">
                <a-select v-model="queryParam.time" placeholder="请选择时间" default-value="0">
                  <a-select-option value="0">5分钟</a-select-option>
                  <a-select-option value="1">10分钟</a-select-option>
                  <a-select-option value="2">15分钟</a-select-option>
                  <a-select-option value="3">30分钟</a-select-option>
                </a-select>
              </a-form-item>
            </a-col>
          </a-row>

          <a-row :gutter="48">
            <a-col :md="8" :sm="24">
              <a-form-item label="">
                <a-select v-model="queryParam.reportType" placeholder="请选择需要查看的报表" default-value="0">
                  <a-select-option value="0">电量报表</a-select-option>
                  <a-select-option value="1">电流电压频率报表</a-select-option>
                  <a-select-option value="2">功率报表</a-select-option>
                  <a-select-option value="3">功率因素报表</a-select-option>
                  <a-select-option value="4">四象限无功总电能</a-select-option>
                  <a-select-option value="5">日用电量报表</a-select-option>
                  <a-select-option value="6">月用电量报表</a-select-option>
                </a-select>
              </a-form-item>
            </a-col>
            <a-col :md="8" :sm="24">
              <a-form-item label="">
                <a-select v-model="queryParam.headquarters" placeholder="请选择总部" default-value="">
                  <a-select-option value="0">澳蓝福州总部</a-select-option>
                </a-select>
              </a-form-item>
            </a-col>
            <a-col :md="8" :sm="24">
              <span class="table-page-search-submitButtons">
                <a-button type="primary" @click="handleSearch">查询</a-button>
                <a-button style="margin-left: 8px" @click="handleReset">重置</a-button>
              </span>
            </a-col>
          </a-row>
        </a-form>
      </div>

      <!-- 表格区域 -->
      <s-table
        :columns="columns"
        :data="loadData"
        :pagination="false"
      >
        <span slot="serial" slot-scope="text, record, index">
          {{ index + 1 }}
        </span>
      </s-table>
    </a-card>
  </page-header-wrapper>
</template>

<script>
import moment from 'moment'
import { STable } from '@/components'

const columns = [
  {
    title: '日期',
    dataIndex: 'date'
  },
  {
    title: '区域',
    dataIndex: 'region3'
  },
  {
    title: '负荷(kW)',
    dataIndex: 'device'
  },
  {
    title: '温度(℃)',
    dataIndex: 'meterAddress'
  },
  {
    title: '倍率（变比）',
    dataIndex: 'ratio'
  },
  {
    title: '正向有功总',
    dataIndex: 'activePower'
  },
  {
    title: '正向无功总',
    dataIndex: 'reactivePower'
  },
  {
    title: '反向有功总',
    dataIndex: 'reverseActivePower'
  },
  {
    title: '反向无功总',
    dataIndex: 'reverseReactivePower'
  }
]

export default {
  name: 'EnergyReport',
  components: {
    STable
  },
  data () {
    return {
      columns,
      queryParam: {
        date: moment(),
        region: '0'
      },
      loadData: parameter => {
        const requestParameters = Object.assign({}, parameter, this.queryParam)
        console.log('loadData request parameters:', requestParameters)
        return this.getReportData(requestParameters)
      }
    }
  },
  methods: {
    handleSearch () {
      this.$refs.table.refresh(true)
    },
    handleReset () {
      this.queryParam = {
        date: moment(),
        region: '0'
      }
      this.$refs.table.refresh(true)
    },
    getReportData () {
      // 模拟数据
      const data = [
        {
          key: '1',
          date: '2021-06-01 17:55',
          region3: '1号表',
          device: '	157.6',
          meterAddress: '28.5',
          ratio: '0.5',
          activePower: '143.23',
          reactivePower: '23.92',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '2',
          date: '2021-06-01 17:50',
          region3: '3号表',
          device: '	140.2',
          meterAddress: '28.3',
          ratio: '0.5',
          activePower: '132.63',
          reactivePower: '20.32',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '3',
          date: '2021-06-01 17:45',
          region3: '6号表',
          device: '	160.8',
          meterAddress: '28.6',
          ratio: '0.5',
          activePower: '145.03',
          reactivePower: '22.41',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '4',
          date: '2021-06-01 17:40',
          region3: '4号表',
          device: '	130.5',
          meterAddress: '27.9',
          ratio: '0.5',
          activePower: '123.92',
          reactivePower: '24.09',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '5',
          date: '2021-06-01 17:35',
          region3: '8号表',
          device: '	115.9',
          meterAddress: '27.6',
          ratio: '0.5',
          activePower: '109.83',
          reactivePower: '19.92',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '6',
          date: '2021-06-01 17:30',
          region3: '2号表',
          device: '168.3',
          meterAddress: '28.8',
          ratio: '0.5',
          activePower: '152.32',
          reactivePower: '31.09',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '7',
          date: '2021-06-01 17:25',
          region3: '4号表',
          device: '145.7',
          meterAddress: '28.2',
          ratio: '0.5',
          activePower: '132.63',
          reactivePower: '20.32',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '8',
          date: '2021-06-01 17:20',
          region3: '10号表',
          device: '158.2',
          meterAddress: '28.7',
          ratio: '0.5',
          activePower: '145.03',
          reactivePower: '22.41',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '9',
          date: '2021-06-01 17:15',
          region3: '5号表',
          device: '128.6',
          meterAddress: '28.0',
          ratio: '0.5',
          activePower: '123.92',
          reactivePower: '24.09',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '10',
          date: '2021-06-01 17:10',
          region3: '8号表',
          device: '113.4',
          meterAddress: '27.8',
          ratio: '0.5',
          activePower: '109.83',
          reactivePower: '19.92',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '11',
          date: '2021-06-01 17:05',
          region3: '11号表',
          device: '170.1',
          meterAddress: '28.9',
          ratio: '0.5',
          activePower: '152.32',
          reactivePower: '31.09',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '12',
          date: '2021-06-01 17:00',
          region3: '12号表',
          device: '	155.5',
          meterAddress: '28.5',
          ratio: '0.5',
          activePower: '146.98',
          reactivePower: '26.63',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        },
        {
          key: '',
          date: '',
          region1: '',
          region2: '',
          region3: '',
          device: '',
          meterAddress: '',
          ratio: '总计',
          activePower: '1520.34',
          reactivePower: '301.28',
          reverseActivePower: '0',
          reverseReactivePower: '0'
        }
      ]
      return Promise.resolve({
        data,
        total: data.length,
        pageSize: 13,
        current: 1
      })
    }
  }
}
</script>

<style scoped>
.table-page-search-wrapper {
  margin-bottom: 20px;
}
</style>
