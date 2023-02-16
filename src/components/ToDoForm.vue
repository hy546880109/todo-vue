<template>
    <form @submit.prevent="onSubmit">
        <label for="new-todo-input" class="label__lg">你需要添加的任务? </label>
        <input type="text" id="new-todo-input" name="new-todo" autocomplete="off" v-model.trim.lazy="label"
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
            console.log('label: ', this.label);
            this.$emit("todo-added", this.label);
            this.label = "";
        },
    },
    data() {
        return {
            label: "",
        };
    },
};
</script>