<template>
    <div>
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
        {{msg}}
    </div>
</template>

<script>
    export default {
        name: "Book",
        data(){
            return {
                msg:'Hello vue',
                books:[
                    {
                        id:1,
                        name:'西游记',
                        author:'吴承恩'
                    },
                    {
                        id:2,
                        name:'红楼梦',
                        author:'曹雪芹'
                    },
                    {
                        id:3,
                        name:'三国演义',
                        author:'罗贯中'
                    },
                    {
                        id:4,
                        name:'水浒传',
                        author:'斯耐庵'
                    }
                ]
            }
        },
        created() {
            const _this=this;
            axios.get('http://localhost:8181/book/findAll').then(function (resp) {
                _this.books = resp.data;
            })
        }
    }
</script>

<style scoped>

</style>
