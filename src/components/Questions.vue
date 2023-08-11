<template>
    <div class="questions-ctr">
        <div class="progress">
            <div class="bar" :style="{ width: `${(questionsAnswered / questions.length) * 100}%` }"></div>
            <div class="status">{{ questionsAnswered }} out of {{ questions.length }} questions answered</div>
        </div>
        <transition-group name="fade">
            <div class="single-question" v-for="(question, id) in questions" :key="question.q"
                v-show="questionsAnswered === id">
                <div class="question">{{ question.q }}</div>
                <div class="answers">
                    <div class="answer" v-for="answer in question.answers" :key="answer.text"
                        @click.prevent="selectedAnswer(answer.is_correct)">{{ answer.text }}</div>
                </div>
            </div>
        </transition-group>
    </div>
</template>

<script>
export default {
    name: "Questions",
    props: ["questions", "questionsAnswered"],
    emit: ["question-answered"],
    methods: {
        selectedAnswer(is_correct) {
            this.$emit('question-answered', is_correct)
        }
    },
}
</script>