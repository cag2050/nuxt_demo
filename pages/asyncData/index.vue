<template>
    <div>
        <div>github 中，js 仓库 stars 数排名：</div>
        total_count：{{ total_count }}
        <el-table :data="items" style="width: 70%">
            <el-table-column
                type="index"
                :index="indexMethod"
            ></el-table-column>
            <el-table-column prop="full_name" label="项目全名" width="300px">
            </el-table-column>
            <el-table-column
                prop="stargazers_count"
                label="stars 数"
                width="100px"
            >
            </el-table-column>
            <el-table-column label="仓库地址">
                <template slot-scope="scope">
                    <a :href="scope.row.html_url" target="_blank">{{
                        scope.row.html_url
                    }}</a>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Index',
    // 异步数据：https://zh.nuxtjs.org/guide/async-data
    // 1. 返回 Promise
    // /*
    asyncData({ params }) {
        return axios
            .get(
                `https://api.github.com/search/repositories?q=+language:js&sort=stars&order=desc`
            )
            .then(res => {
                return {
                    items: res.data.items,
                    total_count: res.data.total_count
                }
            })
    },
    // */
    // 2. 使用 async或await
    /*
    async asyncData({ params }) {
        const { data } = await axios.get(
            `https://api.github.com/search/repositories?q=+language:js&sort=stars&order=desc`
        )
        return { items: data.items, total_count: data.total_count }
    },
    */
    // 3. 使用回调函数
    /*
    asyncData({ params }, callback) {
        axios
            .get(
                `https://api.github.com/search/repositories?q=+language:js&sort=stars&order=desc`
            )
            .then(res => {
                callback(null, {
                    items: res.data.items,
                    total_count: res.data.total_count
                })
            })
    },
    */
    methods: {
        indexMethod(index) {
            return index + 1
        }
    }
}
</script>

<style scoped></style>
