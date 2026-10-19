<script setup>
const props = defineProps({
    dragonProps: Object, 

})

</script>



<template>
    <article>
        <h3>{{ dragonProps.name }}</h3>
        <img :src="dragonProps.img_url" alt="">
        <form>
            <label for="betterName">Rename to:</label>
            <input type="text" placeholder="Better name..." id="betterName" required>
            <input type="submit" value="Update name" />
         </form>
    </article>


</template>



<style scoped>
article{
border: 2px solid red;
border-radius: 5px;
padding: 1rem;

h3{
    text-align: center;
}

img{
    max-width: 100%;
}

form{
    display: flex;
    align-items: center;
    gap: 1rem;

    input:last-of-type{
        background-color: red;
        border-radius: 5px;
        padding: .5rem 1.5rem;
        margin-left: auto;
        border: none;
        color: white;
        cursor: pointer;
    }
}

}
</style>