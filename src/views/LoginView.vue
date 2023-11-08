<template>
    <div class="home">
        <a-form name="basic" :label-col="{ span: 8 }" :wrapper-col="{ span: 16 }" autocomplete="off" @finish="onFinish"
            @finishFailed="onFinishFailed">
            <a-form-item label="Username" name="username"
                :rules="[{ required: true, message: 'Please input your username!' }]">
                <a-input v-model:value="formState.username" />
            </a-form-item>

            <a-form-item label="Password" name="password"
                :rules="[{ required: true, message: 'Please input your password!' }]">
                <a-input-password v-model:value="formState.password" />
            </a-form-item>

            <a-form-item name="remember" :wrapper-col="{ offset: 8, span: 16 }">
                <a-checkbox v-model:checked="formState.remember">Remember me</a-checkbox>
            </a-form-item>

            <a-form-item :wrapper-col="{ offset: 8, span: 16 }">
                <a-button type="primary" html-type="submit">Submit</a-button>
            </a-form-item>
        </a-form>

    </div>
</template>
  
<script lang="ts">
import { defineComponent,reactive  } from 'vue';


export default defineComponent({
    name: 'HomeView',
    setup() {
        interface FormState {
            username: string;
            password: string;
            remember: boolean;
        }

        const formState = reactive<FormState>({
            username: '',
            password: '',
            remember: true,
        });
        const onFinish = (values: any) => {
            console.log('Success:', values);
        };

        const onFinishFailed = (errorInfo: any) => {
            console.log('Failed:', errorInfo);
        };

        return {
            formState,
            onFinish,
            onFinishFailed
        }
    }
});
</script>

<style scoped>
.home {
    height: 100%;
    /* 设置背景图片 */
    background-image: url('../../public/image/1.jpg');
    /* 设置背景图片不重复 */
    background-repeat: no-repeat;
    /* 设置背景图片的位置 */
    background-position: center;
    /* 设置背景图片的大小 */
    background-size: cover;
    /* 设置背景图片的平铺方式 */
    background-attachment: fixed;

    display: flex;
    justify-content: center;
            align-items: center;
}

.home img {
    width: 100%;
    height: 100%;
}
</style>
  