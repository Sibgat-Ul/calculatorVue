<template>
    <div class="main">
        <div class="dis">
            <div class="" > {{ res }} </div>
            <div class="" > {{ dis }} </div>
            <input type="text" name="" class="" v-model="n1">
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
            let dis = ref(0);
            let res = ref(0);
            let equalPressed = ref(false);

            let enterValue = ((num) => {
                n1.value = num;
            })

            let equal = (() => {
                equalPressed.value = true;
                dis.value = res.value;
            })

            let clear = (() => {
                dis.value = 0;
                res.value = 0;
                n1.value = 0;
                equalPressed.value = false;
            })
                        
            let add = (() => {
                res.value += n1.value;
                console.log(res.value)
            });
            
            let ded = (() => {
                res.value -= n1.value;
            });
            
            let multi = (() => {
                if(res.value == 0) res.value = n1.value;
                else res.value *= n1.value;
            });

            let div = (() => {
                res.value /= n1.value;
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