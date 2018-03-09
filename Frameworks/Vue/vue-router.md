# Vue Router
npm install --save vue-router
```js
//main.js
import VueRounter from 'vue-router';

Vue.use(VueRouter)
const router = new VueRouter({
    mode: 'history', // remove # in url
    base: __dirname,
    routes: [
        {path: '/', component: Home},
        {path: '/about', component: About}
    ]
});

new Vue({
    router,
    template: `
        <div id='app'>
            <router-link to='/'>Home</router-link>
            <router-link to='/about'>About</router-link>

            <router-view></router-view>
        </div>
    `

}).$mount('#app')

//push new page
methods: {
    goHome(){
        this.$router.push('/path');
    }
}
```