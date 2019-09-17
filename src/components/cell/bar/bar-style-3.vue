<template>
    <div class="chart_container">
        <div class="chart_div" :id='chartId'>
        </div>

    </div>
</template>

<script>
export default {
    props: {
        chartId: {
            type: String,
            default: "bar_style_3"
        }
    },
    data() {
        return {
            charts: ""
        }
    },
    mounted() {
        //   使用刚指定的配置项和数据显示图表。
        this.charts = this.initCharts();
        this.updateCharts();
    },
    methods: {
        initCharts() {
            const el = document.getElementById(this.chartId)
            const charts = this.$echarts.init(el)
            return charts
        },
        updateCharts() {
        var option = {
            textStyle: {
        color: 'rgb(177, 215, 255)'
    },
    title: {
    },
    tooltip : {
        trigger: 'axis',
        axisPointer: {
            type: 'cross',
            label: {
                backgroundColor: '#6a7985'
            }
        }
    },
    legend: {
        data:[
             {
               name:'邮件营销',
               textStyle: {
                    color: '#94c8ff'          // 图例文字颜色
               }
           },{
               name:'联盟广告',
               textStyle: {
                    color: '#94c8ff'          // 图例文字颜色
               }
           },{
               name:'视频广告',
               textStyle: {
                    color: '#94c8ff'          // 图例文字颜色
               }
           },{
               name:'直接访问',
               textStyle: {
                    color: '#94c8ff'          // 图例文字颜色
               }
           },{
               name:'搜索引擎',
               textStyle: {
                    color: '#94c8ff'          // 图例文字颜色
               }
           }]
    },
    toolbox: {
        feature: {
            saveAsImage: {}
        }
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
    },
    xAxis : [
        {
            type : 'category',
            boundaryGap : false,
            splitLine:{  
                            show:false  
                        }, 
            data : ['周一','周二','周三','周四','周五','周六','周日','周一','周二','周三','周四','周五','周六','周日','周一','周二','周三','周四','周五','周六','周日']
        }
    ],
    yAxis : [
        {
            type : 'value',
            splitLine:{  
                            show:false  
                        }, 
        }
    ],
    series : [
        {   
            name:'邮件营销',
            type:'line',
            stack: '总量',
            
            smooth:true, 
            data:[120, 132, 101, 134, 90, 230, 210,120, 132, 101, 134, 90, 230, 210,120, 132, 101, 134, 90, 230, 210]
            
        },
        {
            name:'联盟广告',
            type:'line',
            stack: '总量',
            
            smooth:true, 
            data:[220, 182, 191, 234, 290, 330, 310,220, 182, 191, 234, 290, 330, 310,220, 182, 191, 234, 290, 330, 310]
        },
        {
            name:'视频广告',
            type:'line',
            stack: '总量',
            
            smooth:true, 
            data:[150, 232, 201, 154, 190, 330, 410,150, 232, 201, 154, 190, 330, 410,150, 232, 201, 154, 190, 330, 410]
        },
        {
            name:'直接访问',
            type:'line',
            stack: '总量',
            
            smooth:true, 
            data:[320, 332, 301, 334, 390, 330, 320,320, 332, 301, 334, 390, 330, 320,320, 332, 301, 334, 390, 330, 320]
        },
        {
            name:'搜索引擎',
            type:'line',
            stack: '总量',
            smooth:true, 
            label: {
                normal: {
                    show: true,
                    position: 'top'
                }
            },
            
            data:[820, 932, 901, 934, 1290, 1330, 1320,820, 932, 901, 934, 1290, 1330, 1320,820, 932, 901, 934, 1290, 1330, 1320]
        }
    ]
};


            this.charts.setOption(option);
        }
    }

}
</script>

<style>
.chart_container{
    width:100%;
    height: 100%;
}
.chart_div{
    width:100%;
    height: 100%;
}
</style>
