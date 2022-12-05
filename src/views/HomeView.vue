<script setup lang="ts">
import { onBeforeMount, ref, type Ref } from "vue";

interface QuoteData {
  content: string;
  author: string;
}

const quote: Ref<QuoteData> = ref({
  content: "",
  author: "Author name",
});
onBeforeMount(async () => {
  quote.value = await fetch("https://api.quotable.io/random").then((r) =>
    r.json()
  );
});
</script>

<template>
  <div dark:text-white container mx-auto>
    <div flex flex-row gap-5>
      <div class="basis-3/4">
        <div block rounded-lg shadow-lg bg-white w-full>
          <div py-3 px-6 border-b border-gray-300 text-center font-semibold>
            Notices
          </div>
          <div p-6>123</div>
        </div>
      </div>
      <div class="basis-1/4">
        <div grid gap-4>
          <div>
            <div block rounded-lg shadow-lg bg-white w-full min-h-3>
              <div py-3 px-6 border-b border-gray-300 text-center font-semibold>
                {{ quote.author }}
              </div>
              <div p-6 text-center>{{ quote.content }}</div>
            </div>
          </div>
          <div>
            <div block rounded-lg shadow-lg bg-white w-full min-h-xl>
              <div py-3 px-6 border-b border-gray-300 text-center font-semibold>
                Ranking
              </div>
              <div p-6>123</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
