<template>
    <div>
        <h3>게시글 목록</h3>
        {{ state.row }}
    </div>
</template>

<script>
import { reactive, onMounted } from "vue";
import axios from "axios";

export default {
    setup () {
        const state = reactive({
            row : [],
        })

        const handleData = async() => {
            const url = `/api/boards`;
            const headers = {"Content-Type":"application/json"};
            const { data } = await axios.get(url, {headers});
            console.log(data);
            
            // if(data.status === 200) {
                state.row = data
            // }
        };

        onMounted(()=>{
            handleData();
        })

        return {
            state
        }
    }
}
</script>

<style lang="css" scoped>

</style>