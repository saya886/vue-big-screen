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
            default: "map_style_1"
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
        var option = ""


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
