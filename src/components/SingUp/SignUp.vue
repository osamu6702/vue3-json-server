<script setup>
import axios from 'axios';
import { reactive, computed, onMounted } from 'vue';
import { useRouter } from 'vue-router';
import { useVuelidate } from '@vuelidate/core'
import { required, email, sameAs, minLength } from '@vuelidate/validators'
const router = useRouter()

const state = reactive({
    redirectTo: "/",
})

const userForm = reactive({
    fname: "",
    lname: "",
    email: "",
    password: "",
    password_confirmation: "",
    phone: "",
    address: "",
});

const rules = computed(() => {
    return {
        fname: { required },
        lname: { required },
        email: { required, email },
        password: { required, minLength: minLength(4) },
        password_confirmation: { required, sameAs: sameAs(userForm.password) },
        phone: { required },
        address: { required },
    }
})

onMounted(() => {
    let user = localStorage.getItem('user-info')
    if (user) {
        router.push(state.redirectTo)
    }
})

const v$ = useVuelidate(rules, userForm)

function SignInPage() {
    router.push({ name: "signin" })
}

const submitForm = async () => {
    const result = await v$.value.$validate()
    if (result) {
        alert("Success, form submited!")
        let result = await axios.post('https://json-server-vue3-d109.onrender.com/users', {
            fname: userForm.fname,
            lname: userForm.lname,
            email: userForm.email,
            password: userForm.password,
            password_confirmation: userForm.password_confirmation,
            phone: userForm.phone,
            address: userForm.address,
        })

        if (result.status == 201) {
            console.log("ลงทะเบียนเรียบร้อยแล้วครับ")
            localStorage.setItem("user-info", JSON.stringify(result.data))
            console.log(result.data)
            console.log(JSON.stringify(result.data))
            router.push(state.redirectTo)
        } else {
            console.log("ลงทะเบียนไม่เรียบร้อยแล้วครับ")
        }
    } else {
        alert("Error, form submited!")
    }
}

</script>

<template>
    <div class="container mt-4">
        <div class="row">

            <div class="col-md-5 mb-1">
                <div class="card shadow">
                    <div class="card-header p-0">
                        <img src="https://scontent.xx.fbcdn.net/v/t1.15752-9/420566590_893734672217524_7035407566878439411_n.jpg?stp=dst-jpg_p206x206&_nc_cat=107&ccb=1-7&_nc_sid=510075&_nc_eui2=AeHKARaVcIsbfQM1u22OCX1lV4ZW-PV80PxXhlb49XzQ_MhZOvdbEedOzhPjR8GZ89VTkBd4VkeUCvfELfms9-eR&_nc_ohc=hvChKD1b4AYAX-UZYN9&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AdQSnRHCVy1PtJFJQHFQl2Br5tT9dBtfXwmTfC66SBq3zA&oe=65F254F2"
                            class="card-img-top" alt="sign" height="400px" >
                    </div>
                    <div class="card-body">
                        <p class="card-text text-end">Marionette_Genetics</p>
                    </div>
                </div>
            </div>

            <div class="col-md-7">
                <div class="card shadow">
                    <div class="card-header text-white" style="background: #ff006a ">
                        <h5>Register Form</h5>
                    </div>
                    <div class="card-body">
                        <form @click.prevent>
                            <div class="mb-2">
                                <label for="" class="form-label">Name</label>
                                <input type="text" class="form-control" required v-model="userForm.fname"
                                    placeholder="your name">
                            </div>
                            <span class="text-danger" v-for="error in v$.fname.$errors" :key="error.$uid">
                                {{ error.$message }}
                            </span>

                            <div class="mb-2">
                                <label for="" class="form-label">Lastname</label>
                                <input type="text" class="form-control" v-model="userForm.lname"
                                    placeholder="your lastname" required>
                            </div>
                            <span class="text-danger" v-for="error in v$.lname.$errors" :key="error.$uid">
                                {{ error.$message }}
                            </span>

                            <div class="mb-2">
                                <label for="" class="form-label">E-mail</label>
                                <input type="email" class="form-control" v-model="userForm.email"
                                    placeholder="your E-mail" required>
                            </div>
                            <span class="text-danger" v-for="error in v$.email.$errors" :key="error.$uid">
                                {{ error.$message }}
                            </span>

                            <div class="mb-2">
                                <label for="" class="form-label">Password</label>
                                <input type="password" class="form-control" v-model="userForm.password"
                                    placeholder="Password" required>
                            </div>
                            <span class="text-danger" v-for="error in v$.password.$errors" :key="error.$uid">
                                {{ error.$message }}
                            </span>

                            <div class="mb-2">
                                <label for="" class="form-label">Conirm Password</label>
                                <input type="password" class="form-control" v-model="userForm.password_confirmation"
                                    placeholder="Comfirm Password" required>
                            </div>
                            <span class="text-danger" v-for="error in v$.password_confirmation.$errors" :key="error.$uid">
                                {{ error.$message }}
                            </span>

                            <div class="mb-2">
                                <label for="" class="form-label">Mobile phone</label>
                                <input type="text" class="form-control" v-model="userForm.phone" placeholder="0xx-xxx-xxxx"
                                    required>
                            </div>
                            <span class="text-danger" v-for="error in v$.phone.$errors" :key="error.$uid">
                                {{ error.$message }}
                            </span>

                            <div class="mb-2">
                                <label for="" class="form-label">Address:</label>
                                <textarea v-model="userForm.address" cols="51" rows="2"></textarea>
                            </div>

                            <span class="text-danger" v-for="error in v$.address.$errors" :key="error.$uid">
                                {{ error.$message }}
                            </span>

                            <div class="mb-2">
                                <p type="submit" @click="submitForm" class="btn text-white shadow d-block" style="background: #ff006a ">Register now</p>
                                <p @click="SignInPage" class="text-body text-center d-block">
                                    Already have an Account?
                                    <router-link :to="{ name: 'signin' }" class="text-decoration-none font-weight-bold">
                                        Sing In
                                    </router-link>
                                </p>
                            </div>
                        </form>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Sarabun&display=swap');

.container {
    font-family: 'Sarabun', sans-serif;

}

.form-label {
    color: green;
}
</style>
