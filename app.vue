<template>
  <div class="text-center pt-20" style="font-size: 360px;">
    {{ current_word.char }}
  </div>
  <div class="h-48">
    <div class="text-6xl text-center px-48" v-if="revealed">
      <div class="flex items-center justify-center gap-4">
        <div class="w-32" v-for="char in pinyin(current_word.word).split(' ')">{{ char }}</div>
      </div>
      <div class="flex items-center justify-center gap-4">
      <div class="w-32" v-for="char in current_word.word" :class="char == current_word.char ? 'text-blue-500' : ''">{{ char }}</div>
    </div>
  </div>
  </div>

  <div class="flex items-center justify-center gap-4">
    <button @click="prev" class="text-4xl transform hover:scale-125">◀️</button>
    <button @click="revealed = !revealed" class="text-4xl" :class="revealed?'':'hover:animate-bounce'">{{revealed?'⛔️':'💡'}}</button>
    <button @click="next" class="text-4xl transform hover:scale-125">▶️</button>
  </div>
  <div class="flex items-center justify-center gap-4">
  {{ currentIndx + 1 }}/{{ words.length }}
</div>

</template>

<script setup>
import { pinyin } from 'pinyin-pro';

const words = [
  { char: "肓", word: "病入膏肓" },
  { char: "妁", word: "媒妁之言" },
  { char: "倜", word: "风流倜傥" },
  { char: "圳", word: "深圳" },
  { char: "莞", word: "东莞" },
  { char: "菅", word: "草菅人命" },
  { char: "叱", word: "叱咤风云" },
  { char: "蜃", word: "海市蜃楼" },
  { char: "靥", word: "笑靥如花" },
  { char: "啬", word: "吝啬" },
  { char: "侈", word: "奢侈" },
  { char: "杳", word: "杳无音信" },
  { char: "沓", word: "拖沓" },
  { char: "邋", word: "邋遢" },
  { char: "魑", word: "魑魅魍魉" },
  { char: "饬", word: "捯饬" },
  { char: "尥", word: "尥蹶子" },
  { char: "孓", word: "孑孓" },
  { char: "亍", word: "彳亍" },
  { char: "茕", word: "茕茕孑立" },
  { char: "贻", word: "贻笑大方" },
  { char: "鹄", word: "鸿鹄之志" },
  { char: "砼", word: "砼梁" },
  { char: "栩", word: "栩栩如生" },
  { char: "矍", word: "精神矍铄" },
  { char: "叵", word: "居心叵测" },
  { char: "臬", word: "奉为圭臬" },
  { char: "醍", word: "醍醐灌顶" },
  { char: "郴", word: "郴州" },
  { char: "栉", word: "鳞次栉比" },
  { char: "旯", word: "旮旯" },
  { char: "鳏", word: "鳏寡" },
  { char: "渑", word: "渑池" },
  { char: "歙", word: "歙县" },
  { char: "甪", word: "甪直" },
  { char: "涪", word: "涪陵" },
  { char: "眙", word: "盱眙" },
  { char: "邛", word: "邛崃" },
  { char: "罘", word: "芝罘" },
  { char: "厝", word: "曾厝垵" },
  { char: "蒯", word: "蒯" },
  { char: "阚", word: "阚" },
  { char: "厍", word: "厍" },
  { char: "夔", word: "夔" },
  { char: "殳", word: "殳" },
  { char: "郏", word: "郏" },
  { char: "宓", word: "宓" },
  { char: "爨", word: "爨" },
]

words.sort(() => Math.random() - 0.5)

const currentIndx = ref(0)
const current_word = computed(() => words[currentIndx.value])
const revealed = ref(false)
const next = () => {
  currentIndx.value = (currentIndx.value + 1) % words.length
  revealed.value = false
}
const prev = () => {
  currentIndx.value = (currentIndx.value - 1 + words.length) % words.length
  revealed.value = false
}
</script>