<template>
  <div class="page">
    <div class="container">
      <h2>Word Scramble</h2>

      <div class="content">
        <p class="word">{{ scrambledWord }}</p>

        <div class="details">
          <p class="hint">
            Hint: <span>{{ wordHint }}</span>
          </p>

          <p class="time">
            Time Left:
            <span
              ><b>{{ timeLeft }}</b
              >s</span
            >
          </p>
        </div>

        <input
          v-model="inputText"
          type="text"
          spellcheck="false"
          placeholder="Enter a valid word"
          :maxlength="correctWord.length"
        />
        <div class="buttons">
          <button type="button" class="refresh-word" @click="refreshWord">
            Refresh Word
          </button>

          <button type="button" class="check-word" @click="checkWord">
            Check Word
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const words = [
  { word: "addition", hint: "The process of adding numbers" },
  { word: "meeting", hint: "Event in which people come together" },
  { word: "number", hint: "Math symbol used for counting" },
  { word: "exchange", hint: "The act of trading" },
  { word: "canvas", hint: "Piece of fabric for oil painting" },
  { word: "garden", hint: "Space for planting flowers and plants" },
  { word: "position", hint: "Location of someone or something" },
  { word: "feather", hint: "Hair-like outer covering of birds" },
  { word: "comfort", hint: "A pleasant feeling of relaxation" },
  { word: "tongue", hint: "The muscular organ of the mouth" },
  { word: "expansion", hint: "The process of increase or growth" },
  { word: "country", hint: "A politically identified region" },
  { word: "group", hint: "A number of objects or persons" },
  { word: "taste", hint: "Ability of the tongue to detect flavor" },
  { word: "store", hint: "Large shop where goods are traded" },
  { word: "field", hint: "Area of land for farming activities" },
  { word: "friend", hint: "Person other than a family member" },
  { word: "pocket", hint: "A bag for carrying small items" },
  { word: "needle", hint: "A thin and sharp metal pin" },
  { word: "expert", hint: "Person with extensive knowledge" },
  { word: "statement", hint: "A declaration of something" },
  { word: "second", hint: "One-sixtieth of a minute" },
  { word: "library", hint: "Place containing a collection of books" },
];

const scrambledWord = ref("");
const wordHint = ref("");
const timeLeft = ref(30);
const inputText = ref("");
const correctWord = ref("");
let timer = null;

// 타이머 시작
const startTimer = () => {
  clearInterval(timer);

  timer = setInterval(() => {
    if (timeLeft.value > 0) {
      timeLeft.value--;
    } else { // 시간이 다 되었을 경우
      alert(`시간초과! 정답은 ${correctWord.value.toUpperCase()} 였습니다`);
      refreshWord();
    }
  }, 1000);
};

// 새로운 단어로 갱신
const refreshWord = () => {
  timeLeft.value = 30;

  // 랜던으로 단어 및 힌트 선택
  const { word, hint } = words[Math.floor(Math.random() * words.length)];

  // 단어 랜덤으로 섞기
  scrambledWord.value = shuffleWord(word);
  wordHint.value = hint;
  correctWord.value = word.toLowerCase();
  inputText.value = "";
  
  startTimer();
};

// 단어를 랜덤으로 섞기
const shuffleWord = (word) => {
  return word.split("").sort(() => Math.random() - 0.5).join("");
}

// 입력한 단어 검사
const checkWord = () => {
  const userWord = inputText.value.toLowerCase();

  // 빈 칸일 경우
  if (!userWord) {
    return alert("단어를 입력해 주세요.");
  }

  // 정답이 틀릴 경우
  if (userWord !== correctWord.value) {
    return alert(`틀렸습니다! ${userWord} 정답이 아닙니다`);
  }

  // 정답일 경우
  alert(`ㅊㅊㅊ! ${correctWord.value.toUpperCase()} <--- 요고시 정답`);

  refreshWord();
};

onMounted(() => {
  refreshWord();
});

// 페이지를 떠날 때 타이머 정리
onBeforeUnmount(() => {
  clearInterval(timer);
});
</script>

<style lang="scss" scoped>
@use "@/assets/scss/pages/20241122/assignment4.scss" as assignment4;
</style>
