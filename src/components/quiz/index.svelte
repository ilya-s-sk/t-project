<script>
  import Section from "../atoms/section/index.svelte";
  import Title from "../atoms/title/index.svelte";
  import ArrowIcon from "../atoms/arrow/index.svelte";
  import style from "./style.pcss";

  let isQuizStarted = true;
  let step = 0;
  let score = 0;

  let hasAnswer = false;
  let choosenAnswerIndex = null;

  const quizContent = [
    {
      question: "Наиболее значимый орган кабана обыкновенного",
      answers: [
        {
          text: "Уши",
          comment: "Вряд ли он может ими как-то похвастаться",
          correct: false,
        },
        {
          text: "Хвост",
          comment: "Кого-то правда интересует кабаний хвост?",
          correct: false,
        },
        {
          text: "Писька",
          comment: "Неподражаемая пиьска кабана!",
          correct: true,
        },
      ],
    },
    {
      question: "Для чего нужны цветные карандаши?",
      answers: [
        {
          text: "Рисовать",
          comment: "Как-то это несерьёзно",
          correct: false,
        },
        {
          text: "В попу",
          comment: "Идеальное совпадение",
          correct: true,
        },
        {
          text: "Строить цветные шалаши",
          comment: "Мы тут вообще-то о серьёзных вещах говорим",
          correct: false,
        },
      ],
    },
    {
      question: "Что произошло с Гослингом в конце Драйва?",
      answers: [
        {
          text: "Он выжил",
          comment: "Всё точно так и было",
          correct: true,
        },
        {
          text: "Он не умер",
          comment: "А как могло быть иначе?",
          correct: true,
        },
        {
          text: "Остался жив",
          comment: "И слава богу!",
          correct: true,
        },
      ],
    },
    {
      question: "Когда хочется побаловаться, хочется и...",
      answers: [
        {
          text: "Поприкалываться",
          comment: "Не каждый день такое настроение",
          correct: true,
        },
        {
          text: "Покуролесить",
          comment: "Да, но нет",
          correct: false,
        },
        {
          text: "Порезвиться",
          comment: "Это уже давай при иных обстоятельствах",
          correct: false,
        },
      ],
    },
  ];

  $: currentQuestion = quizContent[step];
  $: currentText = currentQuestion.answers[choosenAnswerIndex]
    ? currentQuestion.answers[choosenAnswerIndex].comment
    : currentQuestion.question;

  function handleInput(isCorrect, order) {
    hasAnswer = true;
    choosenAnswerIndex = order;
    if (isCorrect) {
      score += 1;
    }
  }

  function nextQuestion() {
    hasAnswer = false;
    choosenAnswerIndex = null;
    if (step === quizContent.length - 1) {
      
    } else {
      step += 1;
    }
  }
</script>

<Section class={style.root}>
  <Title class={style.title} count={4} content="Таня очень весёлая!" />
  <p class={style.text}>А тут тест с главными приколами</p>
  <div class={style.quiz}>
    {#if isQuizStarted}
      <p class={style.question}>{currentText}</p>
      <div class={style.optionsList}>
        {#each currentQuestion.answers as { text, correct }, index}
          <label
            class={`${style.option} ${
              index === choosenAnswerIndex
                ? style[`option_${correct ? "correct" : "incorrect"}`]
                : ""
            }`}
          >
            <input
              type="radio"
              name={currentQuestion.question}
              checked={index === choosenAnswerIndex}
              disabled={hasAnswer}
              on:input={() => {handleInput(correct, index)}}
            />
            <span>{text}</span>
          </label>
        {/each}
      </div>
      <button
        class={`${style.nextButton} ${!hasAnswer ? style.nonVisible : ""}`}
        title="Дальше"
        disabled={!hasAnswer}
        on:click={nextQuestion}
      ><ArrowIcon /></button>
    {:else}
      <button
        class={style.button}
        on:click={() => {
          isQuizStarted = true;
        }}>Запустить тест</button
      >
    {/if}
  </div>
</Section>
