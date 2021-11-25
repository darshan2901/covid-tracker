<template>
    <div class="container">
        <h1>{{ text }}</h1>
        <p>{{ timeStamp }}</p>
    </div>
</template>

<script>
import moment from 'moment'


export default{
    name: 'DataTitle',
    props:['text' , 'dateData'],
    computed:{
        timeStamp: function(){
            return moment(this.dateData).format('DD MMMM YYYY, h:mm:ss')
        }
    }
}
</script>

<style scoped>
.container{
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    transition: 0.3s;
    width: 40%;
    padding: 20px;
    margin-left: 30%;
}
</style>
