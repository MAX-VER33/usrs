<template>
    <el-container>
        <Navigate/>
        <el-header style="font-size: 32px;height: 50px;">院校对比</el-header>
        <el-main style="padding-top: 0;">
           <el-row>
                <el-col :span="4">
                    <div style="border: 1px solid var(--el-border-color);display: flex;justify-content: center;align-items: center;height: 100px;">
                        <span style="font-size: 30px;font-weight: bold;">院校信息</span>
                    </div>
                </el-col>
                <el-col :span="5">
                    <div class="div1">
                        <el-input v-model="input1" placeholder="请输入院校名称" clearable />
                        <el-input type="button" value="提交" @click="handle1()" style="width: 30px;margin-left: 5px;"/>
                    </div>
                </el-col>
                <el-col :span="5">
                    <div class="div1">
                        <el-input v-model="input2" placeholder="请输入院校名称" clearable />
                        <el-input type="button" value="提交" @click="handle2()" style="width: 30px;margin-left: 5px;"/>
                    </div>
                </el-col>
                <el-col :span="5">
                    <div class="div1">
                        <el-input v-model="input3" placeholder="请输入院校名称" clearable />
                        <el-input type="button" value="提交" @click="handle3()" style="width: 30px;margin-left: 5px;"/>
                    </div>
                </el-col>
                <el-col :span="5">
                    <div class="div1">
                        <el-input v-model="input4" placeholder="请输入院校名称" clearable />
                        <el-input type="button" value="提交" @click="handle4()" style="width: 30px;margin-left: 5px;"/>
                    </div>
                </el-col>
           </el-row>
            <div>
                <el-select v-model="value1" class="m-2" placeholder="学位" size="large">
                <el-option
                    v-for="item in options1"
                    :key="item.value1"
                    :label="item.label1"
                    :value="item.value1"
                    />
                </el-select>
                <el-select v-model="value2" class="m-2" placeholder="专业" size="large">
                    <el-option
                    v-for="item in options2"
                    :key="item.value2"
                    :label="item.label2"
                    :value="item.value2"
                    />
                </el-select>
                <el-select v-model="value3" class="m-2" placeholder="学级" size="large">
                    <el-option
                    v-for="item in options3"
                    :key="item.value3"
                    :label="item.label3"
                    :value="item.value3"
                    />
                </el-select>
            </div>
            <div style="border: 1px solid var(--el-border-color);height: 50px;display: flex;align-items: center;background-color: #F5DEB3;">
                <div style="border-left: 5px solid red;height: 30px;display:flex;align-items: center;margin-left: 20px;"><span style="margin-left: 15px;font-size: 24px;font-weight: bold;">招录信息</span></div>
            </div>
            <div style="border: 1px solid var(--el-border-color);margin-top: 20px;margin-bottom: 20px;">
                <el-table :data="tableData" border style="width: 100%">
                    <el-table-column prop="baolubi" label="报录比" width="180" />
                    <el-table-column prop="highest" label="最高分" width="180" />
                    <el-table-column prop="lowest" label="最低分" width="180" />
                    <el-table-column prop="average" label="平均分" width="180" />
                    <el-table-column prop="stu_number" label="招生人数" width="180" />
                </el-table>
            </div>
            <div style="border: 1px solid var(--el-border-color);height: 50px;display: flex;align-items: center;background-color: #F5DEB3;">
                <div style="border-left: 5px solid red;height: 30px;display:flex;align-items: center;margin-left: 20px;"><span style="margin-left: 15px;font-size: 24px;font-weight: bold;">院校实力</span></div>
            </div>
            <div style="border: 1px solid var(--el-border-color);margin-top: 20px;">
                <el-table :data="tableData" border style="width: 100%">
                    <el-table-column prop="area" label="院校地区" width="180" />
                    <el-table-column prop="layer" label="院校层次" width="180" />
                    <el-table-column prop="speciality_rank" label="专业排名" width="180" />
                    <el-table-column prop="subject_estimate" label="学科评估" width="180" />
                </el-table>
            </div>
        </el-main>
    </el-container>
</template>

<script setup>
import Navigate from "@/components/Navigate";
import axios from "axios";
import { reactive, ref } from 'vue'
const input1 = ref('')
const input2 = ref('')
const input3 = ref('')
const input4 = ref('')

let tableData = reactive([])

function handle1(){
  axios.post(
    "http://localhost:9001/kaoyancollage/compare1",
    {
      name: input1.value,
      tpye: value1.value,
      speciality: value2.value,
      year: value3.value,
    }
  ).then(result=>{
    this.tableData = result.data.data;
  })
}
function handle2(){
  axios.post(
    "",
    {
      input2,
      value1,
      value2,
      value3,
    }
  ).then(result=>{
    form2 = result.data.data;
  })
}
function handle3(){
  axios.post(
    "",
    {
      input3,
      value1,
      value2,
      value3,
    }
  ).then(result=>{
    form3 = result.data.data;
  })
}
function handle4(){
  axios.post(
    "",
    {
      input4,
      value1,
      value2,
      value3,
    }
  ).then(result=>{
    form4 = result.data.data;
  })
}
const value1 = ref('')

const options1 = [
  {
    value1: '学硕',
    label1: '学硕',
  },
  {
    value1: '专硕',
    label1: '专硕',
  },
]
const value2 = ref('')

const options2 = [
  {
    value2: '软件工程',
    label2: '软件工程',
  },
  {
    value2: '计算机科学与技术',
    label2: '计算机科学与技术',
  },
]
const value3 = ref('')

const options3 = [
  {
    value3: '2021',
    label3: '2021',
  },
  {
    value3: '2022',
    label3: '2022',
  },
  {
    value3: '2023',
    label3: '2023',
  },
]


</script>

<style scoped>
.div1{
    border: 1px solid var(--el-border-color);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100px;
    padding-left: 100px;
    padding-right: 100px;
}
.m-2{
    margin-top: 20px;
    margin-bottom: 20px;
    margin-right: 20px;
}
</style>