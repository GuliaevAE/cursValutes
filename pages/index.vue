<template>
    <div>
        <div :class="$style.header">
            <NuxtLink to="/calc" class="mr-5">
                Калькулятор
            </NuxtLink>
            <NuxtLink to="/curs">
                Курс рубля
            </NuxtLink>
        </div>


        <NuxtChild :datas='datas'/>


    </div>
</template>

<script>
export default {
    async asyncData({ $axios }) {
        const datas = await $axios.$get(`https://www.cbr-xml-daily.ru/daily_json.js`)
        console.log(datas)
        return { datas }
    },

    computed:
    {
    }
}
</script>

<style  module>
.header{
    width: 100%;
    background:rgba(248, 248, 248, 1);
    padding:10px 3%;
    font-weight: 500;
}

</style>
