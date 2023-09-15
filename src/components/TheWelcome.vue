<script>
export default {
  data() {
    return {
      questions: [
        {
          question: "What is the capital of France?",
          options: ["Paris", "London", "Berlin", "Madrid"],
          correctAnswer: "Paris",
        },
        {
          question: "What is 2 + 2?",
          options: ["3", "4", "5", "6"],
          correctAnswer: "4",
        },
        {
          question: "What is the chemical symbol for the element gold",
          options: ["SL", "Au", "UK", "USA"],
          correctAnswer: "Au",
        },
        {
          question: "Who was the first President of the United States?",
          options: [
            "Andrew Jackson",
            "John Quincy Adams",
            "John Adams",
            "George Washington",
          ],
          correctAnswer: "George Washington",
        },
        {
          question: "Who wrote the novel 'To Kill a Mockingbird'?",
          options: [
            "Andrew Jackson",
            "Harper Lee",
            "John Adams",
            "George Washington",
          ],
          correctAnswer: "Harper Lee",
        },
        {
          question: "In which sport would you perform a slam dunk?",
          options: ["Basketball", "Cricket", "BaseBall", "NetBall"],
          correctAnswer: "Basketball",
        },
        {
          question: "Who is known as the 'King of Pop'?",
          options: [
            "Elvis Presley",
            "James Brown",
            "Michael Jackson",
            "Freddie Mercury",
          ],
          correctAnswer: "Michael Jackson",
        },
        {
          question: "What is the largest planet in our solar system?",
          options: ["Mars", "Jupiter", "Venus", "Saturn"],
          correctAnswer: "Jupiter",
        },
        {
          question: "Who directed the film 'Jurassic Park'?",
          options: [
            "Martin Scorsese",
            "Francis Ford Coppola",
            "Alfred Hitchcock",
            "Steven Spielberg",
          ],
          correctAnswer: "Steven Spielberg",
        },
        {
          question:
            "Which band is known for their hit song 'Bohemian Rhapsody'?",
          options: ["Elvis Presley", "James Brown", "Michael Jackson", "Queen"],
          correctAnswer: "Michael Jackson",
        },
      ],
      currentQuestionIndex: 0,
      score: 0,
      showResult: false,
    };
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionIndex];
    },
  },
  methods: {
    checkAnswer(index) {
      if (
        this.currentQuestion.options[index] ===
        this.currentQuestion.correctAnswer
      ) {
        this.score++;
      }
      if (this.currentQuestionIndex < this.questions.length - 1) {
        this.currentQuestionIndex++;
      } else {
        this.showResult = true;
      }
    },
  },
};
</script>

<template>
  <div class="topic">
    <p>Quize App</p>
  </div>
  <div class="quiz-container">
    <div v-if="!showResult" class="question-card">
      <h1 class="question">{{ currentQuestion.question }}</h1>
      <ul class="options">
        <li
          v-for="(option, index) in currentQuestion.options"
          :key="index"
          @click="checkAnswer(index)"
          class="option"
        >
          {{ option }}
        </li>
      </ul>
    </div>
    <div v-else class="result-card">
      <h2 class="result-title">Quiz Result</h2>
      <p class="result-text">
        You scored {{ score }} out of {{ questions.length }}
      </p>
    </div>
  </div>
</template>

<style scoped>
.quiz-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: auto;
  background-color: #f4f4f4;
}

.topic {
  display: flex;
  justify-content: center;
  padding: 20px;
  font-size: 40px;
  font-weight: 700;
  text-decoration: underline;
}

.question-card,
.result-card {
  background-color: #fff;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  width: 400px;
  text-align: center;
}

.question {
  font-size: 24px;
  margin-bottom: 20px;
}

.options {
  list-style: none;
  padding: 0;
}

.option {
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  cursor: pointer;
}

.option:hover {
  background-color: #f0f0f0;
}

.result-title {
  font-size: 24px;
  margin-bottom: 10px;
}

.result-text {
  font-size: 18px;
}
</style>
