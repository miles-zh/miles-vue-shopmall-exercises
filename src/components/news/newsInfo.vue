<template>
    <div class="newsinfo-container">
        <!-- 大标题 -->
        <h3 class="title">新闻标题</h3>
        <!-- 子标题 -->
        <p class="subtitle">
            <span>发表时间：</span>
            <span>点击次数:0次</span>
        </p>
        <hr>
        <!-- 内容区域    -->
        <div class="container">
            新闻内容
            <br><br><br><br><br><br><br>
        </div>
       



        <!-- 从后台获取数据 -->
        <!-- <h3 class="title"> {{ newsinfo.title }}</h3>
        <p class="subtitle">
            <span>发表时间：{{newsinfo.add_time | dateFormat}}</span>
            <span>点击次数:{{newsinfo.click}}次</span>
        </p>
        <hr>
        
        <div class="container" v-html="newsinfo.content">

        </div> -->

        <!-- 评论区域 -->

        <comment-box :id="this.id"></comment-box>

    </div>
</template>

<script>
    // 1.导入评论子组件
    import comment from '../subcompopents/comment.vue'

    export default {
        data(){
            return {
                id: this.$route.params.id, // 将url传过来的id值传到data上
                newsinfo:{}
            }
        }
        ,created(){
            this.getNewsInfo()
        }
        ,methods:{
            getNewsInfo(){  //  获取新闻呢详情
            // this.$http.get('api/getnew/' + this.id).then(result => {
            //     if(result.status === 0){
            //         this.newsinfo = result.body.message[0]
            //     }else{
            //         Toast('获取新闻详情失败')
            //     }
            // })

            }
        },
        components:{  //  用来注册子组件的节点
            'comment-box':comment
        }
    }
</script>

<style lang="scss" scoped>
    .newsinfo-container{
        padding:0 4px;

        .title{
            font-size:16px;
            text-align: center;
            margin:15px 0;
            color:#f40;
        }
        .subtitle{
            font-size: 13px;
            color:#226aff;
            // 设置里面元素左右对齐
            display: flex;
            justify-content: space-between;
        }
        .container{
            // 取消scoped才能生效
            img{
                width:100%
            }
        }
    }
</style>