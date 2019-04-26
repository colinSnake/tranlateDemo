<template>
    <div class="translateResult">
        <h2 :style="{color: fontColor}">{{contentText}}</h2>
    </div>
</template>

<script>
    export default {
        name: 'translateResult',
        props:['contentText'],
        data(){
            return{
                fontColor: ''
            }
        },
        created(){
            this.fontColor = this.randomColor()
            console.log(this.fontColor)
        },
        methods:{
            randomColor(){//十六进制颜色随机
                var r = Math.floor(Math.random()*256);
                var g = Math.floor(Math.random()*256);
                var b = Math.floor(Math.random()*256);
                var color = '#'+r.toString(16)+g.toString(16)+b.toString(16);
                return color;
            }
        }
    }
</script>
<style>
    h2{
        margin-top: 20px; 
        font-size: 28px;
    }
</style>


