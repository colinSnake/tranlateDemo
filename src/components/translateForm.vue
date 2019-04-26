<template>
    <div class="translateForm row">
        <div class="col-md-6 offset-md-3">
            <form class="active form-inline" @submit.prevent="formSubmit">
                <input type="text" placeholder="请输入想要翻译的内容" v-model="translateText" class="form-control">
                <select class="form-control inputSelect" v-model="language">
                    <option value="en">English</option>
                    <option value="ru">Russian</option>
                    <option value="ko">Korean</option>
                    <option value="ja">Japanese</option>
                    <option value="zh">Chinese</option>
                </select>
                <input type="submit" class="btn btn-success" value="翻译">
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: 'translateForm',
    data(){
        return{
            translateText: '',
            language: '',
        }
    },
    created(){
        this.language = 'en'
    },
    methods:{
        formSubmit(){
            // 子->父
            this.$emit('formSubmit',this.translateText,this.language)
        }
    }
}
</script>
<style>
    .active{
        height: 80px;
        display: flex;
        justify-content: center;
        background-color: #ecf0f1; 
        border-radius: 10px; 
    }
    .inputSelect{
        margin: 0 10px; 
    }
</style>


