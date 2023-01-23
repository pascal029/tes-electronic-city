<script>
export default {
    emits : ['login'],
    data () {
        return {
            username : '',
            password : ''
        }
    },
    methods : {
        loginAction(data){
            data = {
                username : this.username,
                password : this.password
            }
            this.$emit('login', data)
        }
    }
}
</script>


<template>
    <div class="container px-6 py-12 h-full">
        <div class="grid h-48 mt-10">
            <div class="grid h-48 place-items-start content-end">
                <p id="start" class="font-bold">Let's get started!</p>
                <p id="words">Sign in for work absence</p>
            </div>
            <div class="mt-5">
                <form @submit.prevent="loginAction">
                    <div>
                        <input v-model="username" type="text" placeholder="Username" class="input input-bordered w-full max-w-xs" />
                    </div>
                    <div>
                        <input v-model="password" type="password" placeholder="Password" class="input input-bordered w-full max-w-xs mt-2" />
                    </div>
                    <div>
                        <button type="submit" class="btn w-full max-w-xs mt-2" id="loginButton">Login</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<style scoped>
#start {
    color : #0019FB;
    font-size: 24px;
}

#words {
    color : #785D5D;
    font-size: 16;
}
#loginButton {
    background-color: #0019FB;
}
</style>