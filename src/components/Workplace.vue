<template>
    <div>
        <input 
            type="text"
            :style="data.inputClass" 
            v-show="data.showInput"
            v-model="number" 
            @keyup.enter="finishedInput"
        />
        <span v-show="data.displayNumber">
            {{ data.number }}
        </span>
        <div class="btn-container">
            <button 
                @click="finishedInput"
                class="btn btn-success"
            >
                ОК
            </button>
            <button 
                @click="back"
                class="btn btn-danger"
            >
                Назад
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Workplace',

        props : {
            data: {
                type: Object,
                require: true,
            }
        },

        data() {
            return {
                display: false,
                number: '',
            }
        },

        methods: {
            back() {
                this.$emit('back', this.display)
            },

            finishedInput() {
                this.$emit('finishedInput', this.number)
                
                setTimeout(() => this.number = '', 500)
            },
        }
    }
</script>

<style scoped>
    div {
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
    }

    .btn-container {
        display: flex;
        min-width: 200px;
        margin-top: 50px;
        flex-direction: row;
        justify-content: space-between;
    }

    .btn {
        display: flex;
        width: 75px;
        height: 30px;
        justify-content: center;
        align-items: center;
    }

    [type="text"] {
        font-size: 25px;
        text-align: center;
        padding: 5px;
        border: solid 1px #333;
        border-radius: 10px;
    }

    span {
        font-size: 32px;
    }
</style>