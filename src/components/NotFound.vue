<template>
    <div class="not-found-page">
        <img src="../assets/404.png" alt="404">
    </div>
    <h1 class="animate">Страница не найдена</h1>
</template>
  
<script>
export default {
    name: 'NotFoundPage',
};
</script>
  
<style scoped>
.not-found-page {
    text-align: center;
    margin-top: 80px;
}

.not-found-page {
    animation: scaleAnimation 40s infinite;
}

@keyframes scaleAnimation {
    0% {
        transform: scale(1);
    }

    50% {
        transform: scale(1.2);
    }

    100% {
        transform: scale(1);
    }
}

h1 {
    font-size: 100px;
    color: red;
}

img {
    width: 400px;
}
</style>
  