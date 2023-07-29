<template>
    <div class="empty">
        <img src='https://freesvg.org/img/1554961904.png' alt="EmptyList"/>
        <span>Empty list</span>
    </div>
</template>

<style scoped>
    .empty{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    span{
        margin: 30px;
        font-size: 36px;
        font-weight: bold;
    }

    img {
        margin: 30px;
        width: 200px;
        height: 200px;
    }
</style>