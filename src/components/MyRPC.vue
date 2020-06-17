<template>
    <div class="group reqres">
        <div class="half left">
            <h2>Request</h2>
            <button
                class="half left"
                @click="handleClick()"
            >
                Make multiply request
            </button>
            <div class="half">
                <input 
                  type="text"
                  v-model="requestValue"
                  class="half left"
                />
                <span 
                  class="response half item"
                >
                  {{displayResponse}}
                </span>
            </div>
        </div>
        <div class="half">
                <h2>Response</h2>
                <div class="half left item">Multiply number with:</div>
                <input 
                  type="text"
                  class="half"
                  v-model="responseValue"
                />
        </div>
    </div>
</template>
<script>
export default {
    name: 'my-rpc',
}
</script>