<template>
    <div :class="$style.container">
        <span :class="[$style.Title, $style.boldFont] ">Курс рубля</span>

        <div class="flex w-full  flex-wrap justify-between">
            <div :class="$style.card" v-for="(item,k) in Object.values(this.datas.Valute)" :key="item.Name">
                <div :class="[$style.symbol, k%2!=0?$style.redBord:$style.blueBord ]" >
                    <img v-if="k%2!=0" src="~/assets/images/handRed.svg" alt="">
                    <img v-if="k%2==0" src="~/assets/images/handBlue.svg" alt="">
                </div>
                <span :class="$style.boldFont">{{item.CharCode}}</span>
                <span>{{item.Name}}</span>
                <ul>
                    <li>
                        <span :class="$style.boldFont">Номинал: {{item.Nominal}}</span>
                    </li>
                    <li>
                        <span :class="$style.boldFont">Курс: {{item.Value}}</span>
                    </li>
                </ul>
            </div>
            <div :class="$style.footer">
                <div :class="[$style.symbol, $style.blueBord] ">
                    <img src="~/assets/images/infoBlue.svg" alt="">
                </div>
                <span class="text-2xl" :class="$style.boldFont">Телефон: 8 (800) 888-90-28, </span>
                <span class="text-2xl" :class="$style.boldFont">email: info@example.ru</span>
            </div>
        </div>
    </div>
</template>




<script>
export default {
    props: ['datas']
}
</script>

<style module>

.footer {
    display: flex;
    flex-direction: row;
    background: rgba(248, 248, 248, 1);
    width: 100%;
    box-sizing:border-box;
    padding: 30px 25px;
    border-radius: 15px;
    margin-top: 20px;
}

.footer span{
    color: rgba(15, 68, 113, 1);
}

.card {
    width: 32%;
    min-height: 50px;
    background: rgba(248, 248, 248, 1);
    border-radius: 15px;
    box-shadow: 0 1px 3px 0px rgba(0, 0, 0, 0.31);
    display: flex;
    flex-direction: column;
    padding: 30px 25px;
    margin-top: 20px;
}

.container {
    width: 100%;
    box-sizing: border-box;
    padding: 20px 3%;
}

.boldFont {
    font-weight: 500;
}

.Title {
    font-size: 30px;
    color: rgba(15, 68, 113, 1);
}

.symbol {
    height: 50px;
    width: 50px;
    border: 3px solid rgba(15, 68, 113, 1);
    border-radius: 0 10px 0 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    box-sizing: border-box;
    padding: 5px;
    margin-right: 20px;
}

.blueBord{
    border: 3px solid rgba(15, 68, 113, 1);
}

.redBord{
    border: 3px solid rgba(224, 32, 37, 1)
}

span {
    margin-top: 10px;
}



li::before {
    content: "";
    display: inline-block;
    height: 10px;
    width: 10px;
    border: 2px solid red;
    border-radius: 50%;
    margin-right: 10px;
}

@media (max-width: 800px){
    .card{
        width: 47%;
    }
}
@media (max-width: 400px){
    .card{
        width: 100%;
    }
    .footer{flex-direction: column;}
}
</style>