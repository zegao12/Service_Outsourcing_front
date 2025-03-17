<template>
  <page-header-wrapper>
    <a-card :bordered="false">
      <div class="table-page-search-wrapper">
        <a-form layout="inline">
          <a-row :gutter="48">
            <a-col :md="8" :sm="24">
              <a-form-item suffix-icon="clock-circle">
                <a-input v-model="queryParam.startTime" placeholder="开始时间"/>
              </a-form-item>
            </a-col>
            <a-col :md="8" :sm="24">
              <a-form-item suffix-icon="clock-circle">
                <a-input v-model="queryParam.endTime" placeholder="结束时间"/>
              </a-form-item>
            </a-col>
            <a-col :md="8" :sm="24">
              <a-form-item suffix-icon="search">
                <a-input-search v-model="queryParam.event" placeholder="事件"/>
              </a-form-item>
            </a-col>
          </a-row>
        </a-form>
      </div>

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
    title: '时间',
    dataIndex: 'date'
  },
  {
    title: '事件',
    dataIndex: 'event'
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
          date: '2020-09-08 09:06:26',
          event: '线路检测：接口(eth1)断开.'
        },
        {
          key: '2',
          date: '2020-09-07 23:25:49',
          event: '升级DPI特征库成功'
        },
        {
          key: '3',
          date: '2020-09-07 23:25:49',
          event: '更新文件: IKprotocol_2.0.152.lib'
        },
        {
          key: '4',
          date: '2020-09-07 15:43:57',
          event: '线路检测: (wan1)线路检测成功'
        },
        {
          key: '5',
          date: '2020-09-07 15:43:53',
          event: '线路检测: 接口(eth5)连接.'
        },
        {
          key: '6',
          date: '2020-09-07 15:43:27',
          event: '线路检测: (wan1)线路检测失败'
        },
        {
          key: '7',
          date: '2020-09-07 15:43:25',
          event: '线路检测: 接口(eth5)断开.'
        },
        {
          key: '8',
          date: '2020-09-07 15:23:22',
          event: '线路检测: 接口(eth1)连接.'
        },
        {
          key: '9',
          date: '2020-09-07 10:25:47',
          event: '系统启动'
        },
        {
          key: '10',
          date: '2020-09-07 10:25:36',
          event: '线路检测: (wan1)线路检测成功'
        },
        {
          key: '11',
          date: '2020-09-07 10:24:58',
          event: '线路检测: 接口(eth5)连接.'
        },
        {
          key: '12',
          date: '2020-09-07 10:24:55',
          event: '线路检测: 接口(eth5)断开.'
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
