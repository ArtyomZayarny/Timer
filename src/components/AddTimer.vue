<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title" placeholder="Timer Name">
        <button type="submit">Create Timer</button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                title:''
            }
        },
        methods: {
            onSubmit() {
              // console.log('Submit',this.title)
                if (this.title.trim()) {
                    const newTodo = {
                        id:Date.now(),
                        title:this.title,
                        completed:false
                    }
                    this.$emit('add-todo',newTodo);
                    this.title = '';
                }
            }
        }
    }
</script>
<style>
    input[type="text"] {
        font-family: Nunito Sans;
        font-style: normal;
        font-weight: normal;
        font-size: 17px;
        line-height: 23px;
        color: rgba(103, 108, 117, 0.7);
        background: #F8F9FA;
        border: 1px solid #E7E8EA;
        box-sizing: border-box;
        border-radius: 6px;
        padding: 15px 20px;
        width: 305px;
    }
    button[type="submit"] {
        background: linear-gradient(163.14deg, #FF8E64 0%, #FFE641 100%);
        border-radius: 6px;
        font-family: Nunito Sans;
        font-style: normal;
        font-weight: bold;
        font-size: 17px;
        line-height: 24px;
        text-align: center;
        letter-spacing: 1px;
        color: #FFFFFF;
        outline: none;
        border:none;
         padding: 13px 25px;
        margin-left: 20px;
    }
    form {
        margin-bottom: 30px;
    }
</style>

