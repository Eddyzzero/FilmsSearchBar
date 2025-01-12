<template>
    
    <div>
        <input
        class="rounded-lg px-6 py-1 bg-sky-600/50 text-white"
        type="text"
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value )"
            placeholder="Rechercher..."
        />
    </div>

</template>

<script>
export default {
    props: {
        modelValue: {
            type: String,
            required: true, 
        }
    }
}


</script>