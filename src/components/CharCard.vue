<script>
export default {
    props: {
        char: Object,
        index: Number,
    }
}
</script>

<template>
    <div class="container">
        <img :src="char.image" alt="">
        <h4 class="name">
            {{char.name}}
        </h4>
        <span class="status">
            {{char.status}}
        </span>
    </div>
</template>

<style lang="scss" scoped>
@use "../styles/partials/_palette.scss";

.container{

    background-color: palette.$primary;
    text-align: center;
    padding: .6rem;

    img{
        width: 100%;
    }

    h4{
        color: white;
    }

    .status{
        color: palette.$descText;
    }
}
</style>