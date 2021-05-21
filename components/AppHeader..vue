<template>
    <header class="header">
        <h1 class="title">
            <ul>
                <li>
                    <nuxt-link to="/">Home</nuxt-link>
                </li>
                 <li>
                    <nuxt-link to="/about">About</nuxt-link>
                </li>
                  <li>
                    <nuxt-link to="/recipes">Recipe</nuxt-link>
                </li>
            </ul>
        </h1>
    </header>
</template>

<script>
export default {
    name: 'AppHeader'
}
</script>
<style>
*{
    padding: 0%;
    margin: 0%;
}
.header{
    overflow: hidden;
    background-color: #f1f1f1;
    padding: 10px 5px;
}
.header ul{
    display: flex;
    list-style-type: none;

}
.header a{
  float: left;
  color: black;
  text-align: center;
  padding: 12px;
  text-decoration: none;
  font-size: 18px;
  line-height: 25px;
  border-radius: 4px;
}
.header a:hover{
    background-color: #ddd;
    color: black;
}


</style>