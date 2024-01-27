<template>
    <div class="backdrop" @click.self ="closeModal">
        <div class="modal" :class="{dark_color: theme === 'dark'}">
            <h1>text from modal</h1>
            <p>paragraph - {{header}}</p>
            <slot></slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>

export default{
    props: ['header','theme'],
    methods: {
        closeModal(){
            this.$emit('close');
        }
    }
}

</script>


<style scoped>
.backdrop{
    top: 0;left: 0;
    width: 100%;
    height: 100%;
    background: #00000080;
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
}
.modal{
    background: #fff;
    width: 400px;
    border-radius: 10px;
    padding: 20px 50px;
}
h1{color: red;}
.dark_color{color: green;}
</style>