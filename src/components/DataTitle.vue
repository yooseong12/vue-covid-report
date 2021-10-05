<template>
    <div class="text-center">
        <!-- {{}} <- 이 코드를 사용하면 밑에 .text로 시작하면서 class뒤에 css태그를 넣으면
        적용됨(팁) -->
        <h2 class="text-3xl font-bold">{{text}}</h2>
        <div class="text-2xl mt-4 mb-10">
            {{timestamp}}
        </div>
    </div>
</template>
<script>
import moment from 'moment'

export default {
    name : 'DataTitle',
    // props = 변하지 않는 데이터
    props:['text','dataDate'],
    computed:{
        timestamp: function(){
            return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
        }
    }
}
</script>
