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
            default: "ball_style_2"
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
                backgroundColor: '#000',
                globe: {
                    baseTexture: "static/imgs/ball/world.topo.bathy.200401.jpg",
                    heightTexture: "static/imgs/ball/world.topo.bathy.200401.jpg",
                    displacementScale: 0.04,
                    shading: 'realistic',
                    environment: 'static/imgs/ball/starfield.jpg',
                    realisticMaterial: {
                        roughness: 0.9
                    },
                    postEffect: {
                        enable: true
                    },
                    light: {
                        main: {
                            intensity: 5,
                            shadow: false
                        },
                        ambientCubemap: {
                            texture: 'static/imgs/ball/pisa.hdr',
                            diffuseIntensity: 0.2
                        },
                        ambient: {
                            intensity:5
                        }
                    },
                    viewControl: {
                        distance:200,
                    }
                }
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
