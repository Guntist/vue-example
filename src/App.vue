<template>
    <div class="container" id="app">
        <!-- <img src="./assets/logo.png"> -->
        <button><router-link :to="{ name: 'HelloWorld' }">Home (HelloWorld)</router-link></button>
        <button><router-link to="/props-type">Props Default Type</router-link></button>
        <button><router-link to="/list-rendering">List Rendering</router-link></button>
        <button><router-link to="/list-filtering">List Filtering</router-link></button>
        <button><router-link to="/event-handling">Event Handling</router-link></button>
        <button><router-link to="/parent-child-event-handling">Parent Child Event Handling</router-link></button>
        <button><router-link to="/parent-child-twoway-binding">Parent Child Twoway Binding</router-link></button>
        <button><router-link to="/element-find">Element Find</router-link></button>
        <button><router-link to="/style-bind">Style Bind</router-link></button>
        <button class="btnbold"><router-link to="/lifecycle-hook">LifeCycle Hook</router-link></button>
        <button class="btnbold"><router-link to="/mixin">Mixin</router-link></button>
        <button class="btnbold"><router-link to="/scoped-slots">Scoped Slots</router-link></button>
        <button class="btnbold"><router-link to="/render-function">Render Function</router-link></button>
        <button class="btnbold"><router-link to="/custom-render-function">Custom Render Function</router-link></button>
        <button class="btnbold"><router-link to="/watcher">Watch Options</router-link></button>
        <button><router-link to="/form-control">Form Control</router-link></button>
        <button><router-link to="/coins/ethereum">Dynamic path routes - Ethereum</router-link></button>
        <button><router-link to="/coins/bitcoin">Dynamic path routes - Bitcoin</router-link></button>
        <button><router-link to="/filters">Filters</router-link></button>
        <button class="btnbold"><router-link to="/service-caller">Service Caller</router-link></button>
        <button class="btnbold"><router-link to="/mock-service">Mock Service</router-link></button>
        <button class="btnbold"><router-link to="/dynamic-component-mount">Dynamic Component (Mount)</router-link></button>
        <router-view/>
    </div>
</template>

<script>
export default {
    name: 'app'
};
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
.btnbold {
    border-color: orange;
}
</style>
