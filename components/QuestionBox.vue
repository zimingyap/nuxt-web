<template>
    <div class="question-box-container">
        <b-jumbotron>
            <template slot="lead">
               {{currentQuestion.question}}
            </template>

            <hr class="my-4"/>
            <b-list-group>
                <b-list-group-item 
                    v-for="(answer,index) in answers" 
                    :key="index"
                    @click.prevent="selectAnswer(index)"
                    :class="[
                        !answered && selectedIndex === index ? 'selected' :
                        answered && correctIndex === index ? 'correct' :
                        answered && selectedIndex === index && correctIndex !== index ? 'incorrect' : ''
                        ]"
                >
                {{answer}}
                </b-list-group-item>
               
            </b-list-group>
            <p >
                
            </p>

            <b-button variant="primary" 
            @click="submitAnswer"
            :disabled="selectedIndex === null || answered">
                Submit
            </b-button>
            <b-button @click="next" variant="success" href="#">Next Question</b-button>
        </b-jumbotron>
    </div>
</template>


<script>
import _ from 'lodash'
    export default {
        name: 'QuestionBox',
        props: {
            currentQuestion: Object,
            next: Function,
            increment: Function
        },
        data() {
            return{
                selectedIndex: null,
                correctIndex: null,
                shuffledAnswers: [],
                answered: false,
            }
        },
        computed: {
            answers() {
                // let answers = [...this.currentQuestion.incorrect_answers]
                // answers.push(this.currentQuestion.correct_answer)
                return this.shuffledAnswers  
            }
        },
        methods: {
            selectAnswer(index) {
                this.selectedIndex = index
            },
            shuffleAnswers(){
                let answers = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer]
                this.shuffledAnswers = _.shuffle(answers)
                this.correctIndex = this.shuffledAnswers.indexOf(this.currentQuestion.correct_answer)
            },
            submitAnswer(){
                let isCorrect = false
                if (this.selectedIndex === this.correctIndex){
                    isCorrect = true
                }
                this.answered = true
                this.increment(isCorrect)
            }
        },
        watch: {
            currentQuestion: {
                immediate: true, //shuffle the first question
                handler(){
                    this.selectedIndex = null
                    this.shuffleAnswers()
                    this.answered = false
                }
                
            }
        }
    }
</script>

<style >
    .question-box-container{
        padding-top: 20px;
        
    }
    .list-group-item:hover {
        background-color: #EEE;
        cursor: pointer;
    }
    .selected {
        background-color: lightblue;
    }
    .correct {
        background-color: green;

    }
    .incorrect {
        background-color: red;
    }
</style>