<template>
    <div class="questions-ctr">
        <div class="progress">
            <div class="bar" :style="{ width: `${quesAns / ques.length * 100}%` }"></div>
            <div class="status">{{ quesAns }} out of {{ ques.length }} questions answered</div>
        </div>
        <transition-group name="fade">
        <div class="single-question" v-for="(que, index) in ques" :key="que.q" v-show="index === quesAns">
            <div class="question">{{que.q}}</div>
            <div class="answers" v-for="an in que.answers" :key="an.text">
                <div class="answer" @click.prevent="selectAns(an.is_correct)">{{ an.text }}</div>
            </div>
        </div>
        </transition-group>
    </div>
</template>

<script>
    export default {
        name: 'Question',
        props: ['ques','quesAns'],
        emits: ['select-event'],
        data() {
            return {
                
            }
        },
        methods: {
            selectAns(is_correct) {
                this.$emit('select-event',is_correct);
                console.log('select event')
            }
        }
    }
</script>

<style>

</style>