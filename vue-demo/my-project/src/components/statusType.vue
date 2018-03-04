<template>
  <div>
    <div class="choose clearfix">
      <span @click="toggleShow" class="add">+</span>
      <div v-for="(item, index) in set" class="name">
        <span >{{item}}</span>
        <i class="tagClose"></i>
      </div>
    </div>
    <div ref="status" class="statusList">
      <div class="search">
        <input type="text" placeholder="搜索">
      </div>
      <div v-for="item in statusList" class="clearfix tag">
        <label @click="check($event)"><input type="checkbox" class="sure" ref="check">{{item.status_name}}</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
        return {
          showAdd: false,
          tag: [],
          set: [],
          statusList: [
            {
              'status_name': '变更中'
            },
            {
              'status_name': '未生效'
            },
            {
              'status_name': '作废'
            },
            {
              'status_name': '正常'
            },
            {
              'status_name': '审核中'
            }
          ]
        }
  },
  methods: {
    toggleShow () {
      if (this.showAdd == false) {
        this.$refs.status.style.display = 'block';
        this.showAdd = true;
      }else {
        this.$refs.status.style.display = 'none';
        this.showAdd = false;
      }
    },
    check (event) {
      var el = event.currentTarget;
      this.tag.push(el.innerText);
      this.set = Array.from(new Set(this.tag));
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.clearfix:after,.clearfix:before{
  content: '';
  display: block;
  clear: both;
}
.clearfix{
  zoom: 1;
}
.choose{
  width: 400px;
  height: 30px;
  border: 1px solid #000;
  padding-top: 5px;
}
.search{
  width: 400px;
  background: #f9fbfc;
  padding: 5px 0 5px 0;
}
.tag{
  padding: 10px 0 0 30px;
}

.search input {
  padding-left: 50px;
  margin-left: 25px;
  width: 300px;
  height: 30px;
  border-radius: 15px;
  background:#fff url('../assets/search.png') no-repeat 3%;
  border: 1px solid #e0e5e9;
}
.choose .add{
  float: right;
  cursor: pointer;
}
.name{
  display: block;
  float: left;
  width: 70px;
  height: 25px;
  line-height: 25px;
  background: dodgerblue;
  border-radius: 15px;
  padding-right: 5px;
  text-align: center;
}
.tagClose:before{
  content: "\2716";
}
.tagClose{
  border-radius: 50%;
  text-align: center;
  position: relative;
  cursor: pointer;
  font-size: 12px;
  height: 16px;
  width: 16px;
  line-height: 16px;
  vertical-align: middle;
  top: -1px;
  right: -5px;
  color: #fff;
}
  .sure{
    float: left;
  }
  .statusList {
    border-radius: 5px;
    display: none;
  }
input[type=checkbox] {
  position: relative;
  width: 30px;
}
input[type=checkout]::before{
  content:'';
  position: absolute;
  top: 0;
  left: 0;
  width: 14px;
  height: 14px;
  line-height: 14px;
  text-align: center;
  color: #fff;
  font-size: 16px;
  background-color: #fbfdff;
  border-radius: 4px;
  border: 1px solid #cad5dc;
}
input[type=checkout]:checked::before {
  color: #fff;
  background-color: #32bdff;
  content: '\2713';
}
</style>
