<template>
    <nav class="navbar-container">
        <section class="navbar-right">
            <div class="logo-container">
                <img height="48" src="../assets/aduro-logo-r.svg" />
            </div>
            <h1 class="aduro-heading">COACHING</h1>
        </section>
        <section class="navbar-center"></section>
        <section class="navbar-left"></section>
    </nav>
</template>

<script>
export default {
    name: 'NavBar'
}
</script>

<style lang="scss" scoped>
.navbar-container {
    position: absolute;
    top: 0;
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
}
.navbar-right, .navbar-left, .navbar-center {
    display: flex;
    flex-direction: row;
    align-items: center;
}
.logo-container {
    padding: 5px;
}
.aduro-heading {
    color: $a-red;
    font-size: 1.8em;
    padding-left: 5px;
    font-weight: lighter;
    margin: 0;
}
</style>