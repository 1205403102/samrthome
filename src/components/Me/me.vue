<template>
  <div>
    <!--header导航条-->
    <x-header :left-options="{showBack: false}"
              :title="'个人中心'">
    </x-header>
    <div style="position: relative;margin-top: 0px;overflow: hidden;">
      <group label-align="left">
        <cell :title="nickname" link="/me/info" is-link>
          <img slot="icon" width="60" height="60" style="display:block;margin-right:5px;border-radius: 50%"
               :src="myImage">
          <p>点此绑定手机</p>
        </cell>
      </group>
      <group label-width="4.5em" label-margin-right="2em" label-align="left" style="font-size: 12px;">
        <cell :title="'我的家庭'" link="/my_family" is-link>
          <img slot="icon" width="20" style="display:block;margin-right:10px;" src="../../assets/img/scene2.png">
        </cell>
      </group>
    </div>
    <!--导航栏-->
    <div>
      <tabbar style="position: fixed;">
        <tabbar-item link="/Home">
          <img slot="icon" src="../../assets/img/scene.png">
          <span slot="label">我的设备</span>
        </tabbar-item>
        <tabbar-item link="/scene">
          <img slot="icon" src="../../assets/img/home.png">
          <span slot="label">智能场景</span>
        </tabbar-item>
        <tabbar-item selected link="/me">
          <img slot="icon" src="../../assets/img/me1.png">
          <span slot="label">个人中心</span>
        </tabbar-item>
      </tabbar>
    </div>

  </div>

</template>

<script>
  import {XButton, XHeader, Tabbar, TabbarItem, Group, Cell} from 'vux'
  export default {
    data() {
      return {
        nickname: '',
        myImage: ''
      }
    },
    created() {
      var mydata = JSON.parse(localStorage.mydata).user
      mydata.nickname = '' ? this.nickname = mydata.phone : this.nickname = mydata.nickname;
      this.myImage = 'http://120.79.21.193/SmartHome' + mydata.photo
    },
    methods: {
    },
    components: {
      XButton,
      XHeader,
      Tabbar,
      TabbarItem,
      Group,
      Cell
    }
  }
</script>

<style lang="less" scoped>

</style>
