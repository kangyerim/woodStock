<template>
<div>
    <div style="margin: 0 auto; width: 50%">
    <v-form>
        <table class="login_input">
            <tr><v-col cols="12" md="4" >
                <v-text-field
                        class="justify-center"
                        v-model=userId
                        :rules="idRules"
                        :counter="10"
                        label="아이디"
                        required
                ></v-text-field>
            </v-col></tr>
            <tr><v-col
                    cols="12"
                    md="4"
            >
                <v-text-field
                        v-model=password
                        type="password"
                        :rules="passRules"
                        :counter="10"
                        label="패스워드"
                        required
                ></v-text-field>
            </v-col></tr>
            <tr><v-col cols="12"
                       md="4">
                <v-text-field
                        v-model=userName
                        :rules="nameRules"
                        :counter="10"
                        label="이름"
                        required
                ></v-text-field>
            </v-col></tr>
            <tr><v-col
                    cols="12"
                    md="4"
            >
                <v-text-field
                        v-model=address
                        :rules="addressRule"
                        :counter="20"
                        label="주소"
                        required
                ></v-text-field>
            </v-col></tr>
        </table>
    </v-form>
    </div>

    <div style="margin: 0 auto; width: 30%">
    <v-btn @click="reset">돌아가기</v-btn>
        <span style="padding-right: 30px"></span>
    <v-btn @click="submission">제출하기</v-btn>
    </div>

</div>
</template>

<script>
    export default {
        data: () => ({
            valid: false,
            userId: '',
            idRules : [
                v => !!v || 'userId is required',
                v => v.length <= 10 || 'userId must be less than 10 characters',
            ],
            password: '',
            passRules: [
                v => !!v || 'password is required',
                v => v.length <= 10 || 'password must be less than 10 characters',
            ],
            userName: '',
            nameRules: [
                v => !!v || 'name is required',
                v => /.+@.+/.test(v) || 'E-mail must be valid',
            ],
            address: '',
            addressRule: [
                v => !!v || 'address is required',
                v => /.+@.+/.test(v) || 'address must be valid',
            ],
        }),
        methods: {
            submission() {
                this.$store.dispatch('member/submission',{userName : this.userName, password : this.password, userId : this.userId, email : this.email})
            },
            reset() {
                this.password = ''
                this.userId = ''
            },
        }
    }
</script>

<style scoped>
    .buttons{
        text-align: center;
    }
    .login_input{
        width: 1200px;
        color: #ffffff;
        text-align: center;
        margin: 0 auto;
    }
</style>