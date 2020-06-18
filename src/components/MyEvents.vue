<template>
    <div class="group pubsub">
        <div class="half left">
            <h2>Publish</h2>
            <button 
              class="half left" 
              id="send-evnet" 
              @click="handleClick()"
            >
              Send test-event with
            </button>
            <input 
              type="text"
              class="half"
              id="event-data"
              v-model="value"
            />
        </div>
        <div class="half">
            <h2>Subscribe</h2>
            <ul id="events-received">
                <div v-for="event in eventsReceived" :key="event.id">
                    <li>{{event}}</li>
                </div>
            </ul>
        </div>
    </div>
</template>
<script>
export default {
    name: 'my-events',
    props: ["ds"],
    data() {
        return {
            eventsReceived: [],
            value: ""
        };
    },
    created() {
        this.event = this.ds.event;
        this.event.subscribe("test-event", value => {
            this.eventsReceived.push(value);
        });
    },
    methods: {
        handleClick() {
            this.event.emit("test-event", this.value);
        }
    }
};
</script>