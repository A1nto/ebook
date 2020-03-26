<template>
    <div id="app">
        <router-view />
    </div>
</template>

<script>
export default {
    name: 'App'
}
function ready () {
    const html = document.querySelector('html')
    let fontSize = window.innerWidth / 10
    fontSize = fontSize > 50 ? 50 : fontSize
    html.style.fontSize = fontSize + 'px'
}
document.addEventListener('DOMContentLoaded', ready, false)
window.addEventListener('resize', ready, false)
</script>

<style></style>
