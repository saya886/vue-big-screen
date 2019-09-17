<template>
<div id="local_div">
    <header id="header">
			<h3 class="header-title">智能物联</h3>
		</header>
		
		<footer id="footer"></footer>
		



    <div id="container">
      <div id="item_container">
        <div class="item item-1">
          <ball2/>
        </div>
         
        <div class="item item-2">
          <map2/>
        </div>
        <div class="item item-3">
          <radar-style-1/>
        </div>
        <div class="item item-4">
          <table-style-1/>
        </div>
        <div class="item item-5">
          <table-style-1/>
        </div>
        <div class="item item-6">
         <table-style-1/>
          </div>
        <div class="item item-7">
          <bar3/>
        </div>
        <div class="item item-8">
          <table-style-1/>
        </div>
      </div>
    </div>

    <div style="z-index:-4" id="bg_container">
      <bg/>
    </div>


</div>
</template>

<script>
import RadarStyle1 from '../../cell/radar/radar-style-1'
import Table1 from '../../cell/table/table-style-1'
import baseBar from '~components/cell/bar/bar-style-1.vue';
import Bar3 from '~components/cell/bar/bar-style-3.vue';

import Box1 from '../../cell/box/box-style-1'
import Box1Small from '../../cell/box/box-style-1-small'
import Box2 from '../../cell/box/box-style-2'
import Box3 from '../../cell/box/box-style-3'
import Box4 from '../../cell/box/box-style-4'
import Box5 from '../../cell/box/box-style-5'

import ball2 from '../../cell/ball/ball-style-2.vue'
import map2 from '../../cell/map/map-style-2.vue' 
import bg from '../../cell/template_bg/bg.vue'



export default {
  components: {
    'radar-style-1': RadarStyle1,
    'base-Bar': baseBar,
    'bar3':Bar3,
    'table-style-1': Table1,
    'box-style-1': Box1,
    'box-style-1-small': Box1Small,
    'box-style-2': Box2,
    'box-style-3': Box3,
    'box-style-4': Box4,
    'box-style-5': Box5,
    'ball2':ball2,
    'map2':map2,
    'bg':bg
  },
  data() {
    return {
      spinShow1: true,
      ageRangeData: [],
      eventListFetchData: [],
      spinShow1: true,
      infoData: [
        { name: '淳11111', value1: 250 },
        { name: '横溪111', value1: 350 },
        { name: '湖熟', value1: 550 },
        { name: '江宁', value1: 450 },
        { name: '东山', value1: 650 },
        { name: '禄口', value1: 350 },
        { name: '汤山', value1: 750 },
        { name: '麒麟', value1: 850 },
        { name: '谷里', value1: 350 },
        { name: '秣陵', value1: 650 },
        { name: '淳11111', value1: 250 },
        { name: '横溪111', value1: 350 },
        { name: '湖熟', value1: 550 },
        { name: '江宁', value1: 450 },
        { name: '东山', value1: 650 },
        { name: '禄口', value1: 350 },
        { name: '汤山', value1: 750 },
        { name: '麒麟', value1: 850 },
        { name: '谷里', value1: 350 },
        { name: '秣陵', value1: 650 },
        { name: '淳11111', value1: 250 },
        { name: '横溪111', value1: 350 },
        { name: '湖熟', value1: 550 },
        { name: '江宁', value1: 450 },
        { name: '东山', value1: 650 },
        { name: '禄口', value1: 350 },
        { name: '汤山', value1: 750 },
        { name: '麒麟', value1: 850 },
        { name: '谷里', value1: 350 },
        { name: '秣陵', value1: 650 },
      ],
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

    this.$http.get('/table/eventListSource')
      .then(res => {
        if (res.state && res.data) {
          this.eventListFetchData = res.data
          this.spinShow1 = false
        }
      })
      .catch(err => {
        console.log(err)
        this.$fetchMock('/static/mock/table/eventListSource.json')
          .then(res => {
            this.eventListFetchData = res
            this.spinShow1 = false
          })
      })

  },
  methods: {
    getChild(type) {
      this.type = type;
      this.getSource(this.type);
    }
  }
}
</script>

<style lang="scss" scoped>
@import './bigscreen.scss';
</style>

