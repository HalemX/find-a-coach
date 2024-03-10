<template>
  <div>
    <section>
      <base-card>
        <header>
          <h2>{{ fullName }}</h2>
          <h3>${{ selectCoach.hourlyRate }}/hour</h3>
        </header>
      </base-card>
    </section>
    <section>
      <base-card>
        <header>
          <h2>Interested? Reach out now!</h2>
          <base-button link :to="contactLink">Contact</base-button>
        </header>
        <router-view></router-view>
      </base-card>
    </section>
    <section>
      <base-card>
        <base-badge
          v-for="area in selectCoach.areas"
          :key="area"
          :title="area"
          :type="area"
        ></base-badge>
        <p>{{ selectCoach.description }}</p>
      </base-card>
    </section>
  </div>
</template>
<script>
export default {
  props: ["id"],
  data() {
    return {
      selectCoach: null,
    };
  },
  created() {
    this.selectCoach = this.$store.getters["coaches/coaches"].find(
      (coach) => coach.id === this.id
    );
  },
  computed: {
    fullName() {
      return `${this.selectCoach.firstName} ${this.selectCoach.lastName}`;
    },
    contactLink() {
      return `${this.id}/contact`;
    },
  },
};
</script>
