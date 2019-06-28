<template>
    <div>
        {{ total_count }}
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Index',
    asyncData() {
        return axios
            .get(
                `https://api.github.com/search/repositories?q=+language:js&sort=stars&order=desc`
            )
            .then(res => {
                return {
                    total_count: res.data.total_count
                }
            })
    }
}
</script>

<style scoped></style>
