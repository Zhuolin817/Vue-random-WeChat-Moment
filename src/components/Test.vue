<template>
    <div class="pyqbox">
        <div class="innerbox">
            <h1 class="el-icon-share">
                在线pyq文案
            </h1>
            <div class="hbox">
                <h2>{{ pyq }}</h2>
            </div>
        
            <div class="buttonbox">
                <el-button @click="changepyq()">更换语句</el-button>
            </div>
            
        </div>
        
    </div>
  
  
</template>

<script>

import axios from 'axios';
export default {
    data () {
        return {
            pyq:''
        }
    },
    created(){
        axios.get("https://v.api.aa1.cn/api/pyq/index.php?aa1=json").then((res)=>{
            console.log(res.data.pyq)
            this.pyq = res.data.pyq
        })
    },
    methods:{
        changepyq(){
            axios.get("https://v.api.aa1.cn/api/pyq/index.php?aa1=json").then((res)=>{
            console.log(res.data.pyq)
            this.pyq = res.data.pyq
            const h = this.$createElement;

            this.$notify({
            title: '成功',
            message: h('i', { style: 'color: teal'}, '恭喜你刷新成功')
            });
        })
        
        }
    }
}
</script>

<style scoped>
    .pyqbox{
        display: flex;
        height: 100vh;
        
        justify-content: center;
        align-items: center;
        
    }

    .buttonbox{
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .innerbox{
        width: 60vw;
        height: 40vh;
        background-color: white;
        border-radius: 40px;

    }

    .hbox{
        display: flex;
        justify-content: center;
        align-items: center; 
    }

    .innerbox h1{
        padding-left: 3vw;
        color: #409EFF;
    }

    .innerbox h2{
        padding-left: 3vw;
        padding-right: 3vw;
    }

</style>