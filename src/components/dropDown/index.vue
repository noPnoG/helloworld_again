<style lang="scss" scoped>
    .container{
        border: 1px solid #eee;
        float: left;
        overflow: hidden;
        .item{
            width: 180px;
            height: 50px;
            line-height: 50px;
            border-bottom:1px solid #eee ;
            white-space: nowrap;
            box-sizing: border-box;
            .headicon{
                display: inline-block;
                text-align: center;
                width: 40px;
            }
            cursor: pointer;
            &:hover{
                background: #999;
                .num{
                    display: none;
                }
            }
            .title{
                display: inline-block;
                width: 100px;
                margin-left: 10px;
            }
            .num{
                width: 30px;
                text-align:center;
                display: inline-block;
            }
            .dropdown{
                width: 30px;
                text-align:center;
                display: inline-block;
                height: 50px;
                position: relative;
                .icon{
                    vertical-align: middle;
                }
                .dropdownItems{
                    position: absolute;
                    display: none;
                    top: 50px;
                    left: -73px;
                    background: #fff;
                    margin: 0;
                    padding: 0;
                    border: 1px solid #eee;
                    li{
                        padding:0 30px;
                        border-bottom: 1px solid #eee;
                        list-style: none;
                        &:hover{
                            background: #999;
                        }
                    }
                }
                &:hover{
                    .dropdownItems{
                        display: block;
                    }
                }
            }
        }
    }
    .right{
        float: left;
        width: 100px;
        height: 500px;
        background: red;
        overflow: hidden;
    }
</style>
<template>
  <div>

    <div class="container">
      <div v-for="(item,index) in list" :key="index" class="item">
        <i class="el-icon-eleme headicon" />
        <span class="title">{{ item.name }}</span>
        <span class="num">{{ item.val }}</span>
        <div class="dropdown">
          <i class="el-icon-more icon" />
          <ul class="dropdownItems">
            <li>编辑</li>
            <li>删除</li>
          </ul>
        </div>
      </div>
    </div>
    <div class="right" />
  </div>

</template>
<script>
export default {
  data() {
    return {
      list: [
        {
          name: '普通仓库',
          val: 2
        }, {
          name: '一般仓库',
          val: 2
        }, {
          name: '为的仓库',
          val: 2
        }, {
          name: '而定仓库',
          val: 2
        }
      ]
    }
  }
}
</script>

