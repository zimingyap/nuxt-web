<template>
    <div>
        <h1>This is a nuxt app</h1>
        <Nuxt />
    </div>
</template>

<script>
export default {
   
    head(){
        return{
            title: 'About the app',
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'Find any recipe you want'
                }
            ]
        };
    }
};
</script>