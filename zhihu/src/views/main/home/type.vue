<template>
    <div>
        <ul v-for="(item) in list" :key="item.id">
            <p>{{item.title}}</p>
            <p>{{item.description}}</p>
            <img :src="item.banner" alt="">
            <p>{{`${item.favor}赞同，${item.comment}评论`}}</p>
        </ul>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    data(){
        return {
            page: 1,
            pageSize: 10,
            list: []
        }
    },
    async created(){
        let data = await axios.get(`/api/list?type=${this.$route.params['type']}&page=${this.page}&pageSize=10`)
        console.log('router...', data);
        this.list = data.data;
    }
}
</script>