<template>
    <div>
        <b-container class="bv-example-row">
            <b-row>
                <b-col sm="6" offset='3'>
                    <LazyQuestionBox   
                    v-if="questions.length"
                        :currentQuestion="questions[index]"
                        :next="next"
                        :increment="increment"
                        />    
                    <!-- <question-box
                        v-if="questions.length"
                        :currentQuestion="questions[index]"
                        :next="next"
                        :increment="increment"
                    /> -->
                </b-col>
                
            </b-row>
        </b-container>
    </div>
</template>

<script>
import QuestionBox from '../components/QuestionBox.vue'
    export default {
        head(){
        return{
            title: 'Quiz',
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'Quiz app'
                }
            ]
        };
    },
        components: {
            QuestionBox
        },
        data() {
            return{
                questions: [],
                index: 0,
                numCorrect: 0,
                numTotal: 0,
            }
        },
        methods: {
            next(){
               this.index++ 
            },
            increment(isCorrect){
                if (isCorrect){
                    this.numCorrect++
                }
                this.numTotal++
            }
        },
        // mounted: function(){
        //     fetch("https://opentdb.com/api.php?amount=50&category=9", {
        //         method: 'get'
        //     })
        //     .then((response)=> {
        //         return (response.json());
        //     })
        //     .then((jsonData) => {
        //         this.questions = jsonData.results
        //     })
        // },
        async fetch() {
            this.questions = await fetch('https://opentdb.com/api.php?amount=50&category=9',{ method: 'get'}).then(res => 
            res.json()).then(jsonData => this.questions = jsonData.results);
        }
    }
</script>

<style>
       
</style>