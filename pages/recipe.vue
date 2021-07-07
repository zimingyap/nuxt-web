<template>
  <div>
  <b-input-group class="mt-3 mx-auto" style="width: 40%;" v-model="recipeName" >
    <template #append>
      <b-input-group-append>
        <b-button variant="info" v-on:click="getRecipe">Search</b-button>
      </b-input-group-append>
    </template>
    <b-form-input></b-form-input>
  </b-input-group>

  </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            recipes: [],
            recipeName: '',
        }
    },
    methods: {
        getRecipe: function(){
            axios.get('https://www.themealdb.com/api/json/v1/1/search.php?s='+this.recipeName)
            .then(response => response.json())
            .then(data => 
                 { let html = "";
                    if (data.meals) {
                        data.meals.forEach(meal => {
                            html += `
                        <div class = "meal-item" data-id = "${meal.idMeal}">
                            <div class = "meal-img">
                                <img src = "${meal.strMealThumb}" alt = "food">
                            </div>
                            <div class = "meal-name">
                                <h3>${meal.strMeal}</h3>
                                <a href = "#" class = "recipe-btn">Get Recipe</a>
                            </div>
                        </div>
                    `;
                        });
                        mealList.classList.remove('notFound');
                    } else {
                        html = "Sorry, we didn't find any meal!";
                        mealList.classList.add('notFound');
                    }

                    mealList.innerHTML = html;});
            console.log(data);
        }
    },

    // watch: {
    //     recipeName: 'getRecipe'
    // }

//    async fetch(){
//        this.recipes = await fetch('www.themealdb.com/api/json/v1/1/search.php?s=${}')
//    }


}
</script>

<style>

</style>