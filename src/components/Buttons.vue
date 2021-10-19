<template>
    <div class="main">
        <div class="dis">
            <div class="" > {{ res }} </div>
            <div class="" > {{ dis }} </div>
            <div class="">
                <div class="p" style="text-align: end;">
                    Vue Calculator
                </div>

                <input type="text" name="" class="disMain" v-if="equalPressed == false" 
                        v-model="n1">
                <div class="disMain" v-else>
                    <p class="disP">
                        {{ res }}
                    </p>
                </div>
            </div>
        </div>
    </div>

    <div class="btnCont">
        <button class="equal btn" @click="equal"> = </button>
        <button class="clear btn" @click="clear"> C </button>
        <button class="equal btn" @click="equal"> delete </button>
        <button class="add btn" @click="add"> + </button>
        <button class="ded btn" @click="ded"> - </button>
        <button class="div btn" @click="div"> / </button>
        <button class="multi btn" @click="multi"> * </button>
        <button class="multi btn" @click="multi"> % </button>

        <button class="num btn" v-for="num in numbers" :key="num" @click="enterValue(num)">
            {{ num }}
        </button>
    </div>
</template>

<script>
    import { ref } from 'vue';

    export default {
        setup() {
            let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
            let n1 = ref(0);
            let c1 = ref(0);
            let dis = ref(0);
            let res = ref(0);
            let equalPressed = ref(false);
            let symbol = ref("");

            let enterValue = ((num) => {
                equalPressed.value = false;
                n1.value = num;
            })

            let equal = (() => {
                c1.value = n1.value;
                equalPressed.value = true;

                switch(symbol.value) {
                    case "+":
                        res.value += c1.value;
                        break;
                    case "-":
                        res.value -= c1.value;
                        break;
                    case "*":
                        res.value *= c1.value;
                        break;
                    case "/":
                        res.value /= c1.value;
                        break;
                    case "%":
                        //percent();
                        break;
                }

                n1.value = res.value;
            })

            let clear = (() => {
                dis.value = 0;
                res.value = 0;
                n1.value = 0;
                equalPressed.value = false;
            })
                        
            let add = (() => {
                symbol.value = "+";

                c1.value = n1.value;
                res.value += c1.value;

                n1.value = 0;
            });
            
            let ded = (() => {
                symbol.value = "-";
                c1.value = n1.value;

                if (res.value == 0) {
                    res.value = c1.value;
                    res.value -= c1.value;
                } else if (res.value != 0) {
                    res.value -= c1.value;
                }

                n1.value = 0;
            });
            
            let multi = (() => {
                symbol.value = "*";
                c1.value = n1.value;

                if(res.value == 0) {    
                    res.value = c1.value;
                    res.value *= c1.value;
                } else if (res.value != 0) {
                    res.value *= c1.value;
                }

                n1.value = 0;
            });

            let div = (() => {
                symbol.value = "/";
                c1.value = n1.value;

                if (res.value == 0) {
                    res.value = c1.value
                    res.value /= c1.value;
                }
                else {
                    res.value /= c1.value;
                }

                n1.value = 0;
            })

            return {
                n1,
                res,
                dis,
                add,
                ded,
                div,
                equal,
                clear,
                multi,
                numbers,
                enterValue,
                equalPressed
            }
        }
    }
</script>

<style>

</style>
