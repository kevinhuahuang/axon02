<template>
  <div class="container">
    <div class="content">
      <div class="left_part">
        <a v-for="(item, index) in mainLinkArray" :key="index" :href="item[1]">{{item[0]}}</a>
      </div>
      <div class="right_part">
        <a v-for="(item, index) in linkArray" :key="index" :href="item[1]">{{item[0]}}</a>
      </div>
    </div>
    <div class="sep_line"></div>
  </div>
</template>

<script>
export default {
  name: 'NavigatorHeader',
  data: function () {
    return {
    }
  },
  props: {
    mainLinkArray: {
      type: Array,
      default () {
        return [['主页', '../guide'], ['简历', '../resume']]
      }
    },
    linkArray: {
      type: Array,
      default () {
        return [['网页应用', '../dp7'], ['商城', '../millet'], ['股票', '../start_page'], ['其它', '../others']]
      }
    }
  }
}
</script>

<style scoped>
  .container {
    position:fixed;
    top: 0;
    width:100%;
    z-index:2;
    background: white;
  }
  .content {
    position: relative;
    display: flex;
    text-align: left;
    justify-content: space-between;
    width: inherit;
    height: 50px;
  }

  .left_part {
    margin-left: 30px;
    display: flex;
    justify-content: flex-start;
    font-size: 1.2em;
    font-weight: bold;
  }
  .left_part  a {
    cursor: pointer;
    margin-top: 12px;
    margin-left: 30px;
  }
  a {
    color: black;
    text-decoration: none;
  }
  a:hover {
    color: orangered;
  }
  .right_part {
    margin-right: 30px;
    display: flex;
    justify-content: flex-end;
  }
  .right_part a {
    cursor: pointer;
    margin-top: 25px;
    margin-right: 15px;
  }

  .sep_line {
    width: inherit;
    height: 20px;
    border-top: 2px solid grey;
  }
</style>
