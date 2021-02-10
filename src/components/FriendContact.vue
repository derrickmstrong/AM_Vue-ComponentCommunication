<template>
  <li>
    <h2>{{ name }} {{ isFriendFavorite === "1" ? "(Favorite)" : "" }}</h2>
    <button @click="toggleFavorite">Toggle Friend</button>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  // props should always be camelCase
  // props: ["name", "phoneNumber", "emailAddress", "isFavorite"],
  // You can provide a type and an object of the props
  props: {
    name: {
      type: String,
      required: true,
    },
    phoneNumber:  {
      type: String,
      required: true,
    },
    emailAddress:  {
      type: String,
      required: true,
    },
    isFavorite:  {
      type: String,
      required: false,
      // default can also be a function
      default: '0',
      // validator allows you to run a function to validate if valid values are assigned to the key
      validator: function(value) {
        return value === '1' || value === '0';
      }
    },
  },
  data() {
    return {
      detailsAreVisible: false,
      isFriendFavorite: this.isFavorite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      if (this.isFriendFavorite === "1") {
        return (this.isFriendFavorite = "0");
      } else {
        return (this.isFriendFavorite = "1");
      }
    },
  },
};
</script>
