<template>
  <div class="events">
    <h1>Events For Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event"/>
  </div>
</template>

<script>
import EventService from "@/services/EventService.js";
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";

export default {
  name: "EventList",
  components: {
    EventCard,
  },

  data() {
    return {
      events: null
    }
  },
  created() {
    EventService.getEvents()
    .then(response => this.events = response.data)
    .catch(errors => console.log(errors))
  }
};
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>