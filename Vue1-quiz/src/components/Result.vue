<template>
    <div class="result">
        <div class="title">{{ result[resultIndex].title }}</div>
        <div class="desc">
            {{ result[resultIndex].desc }}
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Result',
        props: ['totalCorrect','result'],
        computed: {
            resultIndex() {
                let index=0;
                this.result.forEach((e, i) => {
                    if(e.min <= this.totalCorrect && e.max >= this.totalCorrect) {
                        index = i;
                    }
                });
                return index;
            }
        }
    }
</script>

<style>

</style>