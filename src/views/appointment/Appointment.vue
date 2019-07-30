<template>
  <div class="appointment">
    <header>门诊预约</header>
    <div class="container">
      <div class="aside">
        <h3>操作流程</h3>
        <ul>
          <li :class="{active: index===0}" @click="handleTab(0)">
            <span class="red" v-if="boo.depatment">更新</span>
            <span v-else>选择</span>预约科室
          </li>
          <li :class="{active: index===1}" @click="handleTab(1)">
            <span class="red" v-if="boo.date">更新</span>
            <span v-else>选择</span>预约日期
          </li>
          <li :class="{active: index===2}" @click="handleTab(2)">
            <span class="red" v-if="boo.doctor">更新</span>
            <span v-else>选择</span>预约医生
          </li>
          <li :class="{active: index===3}" @click="handleTab(3)">
            <span class="red" v-if="boo.times">更新</span>
            <span v-else>选择</span>预约时间
          </li>
          <li :class="{active: index===4}" @click="handleTab(4)">确认并完成</li>
        </ul>
        <div class="btns">
          <!-- <button @click="$router.go(-1);">22</button> -->
          <a href="javascript:;" @click="$router.push('/');">
            <img src="../../assets/zhuye.png" alt />
          </a>
          <a href="javascript:;" @click="$router.go(-1);">
            <img src="../../assets/fanhui.png" alt />
          </a>
        </div>
      </div>
      <div class="main">
        <div class="head">
          <!-- <h3 v-show="initial===0">请选择要预约的科室！</h3>
          <h3 v-show="initial===2">请确认预约信息</h3>-->
          <div class="head-list" v-show="headSwitch">
            已选择:
            <span>{{headList.depatment}}</span>
            <span>{{headList.date}}</span>
            <span>{{headList.doctor}}</span>
            <span>{{headList.times}}</span>
          </div>
        </div>
        <Depatment :list="allData.depatment" v-show="index===0" @click="getItem($event,index)" />
        <Date :list="allData.date" v-show="index===1" @click="getItem($event,index)" />
        <Doctor :list="allData.doctor" v-show="index===2" @click="getItem($event,index)" />
        <Times :list="allData.times" v-show="index===3" @click="getItem($event,index)" />
        <End v-show="index===4" :headList="headList" />
        <el-pagination
          class="pagination"
          layout="prev, pager, next"
          :total="totalLength"
          :page-size="9"
          v-show="paginationSwitch"
        ></el-pagination>
      </div>
    </div>
  </div>
</template>

<script>
import Depatment from "@/views/appointment/Depatment";
import Date from "@/views/appointment/Date";
import Doctor from "@/views/appointment/Doctor";
import Times from "@/views/appointment/Times";
import End from "@/views/appointment/End";
export default {
  name: "appointment",
  data() {
    return {
      index: 0,
      headList: {
        depatment: "",
        date: "",
        doctor: "",
        times: ""
      },
      boo: {
        depatment: false,
        date: false,
        doctor: false,
        times: false
      },
      headSwitch: false,
      paginationSwitch: true,
      allData: {
        depatment: [
          "妇产科",
          "儿科",
          "内科",
          "妇产科",
          "儿科",
          "内科",
          "儿科",
          "内科",
          "妇产科",
          "儿科",
          "内科"
        ],
        date: ["2018-01-09 星期一", "2018-01-11 星期二", "2018-01-11 星期三"],
        doctor: ["朱静", "郑彩霞", "周迅"],
        times: [
          "08:00:00",
          "08:15:00",
          "08:30:00",
          "08:00:00",
          "08:15:00",
          "08:30:00",
          "08:00:00",
          "08:15:00",
          "08:30:00",
          "08:00:00",
          "08:15:00",
          "08:30:00"
        ]
      },
      totalLength: 0
    };
  },
  created() {
    this.totalLength = this.allData.depatment.length;
    // console.log(this.headList);
    // console.log(typeof this.headList.depatment);
  },
  components: {
    Depatment,
    Date,
    Doctor,
    Times,
    End
  },
  watch: {},
  computed: {
    // traversing() {
    //   Object.keys(this.headList).forEach(item => {
    //     if (this.headList[item] !== "") {
    //       return false;
    //     }
    //   });
    // }
  },
  methods: {
    handleTab(i) {
      // if (this.headList.depatment === "") {
      //   alert("请选择预约科室");
      //   return;
      // }
      this.headSwitch = true;
      this.paginationSwitch = true;
      if (i === 4) {
        this.headSwitch = false;
        // if (this.headList.date === "") {
        //   alert("请选择预约日期");
        //   return;
        // }
        // if (this.headList.doctor === "") {
        //   alert("请选择预约医生");
        //   return;
        // }
        // if (this.headList.times === "") {
        //   alert("请选择预约时间");
        //   return;
        // }

        this.paginationSwitch = false;
      }
      if (i === 0) {
        this.totalLength = this.allData.depatment.length;
        this.headSwitch = false;
      } else if (i === 1) {
        this.totalLength = this.allData.date.length;
      } else if (i === 2) {
        this.totalLength = this.allData.doctor.length;
      } else if (i === 3) {
        this.totalLength = this.allData.times.length;
      }
      this.index = i;

      Object.keys(this.headList).forEach((item, index) => {
        if (this.headList[item] !== "") {
          if (item === "depatment") {
            this.boo.depatment = true;
            this.headSwitch = true;
          } else if (item === "date") {
            this.boo.date = true;
          } else if (item === "doctor") {
            this.boo.doctor = true;
          } else {
            this.boo.times = true;
          }
        }
      });
    },
    getItem(e, index) {
      this.headSwitch = true;

      switch (index) {
        case 0:
          this.headList.depatment = e.value;
          break;
        case 1:
          this.headList.date = e.value;
          break;
        case 2:
          this.headList.doctor = e.value;
          break;
        case 3:
          this.headList.times = e.value;
          break;
        default:
          break;
      }
    }
  }
};
</script>

<style scoped lang="less">
header {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 150px;
  font-size: 40px;
  color: #fff;
}
.appointment {
  width: 1280px;
  height: 1024px;
  margin: 0 auto;
  background: url(../../assets/bg-second.jpg) no-repeat center 0;
  .container {
    overflow: hidden;
    margin-top: 20px;
    .aside {
      float: left;
      width: 200px;

      h3 {
        height: 40px;
        line-height: 40px;
        text-align: center;
      }
      ul {
        padding: 20px 0 50px;
        li {
          padding-left: 20px;
          margin-top: 10px;
          line-height: 40px;
          &.active {
            color: #fff;
            background: #18abef;
          }
        }
      }
    }
    .main {
      float: right;
      width: 1000px;
    }
  }
}
.btns {
  a {
    display: block;
    width: 100px;
    img {
      width: 100%;
    }
  }
}
.head {
  .head-list {
    height: 60px;
    line-height: 60px;
    span {
      padding-right: 20px;
    }
  }
}
.pagination {
  text-align: center;
}
</style>
