<template>
    <li v-bind:class="{stop:todo.completed}">
        <span class="timerName">{{todo.title}}</span>
        <Timer/>
        <button class="remove"
            v-on:click="$emit('remove-todo', todo.id)"
        ><i class="fa fa-trash" aria-hidden="true"></i></button>
    </li>
</template>

<script>
    import Timer from '../components/Timer'
    export default  {
        components:{
          Timer
        },
        props: {
            todo: {
                type:Object,
                required:true
            },
            index:Number
        }
    }
</script>
<style>
    .timerName {
        font-family: Nunito Sans;
        font-style: normal;
        font-weight: 800;
        font-size: 20px;
        line-height: 30px;
        color: #5586F2;
        text-overflow: ellipsis;
        overflow: hidden;
        max-width: 145px;
        min-width: 145px;
        text-align: left;
        white-space: nowrap;
    }
    .remove {
        background: linear-gradient(135deg, #F23673 0%, #FCA069 100%);
        border-radius: 6px;
        border:none;
        width: 50px;
        height: 50px;
        cursor:pointer;

    }
    .remove i {
        color:#fff;
        font-size: 20px;
    }


</style>
