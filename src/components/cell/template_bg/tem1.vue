<template>
<div id="local_div">
    <header id="header">
			<h3 class="header-title">大屏数据可视化模板</h3>
			<!--<div class="header-info header-info-l">数据来源：大数据研究院</div>
			<div class="header-info header-info-r">更新日期：2019-04-30</div>-->
		</header>
		
		<footer id="footer"></footer>
		
		<div id="container">
			<div id="flexCon">
				<div class="flex-row">
					<div class="flex-cell flex-cell-l">
						<div class="chart-wrapper">
							<h3 class="chart-title">图表</h3>
							<div class="chart-div">
								<div class="chart-loader"><div class="loader"></div></div>
							</div>
						</div>
					</div>
					<div class="flex-cell flex-cell-c">
						<div class="chart-wrapper">
							<h3 class="chart-title"></h3>
							<div class="chart-div"></div>
						</div>
					</div>
					<div class="flex-cell flex-cell-r">
						<div class="chart-wrapper">
							<h3 class="chart-title"></h3>
							<div class="chart-div chart-done">
								<div class="chart-loader"><div class="loader"></div></div>
							</div>
						</div>
					</div>
				</div>
				<div class="flex-row">
					<div class="flex-cell flex-cell-lc">
						<div class="chart-wrapper">
							<h3 class="chart-title"></h3>
							<div class="chart-div">
								<div class="chart-loader"><div class="loader"></div></div>
							</div>
						</div>
					</div>
					<div class="flex-cell flex-cell-r">
						<div class="chart-wrapper">
							<h3 class="chart-title"></h3>
							<div class="chart-div chart-done">
								

                                <div class="content">
                                <box-style-1 class='box-style-1'>
                                    
                                    <radar-style-1 chartId='radar1' :source='ageRangeData' />
                                </box-style-1>
                                </div>

							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
</div>
</template>
<script>
import RadarStyle1 from '../../cell/radar/radar-style-1'
import Box1 from '../../cell/box/box-style-1'


export default {
  components: {
    'radar-style-1': RadarStyle1,
    'box-style-1': Box1,
  },
  data() {
    return {
      spinShow1: true,
      ageRangeData: [],
    }
  },
  created() {
    this.$http.get('/radar/ageRangeSource')
      .then(res => {
        if (res.state && res.data) {
          this.ageRangeData = res.data
          this.spinShow1 = false
        }
      })
      .catch(err => {
        console.log(err)
        this.$fetchMock('/static/mock/radar/ageRangeSource.json')
          .then(res => {
            this.ageRangeData = res
            this.spinShow1 = false
          })
      })
  },
}
</script>
<style scoped>

.content{
  width: 100%;
  height: 100%;
  display: flex;
  flex-wrap: wrap;
}

/* global */
* {margin:0;padding:0;box-sizing:border-box;}
#local_div {
	width:100%;
	height:100%;
	min-width:1200px;
	min-height:600px;
	overflow:hidden;
}
#local_div {
	position:relative;
	font-family:"Microsoft Yahei", Arial, sans-serif;
	background:#0a1631 url("../../../../static/imgs/template_bg/tem1/bg.png") 0 0 / 100% 100% no-repeat;
}

/* layout */
#header {
	position:relative;
	height:72px;
	background:url("../../../../static/imgs/template_bg/tem1/header.png") 0 0 / 100% 100% no-repeat;
	overflow:hidden;
}
.header-title {line-height:64px;text-align:center;font-size:32px;font-weight:400;color:#fff;}
.header-info {position:absolute;top:36px;font-size:18px;color:#73aae5;}
.header-info-l {left:20px;}
.header-info-r {right:20px;}
#footer {
	position:absolute;
	bottom:0;
	left:0;
	right:0;
	height:24px;
	background:url("../../../../static/imgs/template_bg/tem1/footer.png") 0 0 / 100% 100% no-repeat;
}
#container {position:absolute;top:72px;bottom:24px;left:0;right:0;}

#flexCon {
	height:100%;
	display:-webkit-flex;
	display:-ms-flexbox;
	display:flex;
	-webkit-flex-direction:column;
	-ms-flex-direction:column;
	flex-direction:column;
}
.flex-row {
	-webkit-flex:1;
	-ms-flex:1;
	flex:1;
	display:-webkit-flex;
	display:-ms-flexbox;
	display:flex;
}
.flex-cell {-webkit-flex:1;-ms-flex:1;flex:1;padding:15px;margin: 5px;}
.flex-cell-l,
.flex-cell-r {-webkit-flex:2;-ms-flex:2;flex:2;}
.flex-cell-c {-webkit-flex:3;-ms-flex:3;flex:3;}
.flex-cell-lc {-webkit-flex:4;-ms-flex:4;flex:4;}

.chart-wrapper {position:relative;height:100%;}
.chart-title {height:32px;font-size:22px;font-weight:normal;color:#9aa8d4;}
.chart-div {position:absolute;top:32px;bottom:0;left:0;right:0;}


/* media query */
@media (max-width:1900px) {
	#header {height:48px;}
	#footer {height:16px;}
	#container {top:48px;bottom:16px;}
	.header-title {line-height:42px;font-size:22px;}
	.header-info {top:22px;font-size:16px;}
	.header-info-l {left:14px;}
	.header-info-r {right:14px;}
	.flex-cell {padding:10px;}
	.chart-title {height:24px;font-size:18px;}
	.chart-div {top:24px;}
	.data-t p span {font-size:24px;}
	
}

/* chart-loader */
.chart-loader {
	position:absolute;
	top:0;
	left:0;
	z-index:99;
	width:100%;
	height:100%;
	background:rgba(255, 255, 255, 0);
	transition:all .8s;
}
.chart-loader .loader {
	position:absolute;
	left:50%;
	top:50%;
	width:60px;
	height:60px;
	margin:-30px 0 0 -30px;
	border:3px solid transparent;
	border-top-color:#3498db;
	border-radius:50% !important;
	-webkit-animation:spin 2s linear infinite;
	animation:spin 2s linear infinite;
}
.chart-loader .loader:before {
	content:"";
	position:absolute;
	top:3px;
	left:5px;
	right:5px;
	bottom:5px;
	border:3px solid transparent;
	border-top-color:#e74c3c;
	border-radius:50% !important;
	-webkit-animation:spin 3s linear infinite;
	animation:spin 3s linear infinite;
}
.chart-loader .loader:after {
	content:"";
	position:absolute;
	top:9px;
	left:10px;
	right:10px;
	bottom:10px;
	border:3px solid transparent;
	border-top-color:#f9c922;
	border-radius:50% !important;
	-webkit-animation:spin 1.5s linear infinite;
	animation:spin 1.5s linear infinite;
}
.chart-done .chart-loader {display:none;}
@-webkit-keyframes spin {
	0% {
		-webkit-transform: rotate(0deg);
		-ms-transform: rotate(0deg);
		transform: rotate(0deg)
	}
	100% {
		-webkit-transform: rotate(360deg);
		-ms-transform: rotate(360deg);
		transform: rotate(360deg)
	}
}
@keyframes spin {
	0% {
		-webkit-transform: rotate(0deg);
		-ms-transform: rotate(0deg);
		transform: rotate(0deg)
	}
	100% {
		-webkit-transform: rotate(360deg);
		-ms-transform: rotate(360deg);
		transform: rotate(360deg)
	}
}
</style>


