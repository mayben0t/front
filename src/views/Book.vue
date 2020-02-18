<template>
    <div>
<!--        <h1>{{tip}}</h1>-->
        <table>
            <tr>
                <td>编号</td>
                <td>图书名称</td>
                <td>作者</td>
            </tr>
            <tr v-for="item in books">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.author}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name: "Book",
        data(){
            return{
                // tip: "你好 前端世界"
                books:[
                    {
                        id:1,
                        name:'thinking in java',
                        author:'Bruce Eckel'
                    },
                    {
                        id:2,
                        name: '深入理解虚拟机',
                        author: '周志明'
                    }
                ]
            }
        },
        created() {
            axios.get("http://localhost:8081/book/getAll").then(function (resp) {
                console.log(resp);
                if(resp.data!=null&&resp.data.code ===0 ){
                    books = resp.data.body;
                }
            })
        }
    }

</script>

<style scoped>

</style>