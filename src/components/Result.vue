<template>
    <div class="result">
        <div class="title">{{ results[resultIndex].title }}</div>
        <div class="desc">
            {{ results[resultIndex].desc }}
        </div>
    </div>
</template>

<script>
export default {
    name: "Result",
    props: ["results", "totalCorrect"],
    computed: {
        resultIndex() {
            let index = 0

            this.results.forEach((result, indexR) => {
                if (result.min <= this.totalCorrect && result.max >= this.totalCorrect) {
                    index = indexR
                }
            })
            return index
        }
    }
}
</script>