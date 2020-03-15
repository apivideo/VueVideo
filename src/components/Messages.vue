<template>
        <div>
            <h4>Messages</h4>
            <ul>
                <li v-for="message in messages">{{message}}</li>            
            </ul>
        </div>
</template>

<script>
export default {
    data(){
        return {
            messages: ["Hello", "Hi", "working"]
        };
    }
};
</script>