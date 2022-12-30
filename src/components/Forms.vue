<template>
    <div class="Sign-up-form">
        <form @submit.prevent="AddBtn">
            <div class="form-floating mb-4">
            <input v-model="email" type="email" class="form-control" id="floatingInput" placeholder="name@example.com">
            <label for="floatingInput">Email address</label>
        </div>
        <div class="form-floating mb-4">
            <input v-model="password" type="password" class="form-control" id="floatingPassword" placeholder="Password">
            <label for="floatingPassword">Password</label>
            <p class="error-text">{{ error }}</p>
        </div>
        <div>
            <select v-model="job" class="form-select mb-4">
                <option value="Developer">Web Developer</option>
                <option value="Desinger">Web Designer</option>
            </select>
        </div>
        <div class="form-floating mb-4">
            <input v-model="Skill" @keyup="keyup" type="text" class="form-control" id="floatingInput" placeholder="name@example.com">
            <label for="floatingInput">Skill</label>
        </div>
        <div v-for="Skill in Skills">
            <p class="text-white">{{ Skill }} <span @click="deleteCross(Skill)" class="cross-sign">&#10006;</span></p>
        </div>
        <!-- Check -->
        <div class="d-flex justify-content-between text-white">
            <div class="form-check">
                <input v-model="fav" class="form-check-input" type="checkbox" value="lalisa" id="flexCheckDefault">
                <label class="form-check-label" for="flexCheckDefault">
                    Lalisa
                </label>
            </div>
            <div class="form-check">
                <input v-model="fav" class="form-check-input" type="checkbox" value="jennie" id="flexCheckDefault">
                <label class="form-check-label" for="flexCheckDefault">
                    Jennie
                </label>
            </div>
            <div class="form-check">
                <input v-model="fav" class="form-check-input" type="checkbox" value="Rose" id="flexCheckDefault">
                <label class="form-check-label" for="flexCheckDefault">
                    Rose
                </label>
            </div>
            <div class="form-check">
                <input v-model="fav" class="form-check-input" type="checkbox" value="jisoo" id="flexCheckDefault">
                <label class="form-check-label" for="flexCheckDefault">
                    Jisoo
                </label>
            </div>
        </div>

        <div class="text-center mt-4">
            <button class="btn btn-primary">Create Account</button>
        </div>
        </form>
    </div>
    <div class="text-center">
        <p>Email : {{ email }}</p>
        <p>Password : {{ password }}</p>
        <p>Job : {{ job }}</p>
        <p>Idols : {{ fav }}</p>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                email: '',
                password : '',
                job : 'Developer',
                fav : [],
                Skill : '',
                Skills : [],
                error : '',
                none : '',
            }
        },
        methods: {
            keyup(e) {
                if(e.key === ' '){
                    this.Skills.push(this.Skill);
                    this.Skill = '';
                }
            },
            deleteCross(deleteSkill){
                this.Skills = this.Skills.filter(skill => deleteSkill !== skill)
            },
            AddBtn() {
                if(this.password.length < 8){
                    this.error = 'Password must be at least 8 characters';
                }
            }
        },
    }
</script>

<style scoped>
.Sign-up-form{
  width: 400px;
  margin: 50px auto;
  background-color: #918e8e;
  padding: 40px;
  border-radius: 10px;
}

.cross-sign{
    color: crimson;
    cursor: pointer;
}

.error-text{
    color: crimson;
    font-weight: bold;
}
</style>