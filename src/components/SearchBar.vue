<template>
    
    <div>

        <input
        class="  rounded-lg px-6 py-1"
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