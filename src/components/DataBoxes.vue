<template>
    <div>
        <div class=container>
            <h3>Cases</h3>
            <h6>{{ numberWithCommas(stats.NewConfirmed) }}</h6>
            <h6>{{ numberWithCommas(stats.TotalConfirmed) }}</h6>
        </div>
        <div class=container>
            <h3>Deaths</h3>
            <h6>{{ numberWithCommas(stats.NewDeaths) }}</h6>
            <h6>{{ numberWithCommas(stats.TotalDeaths) }}</h6>
        </div>
    </div>
</template>

<script>
export default{
    name: 'DataBoxes',
    props: ['stats'],
    methods:{
        numberWithCommas(x) {
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
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
