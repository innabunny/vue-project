<template>
  <h1 class="title">Как уютно встретить Новый год</h1>
  <div class="post" v-for="post in posts" v-bind:key="post.id">
    <div class="post__title">{{ post.title }}</div>
    <div class="post__subtitle">
      {{ post.subtitle }}
    </div>
  </div>
  <form class="form" @submit.prevent>
    <input
      class="form__input"
      type="text"
      placeholder="Введите название"
      v-bind:value="inputTitle"
      @input="inputTitle = $event.target.value"
    />
    <input
      class="form__input"
      type="text"
      placeholder="Введите описание"
      v-bind:value="inputSubtitle"
      @input="inputSubtitle = $event.target.value"
    />
    <button class="form__btn" @click="createPost">Создать</button>
  </form>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      posts: [
        {
          id: 1,
          title: "1. Устроить кукольный театр или театр теней",

          subtitle: `Соорудить ширму можно при помощи обыкновенного одеяла или простыни. Для кукольного театра подойдут 
           небольшие мягкие игрушки, а для театра теней нужно вырезать силуэты из бумаги. Лампа, помещённая за ширмой, завершит 
            нехитрую конструкцию. Малыши будут в восторге, а взрослые смогут снова окунуться в детство.`,
        },
        {
          id: 2,
          title: "2. Организовать домашний маскарад",

          subtitle: `Карнавальные костюмы пригодятся не только для детских утренников. Раскрасьте лица, 
          наденьте маски, создайте свой образ из подручных материалов... и попробуйте угадать, кто кем нарядился.`,
        },
        {
          id: 3,
          title: "3. Подготовить новогоднее обращение",

          subtitle: `Кто сказал, что новогоднее обращение может быть только у президента?
           Вашим близким тоже наверняка есть что сказать. Пусть каждый из тех, кто с вами рядом, подготовит пятиминутную речь и выступит перед собравшимися.`,
        },
        {
          id: 4,
          title: "4. Погадать на будущий год",

          subtitle: `Способов масса: испечь китайские печенья с предсказаниями, погадать на картах, на кофейной гуще, на воске. 
          Воспринимать знаки судьбы можно и серьёзно, и несерьёзно. Главное — трактовать их в положительном ключе и надеяться на лучшее.`,
        },
        {
          id: 5,
          title: "5. Заложить новогоднюю традицию",

          subtitle: `Герой фильма «Ирония судьбы» каждое 31 декабря ходил с друзьями в баню. Если у вас нет новогодней традиции, самое время 
          её придумать. Вспомните, какие занятия дарили вам радость в детстве, или подсмотрите идеи у других читателей Лайфхакера.`,
        },
      ],

      inputTitle: "",
      inputSubtitle: "",
    };
  },
  methods: {
    onChangeTitle(event) {
      this.inputTitle = event.target.value;
      console.log(event);
    },
    onChangeSubtitle(event) {
      this.inputSubtitle = event.target.value;
      console.log(event);
    },
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.inputTitle,
        subtitle: this.inputSubtitle,
      };

      this.posts.push(newPost);
      this.inputSubtitle = "";
      this.inputTitle = "";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0;
  padding: 0;
  box-sizing: border-box;

  font-family: "Nunito", sans-serif;
  font-optical-sizing: auto;
  font-style: normal;
  background-image: linear-gradient(90deg, #b8889b 11%, #68a5ed 94%);
  max-width: 100vw;
  height: 100%;
}

.title {
  text-align: center;
  text-transform: uppercase;
  font-size: 2rem;
  font-family: "Nunito", sans-serif;
  padding-top: 2rem;
}
.post {
  margin: 1rem;
  border: 0.1rem solid lightblue;
}

.post__title {
  font-size: 2rem;
  font-weight: 500;
}

.post__subtitle {
  font-size: 1.5rem;
}
.form {
  padding-top: 1rem;
  margin: 0 auto;
  width: 50vw;
  height: 150px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}

.form__input {
  background-color: transparent;
  width: 100%;
  height: 100%;
  border: none;
  border-bottom: 1px solid lightblue;
  font-size: 1rem;
  margin-bottom: 1rem;
}

.form__btn {
  width: 100%;
  height: 100%;
  border-radius: 1px;
  background-color: transparent;
  border: 1px solid lightblue;
  font-size: 1.5rem;
  text-transform: uppercase;
  padding: 0.6rem;
}

.form__btn:hover {
  cursor: pointer;
  transition: all ease-in 1ms;
  opacity: 0.7;
}
</style>
