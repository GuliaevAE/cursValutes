<template>

    <div :class="$style.container">
        <span :class="[$style.Title, $style.boldFont] ">Валютный калькулятор</span>
        <div :class="$style.contWithBlocks">
            <div :class="$style.miniCont">
                <div :class="$style.labelAndInput">
                    <span>Валюта 1</span>
                    <input :class="{[$style.ok]:valute1!==0}" id="valute1" @input="changeInputs" placeholder="Введите название или код" type="text">
                   
                </div>
                <div :class="$style.labelAndInput">
                    <span>Валюта 2</span>
                    <input :class="{[$style.ok]:valute2!==0}" id="valute2" @input="changeInputs" placeholder="Введите название или код" type="text">
                   
                </div>
                <div :class="$style.labelAndInput">
                    <span>Количество</span>
                    <input id="count" @input="changeInputs" placeholder="Введите название или код" type="number">
                    <div v-if="count!==0">{{typeof count}}</div>
                </div>
                <div :class="$style.endValue">
                    <div :class="$style.symbol">
                        <img src="~/assets/images/infoRed.svg" alt="">
                    </div>
                    <span :class="$style.boldFont">Итого: {{finalValue?finalValue:'...'}}</span>
                </div>
            </div>
            <div :class="$style.miniCont">
                <div :class="$style.listAndImages">
                    <span :class="$style.boldFont">
                        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Maxime, voluptatem.
                    </span>
                    <ul>
                        <li>
                            Lorem ipsum dolor.
                        </li>
                        <li>
                            Lorem ipsum dolor, sit.
                        </li>
                        <li>
                            Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                        </li>
                        <li>
                            Lorem ipsum adipisicing elit.
                        </li>
                        <li>
                            Lorem ipsum dolor, sit amet consectetur .
                        </li>
                        <li>
                            Lorem ipsum dolor.
                        </li>
                    </ul>
                    <div :class="$style.imagesBlock">
                        <div :class="$style.img" class="bg-[url('~/assets/images/img-1.jpg')]"></div>
                        <div :class="$style.img" class="bg-[url('~/assets/images/img-2.jpg')] rounded-tr-3xl"></div>
                        <div :class="$style.img" class="bg-[url('~/assets/images/img-3.jpg')] rounded-bl-3xl"></div>
                        <div :class="$style.img" class="bg-[url('~/assets/images/img-4.png')]"></div>
                    </div>
                </div>

            </div>
            <div :class="$style.footer">
                <div class="flex flex-col" :class="$style.help">
                    <span :class="[$style.blueSpan, $style.boldFont]">Нужна помощь</span>
                    <span :class="[$style.blueSpan, $style.boldFont]">Мы поможем! Просто свяжитесь с нами.</span>
                    <span>Наши специалисты с радостью ответят на все ваши вопросы и дадут проффессипональную
                        консультацию по товарам.</span>
                </div>
                <div class="flex flex-col justify-center items-center" :class="$style.help">
                    <a href="" :class="[$style.blueSpan, $style.boldFont]">8 (800) 888-90-28</a>
                    <span>ИЛИ</span>
                    <a href="" :class="$style.blueSpan">info@example.ru</a>

                </div>

            </div>
        </div>
    </div>


</template>


