<template>
    <div class="circular-progress"
        :style="`background: conic-gradient(${color} calc(${percent}deg * 3.6), #ffffff00 0deg);`">
        <div class="value-container">
            {{ percent }}%
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props: {
        percent: String,
        color: String
    }
}
</script>

<style  scoped>
.circular-progress {
    position: relative;
    height: 40px;
    width: 40px;
    background-color: orange;
    border-radius: 50%;
    display: grid;
    place-items: center;
    background: conic-gradient(#f69d3c calc(50deg * 3.6), #ffffff00 0deg);
}

.circular-progress::before {
    content: "";
    position: absolute;
    height: 84%;
    width: 84%;
    background-color: #fff;
    border-radius: 50%;
}

.value-container {
    position: relative;
    font-size: var(--font-size-4);
}
</style>