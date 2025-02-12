<template> 
    <main class="login__main">
        <h1>LoginPage</h1>
        <form v-on:submit.prevent="submitHandler">
            <section>
            <article>
                <label for="email"></label>
                <input 
                v-model="data.email"
                id="email"
                type="email"
                placeholder="entrez votre email"
                class="input"
                />
            </article>
            <article>
                <label for="password"></label>
                <input
                v-model="data.password"
                id="password"
                type="password"
                placeholder="entrez votre mot de passe"
                class="input"
                />
            </article>
        </section>
        <section>
            <button
            type="submit"
            class="button is-primary"
            >Valider</button>
            <button
            type="reset"
            class="button is-danger"
            >réinitialiser</button>
        </section>

        </form>
    </main>
</template>

<script lang="ts" setup>
import { watch, reactive } from "vue"

const data = reactive({
    email: "",
    password: ""
})

watch(data, (val) => {
    console.log('Changement dans la variable data')
})

const isUserInputValid = (input: string): boolean => {
    const pattern = new RegExp('^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$');
    return pattern.test(input);
}

const isPasswordValid = (password: string): boolean => {
    const pattern = new RegExp(/^(?=.*?[A-Z])(?=.*?[a-z])(?=.*?[0-9])(?=.*?[#?!@$%^&*-]).{8,}$/);
    return pattern.test(password);
}

const submitHandler = () => {
    if (!isUserInputValid(data.email)){
        alert('Email invalide');
        return;
    }
    if (!isPasswordValid(data.password)){
        alert('Mot de passe invalide : il doit contenir au moins 8 caractères, une majuscule, une minuscule, un chiffre et un caractère spécial.');
        return;
    }
    console.log('Email et mot de passe valides');
}

const inputHandler = function (){

}

</script>

<style lang="scss" scoped>
.login__main {

}
</style>