<script>
export default {
    props:['datas'],
    data: function () {
        return {
            valute1: 0,
            valute2: 0,
            count: 0,
            finalValue:0,
            

        }
    },
    methods: {
        changeInputs(e) {
            if (e.target.id === 'valute1') {
                let sub = 0
                Object.values(this.datas.Valute).map(x => {
                    if (e.target.value.toLowerCase() === x.NumCode.toLowerCase() || e.target.value.toLowerCase() === x.CharCode.toLowerCase() || e.target.value.toLowerCase() === x.Name.toLowerCase()) {
                        sub = x.Value
                    }
                    return x
                })
                this.valute1 = sub
                
            }
            if (e.target.id === 'valute2') {
                let sub = 0
                Object.values(this.datas.Valute).map(x => {
                    if (e.target.value.toLowerCase() === x.NumCode.toLowerCase() || e.target.value.toLowerCase() === x.CharCode.toLowerCase() || e.target.value.toLowerCase() === x.Name.toLowerCase()) {
                        sub = {Value:x.Value, Nominal:x.Nominal}
                    }
                    return x
                })
                this.valute2 = sub
                
            }
            if (e.target.id === 'count') {
                this.count=Number( e.target.value)
                if(this.value1!==0&&this.value2!==0){
                    this.finalValue = this.valute1/this.valute2.Value*this.valute2.Nominal*this.count
                }
            }
        }
    }

}

</script>


<style module>


.ok{
    box-shadow: 0 0 5px rgb(4, 255, 4);
}
.footer {
    background: rgb(225, 236, 255);
    display: flex;
    flex-direction: row;
    width: 100%;
    border-radius: 10px;
    margin-top: 20px;
    box-sizing: border-box;
    padding: 20px 15px;
}

.footer span {
    font-size: 15px;
}

.blueSpan {
    color: rgba(15, 68, 113, 1);
    font-size: 20px;
}

.imagesBlock {
    width: 50%;
    height: auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center
}

.help {
    width: 50%;
}

.img {
    height: 48%;
    width: 48%;
    background-size: cover;
}

.endValue {
    background: rgb(225, 236, 255);
    padding: 20px 15px;
    margin-top: 30px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    margin-bottom: 20px;
}

.endValue span {
    color: rgba(15, 68, 113, 1);
    font-size: 20px;
    margin-left: 15px;
}

.boldFont {
    font-weight: 500;
    font-size: 30px;
}

.symbol {
    height: 45px;
    width: 45px;
    border: 3px solid red;
    border-radius: 0 10px 0 10px;
    display: flex;
    justify-content: center;
    align-items: center;
}



.listAndImages {
    background: rgb(225, 236, 255);
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    padding: 20px;
    border-radius: 20px;
    width: 100%;
    justify-content: space-between;
}

.listAndImages span {
    width: 100%;
    font-size: 18px;
    color: rgba(15, 68, 113, 1);
}

.Title {
    font-size: 30px;
    color: rgba(15, 68, 113, 1);
}

.labelAndInput {
    width: 100%;
    display: flex;
    flex-direction: column;
    margin-top: 20px;
}

.labelAndInput input {
    width: 100%;
    height: 50px;
    border: 1px solid grey;
    border-radius: 5px;
    box-sizing:border-box;
    padding-left: 15px;
}

.labelAndInput span {
    font-weight: 500;
}

.contWithBlocks {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

}

.container {
    width: 100%;
    box-sizing: border-box;
    padding: 20px 3%;
}


.blockForMinicounts {
    display: flex;
    width: 100%;
    justify-content: space-between;
}

.miniCont {
    width: 48%;
    display: flex;
    flex-direction: column;
}

ul {
    width: 48%;
}

ul li {
    margin-top: 10px;
    margin-bottom: 10px;
    font-size: 15px;
}

li::before {
    content: "";
    display: inline-block;
    height: 10px;
    width: 10px;
    border: 2px solid red;
    border-radius: 50%;
}

@media (max-width: 768px) {

    .imagesBlock {
        flex-direction: column;
        align-items: flex-end;
        justify-content: space-around;
    }

    .img {

        width: 80%;
        height: 20%;
        border-radius: 15px 0 15px 0;
    }
}

@media (max-width: 500px) {
    .miniCont {
        width: 100%;
    }

    .footer {
        flex-direction: column;
        text-align: center
    }

    .imagesBlock {
        width: 100%;
        flex-direction: row;


    }

    .img {
        width: 23%;
        height: 50px;
    }

    .help {
        width: 100%;
    }

    ul {
        width: 100%;
    }
}
</style>