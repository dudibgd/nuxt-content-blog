<template>
  <article>
    <nav>
        <ul>
            <li v-for="link of article.toc" :key="link.id">
            <NuxtLink 
                :to="`#${link.id}`"
                :class="{ 'ml-1 py-2': link.depth === 2, 'ml-4 pb-2': link.depth === 3 }"
                >{{ link.text }}</NuxtLink>
            </li>
        </ul>
    </nav>
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <img :src="article.img" :alt="article.alt" />
    <p>Article last updated: {{ formatDate(article.updatedAt) }}</p>

    <nuxt-content :document="article" />

    <author :author="article.author" />

    <AppSearchInput />

    <prev-next :prev="prev" :next="next" />
  </article>
</template>

<script>
export default {

    async asyncData({ $content, params }) {
       const article = await $content('articles', params.slug).fetch()

       const [prev, next] = await $content('articles')
        .only(['title', 'slug'])
        .sortBy('createdAt', 'asc')
        .surround(params.slug)
        .fetch()

      return { article, prev, next }
    },
    methods: {
        formatDate(date) {
            const options = { year: 'numeric', month: 'long', day: 'numeric' }
            return new Date(date).toLocaleDateString('en', options)
        }
 }


}
</script>

<style>
.nuxt-content h2 {
    font-weight: bold;
    font-size: 28px;
}
.nuxt-content h3 {
    font-weight: bold;
    font-size: 22px;
}
.nuxt-content p {
    margin-bottom: 20px;
    color: rgb(184, 27, 87);
}

.icon.icon-link {
    background-image: url('~assets/svg/icon-key.svg');
    display: inline-block;
    width: 20px;
    height: 20px;
    background-size: 20px 20px;
}
</style>