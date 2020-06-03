<template>
    <div class="timer">
        <div class="score">
            <span>{{hours}}:{{minuts}}:{{seconds}}</span>
        </div>
        <button class="control"  v-bind:class="{'play':pause, 'pause':play }"  @click="controlTimer">
            <i class="fa "
               v-bind:class="{'fa-play':pause, 'fa-pause':play }"
               aria-hidden="true"></i>
        </button>
    </div>
</template>

<script>
export default {

    data() {
        return {
            seconds:0,
            minuts:0,
            hours:0,
            status:'Play',
            play:true,
            pause:false,
            intervalsArr:[],
        }
    },
mounted() {
    //Render initals values 00:00:00
    this.seconds = +this.seconds < 9  ? `0${+this.seconds }` : +this.seconds ;
    this.minuts = +this.minuts < 9  ? `0${+this.minuts }` : +this.minuts ;
    this.hours = +this.hours < 9  ? `0${+this.hours }` : +this.hours ;

    this.controlTimer()
},
    methods: {
        controlTimer() {
            if  (this.status === 'Play') {
                    this.pause = false;
                    this.play = true;
                const interval = setInterval( () => {
                    //Increase seconds
                   this.seconds = +this.seconds < 9 ? `0${+this.seconds + 1}` : +this.seconds + 1;
                   //Increase minuts
                    if (this.seconds === 60) {
                        this.seconds = "00";
                        this.minuts = +this.minuts < 9 ? `0${+this.minuts + 1}` : +this.seconds + 1;
                    }
                    //Increse hours
                    if ( this.minuts === 60) {
                        this.minuts = "00";
                        this.hours = +this.hours < 9 ? `0${+this.hours + 1}` : +this.hours + 1;
                    }
                    //
                },1000)
                this.intervalsArr.push(interval)
            } else {
                //Clear interval
                clearInterval(this.intervalsArr[0]);
                this.pause = true;
                this.play = false;
                this.intervalsArr = [];
            }
            //Toggle button status
            this.status = this.status !== 'Pause' ? 'Pause' : 'Play';

        }
    }
    
}

</script>

<style scoped>
.score {
    background: #E7E8EA;
    border: 1px solid #E7E8EA;
    box-sizing: border-box;
    border-radius: 6px;
    padding: 15px 25px;
}
.timer {
    display: flex;
    margin-left: 20px;
}
.score span {
    font-family: Nunito Sans;
    font-style: normal;
    font-weight: normal;
    font-size: 17px;
    line-height: 23px;
    color: #676C75;
}
.control {
    margin-left: 42px;
    margin-right: 20px;
    border:none;
    outline: none;
    cursor:pointer;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    color:#fff;
}
    .control.play {
        background: linear-gradient(135deg, #7956EC 0%, #2FB9F8 100%);
    }
    .control.pause {background: linear-gradient(135deg, #009FC5 0%, #3CECB0 100%);}
    .play i {
        color:#fff;
        font-size: 16px;
    }
</style>
