<template>
  <div class="questions-ctr">
        <div class="progress">
            <div class="bar"></div>
            <div class="status">{{questionsAnswered}} out of 3 questions answered</div>
        </div>
        <div class="single-question" v-for="(question, index) in questions" :key="question.q" v-show="questionsAnswered === index">
            <div class="question">{{question.q}}</div>
            <div class="answers">
                <div class="answer" v-for="answer in question.answers" :key="answer.text" @click.prevent="updateQA(answer.is_correct)">{{answer.text}}</div>

            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Questions",
    props: [
        "questions",
        "questionsAnswered",
        "updateQA"
    ]
}
</script>

<style>

</style>