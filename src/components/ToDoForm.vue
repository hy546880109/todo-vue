<template>
    <form @submit.prevent="onSubmit">
        <label for="new-todo-input" class="label__lg">你需要添加的任务? </label>
        <input type="text" id="new-todo-input" name="new-todo" ref="textInput" autocomplete="off" v-model.trim.lazy="label"
            class="input__lg" />
        <button type="submit" class="btn btn__primary btn__lg">添加</button>
    </form>
</template>

<script>
export default {
    methods: {
        onSubmit() {
            if (this.label === '') {
                return;
            }
            this.$emit("todo-added", this.label);   ////监听事件并传递参数
            this.label = "";
        },
    },
    data() {
        return {
            label: "",
        };
    },
    mounted(){
        const textInputRef = this.$refs.textInput
        textInputRef.focus()    ////添加焦点
    }
};
</script>