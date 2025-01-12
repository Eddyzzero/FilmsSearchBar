<template>
    <li> {{ content }}</li>
</template>

<script>
export default {
    props: {
        content: {
            Type: String,
            required: true,
        }
    }
}
</script>