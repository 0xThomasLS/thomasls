<template>
  <div class="social-links">
    <ul>
      <li v-for="social in links" :key="JSON.stringify(social)">
        <a class="btn f-w" :href="social.link">
          <img
            v-if="social.icon"
            :src="require(`@/assets/icons/${social.icon}.png`)"
            :alt="`Social icon for ${social.icon}`"
          />
          {{ social.name }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SocialLinks",
  props: {
    links: {
      type: Array,
      require: true,
    },
  },
};
</script>
