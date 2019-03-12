<template>
  <div>
    <x-header :right-options="{showMore: true}" :left-options="{showBack: false}">你装饰了别人的梦</x-header>
    <swiper loop auto :list="demo06_list" :index="demo06_index"></swiper>
    <grid>
      <grid-item :cols="2" :label="('movie')">
        <img slot="icon" src="../assets/movie.png">
      </grid-item>
      <grid-item :label="('ball')">
        <img slot="icon" src="../assets/fire.png">
      </grid-item>
      <grid-item :label="('music')">
        <img slot="icon" src="../assets/music.png">
      </grid-item>
      <grid-item :label="('flower')">
        <img slot="icon" src="../assets/flower.png">
      </grid-item>
    </grid>
    <div>
    <group :title="('Switch the type')">
      <radio title="type" v-model="type" :options="['1', '2', '3', '4', '5']"></radio>
    </group>
    <panel :header="('List of content with image')" :footer="footer" :list="list" :type="type" @on-img-error="onImgError"></panel>
    </div>
    <tabbar>
      <tabbar-item>
        <img slot="icon" src="../assets/home.png">
        <span slot="label">首页</span>
      </tabbar-item>
      <tabbar-item show-dot>
        <img slot="icon" src="../assets/book.png">
        <span slot="label">阅读</span>
      </tabbar-item>
      <tabbar-item selected>
        <img slot="icon" src="../assets/map.png">
        <span slot="label">附近</span>
      </tabbar-item>
      <tabbar-item badge="2">
        <img slot="icon" src="../assets/mine.png">
        <span slot="label">我的</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>
<script>
import { Panel, Group, Radio, Grid, GridItem, Tabbar, TabbarItem, Cell, XHeader, Swiper } from 'vux'
const baseList = [{
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vvsr72j20p00gogo2.jpg',
  title: '送你一朵fua'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
  title: '送你一辆车'
}, {
  url: 'javascript:',
  img: 'https://static.vux.li/demo/5.jpg', // 404
  title: '送你一次旅行',
  fallbackImg: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw50iwj20ff0aaaci.jpg'
}]

const urlList = baseList.map((item, index) => ({
  url: 'http://m.baidu.com',
  img: item.img,
  fallbackImg: item.fallbackImg,
  title: `(可点击)${item.title}`
}))

export default {
  components: {
    Panel,
    Group,
    Radio,
    Grid,
    GridItem,
    Swiper,
    XHeader,
    Tabbar,
    TabbarItem,
    Cell
  },
  data () {
    return {
      demo06_list: urlList,
      demo06_index: 0
    }
  }
}
</script>