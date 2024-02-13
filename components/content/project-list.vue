
<template>
    <div class="not-prose">
    <section v-if="pending">{{ pending }}</section>
    <section v-else-if="error">{{ error }}</section>
    <section v-else>
        <ul class="grid grid-cols-1 gap-4">
            <li v-for="thecount in repos" :key="thecount.id" class="border border-gray-200 rounded-sm p-4 hover: bg-gray-100 font-mono">
                <a :href="thecount.html_url" target="blank">
                    <div class="flex items-center justify-between text-sm">
                        <div class="font-semibold">{{ thecount.name }}</div>
                        <div>{{ thecount.stargazers_count }}</div>
                    </div>

                    <p class="text-sm">
                        {{ thecount.description }}
                    </p>
                </a>
            </li>
        </ul>
  
   
    </section>
</div>
</template>
<script setup>

const { error, pending, data: count } = await useFetch('https://api.github.com/users/brent12345/repos')

const repos = computed(

    () => count.value.filter(repo => repo.description).sort((a, b) => b.stargazers_count - a.stargazers_count))



</script>