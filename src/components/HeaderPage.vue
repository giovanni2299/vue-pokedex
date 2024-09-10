<template>
    <header>
        <div class="flex">
            <img class="logo-ball" src="../../public/Logo-svg.png" alt="">

        </div>

    </header>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>

.flex{
    position: relative;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

.logo-ball{
    width: 200px;
    // height: 100px;
}
.logo-text{
    width: 100%;
    height: 100%;
    
}

header{
    min-height: 90px;
    background-color: black;
}

</style>