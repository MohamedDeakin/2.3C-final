<template>

  <a href="#/">Home</a> |
  <a href="#/about">About</a> |
  <a href="#/non-existent-path">Broken Link</a>
  <component :is="currentView" />

  <!-- Task 1a - Text Interpolation -->
  <div class="task task1a">
    <span>Task 1a: Text Interpolation - Message: {{ msg }}</span>
  </div>

  <!-- Task 1b - Raw HTML -->
  <div class="task task1b">
    <p>Task 1b: Raw HTML</p>
    <p>Using text interpolation: {{ rawHtml }}</p>
    <p>Using v-html directive: <span v-html="rawHtml"></span></p>
  </div>

  <!-- Task 1c - Attribute Bindings -->
  <div class="task task1c">
    <p>Task 1c: Attribute Bindings</p>
    <div v-bind:id="dynamicId"></div>
  </div>
  

  <!-- Task 1d - JavaScript Expressions -->
  <div class="task task1d">
    <p>Task 1d: JavaScript Expressions</p>
    <div>{{ number + 1 }}</div>
    <div>{{ ok ? 'YES' : 'NO' }}</div>
    <div>{{ message.split('').reverse().join('') }}</div>
    <div :id="`list-${id}`"></div>
  </div>

  <!-- Task 1d - Conditional JavaScript Expression -->
  <div class="task task1d" v-if="ok">{{ message }}</div>

  <!-- Task 1d - Function Call -->
  <div class="task task1d">
    <p>Task 1d: Function Call</p>
    <time :title="toTitleDate(date)" :datetime="date">
      {{ formatDate(date) }}
    </time>
  </div> 
  
   <!-- Task 2 - Methods -->
  <div class="task task2">
    <p>Task 2: Methods</p>
    <button @click="incrementCounter" class="button">Increment Counter</button>
    <button @click="decrementCounter" class="button">Decrement Counter</button>
    <p>Counter for Task 2: {{ task2Counter }}</p>
  </div>

  <!-- Task 3 - Reactivity Fundamentals with ref() -->
  <div class="task task3">
    <p>Task 3: Reactivity Fundamentals with ref()</p>
    <div class="count-display">{{ count }}</div>
    <button @click="increment" class="button">Increment</button>
  </div>



  <!-- Task 4 - Computed Properties -->
  <div class="task task4">
    <p>Task 4: Computed Properties</p>
    <p>Has published books:</p>
    <span v-if="publishedBooksMessage">{{ publishedBooksMessage }}</span>
  </div>

  <!-- Task 5a - Binding HTML Classes -->
  <div class="task task5">
    <p>Task 5a: Binding HTML Classes</p>
    <div
      :class="{ active: isActive }"
      @click="toggleClass"
    >
      Toggle Class
    </div>
  </div>

  <!-- Task 5b - Binding Inline Styles -->
  <div class="task task5">
    <p>Task 5b: Binding Inline Styles</p>
    <div
      :style="{ color: textColor, fontSize: fontSize + 'px', backgroundColor: bgColor }"
    >
      Styled Text
    </div>
  </div>

  <!-- Task 6a - v-for with an Object -->
  <div class="task task6a">
    <p>Task 6a: v-for with an Object</p>
    <ul>
      <li v-for="(value, key) in myObject">
        {{ key }}: {{ value }}
      </li>
    </ul>
  </div>

  <!-- Task 6b - v-for with a Range -->
  <div class="task task6b">
    <p>Task 6b: v-for with a Range</p>
    <span v-for="n in 10">{{ n }}</span>
  </div>

  <!-- Task 6c - v-for on <template> -->
  <div class="task task6c">
    <p>Task 6c: v-for on &lt;template&gt;</p>
    <ul>
      <template v-for="item in items">
        <li>{{ item.msg }}</li>
        <li class="divider" role="presentation"></li>
      </template>
    </ul>
  </div>

    <!-- Task 6d - v-for with v-if -->
  <div class="task task6d">
    <p>Task 6d: v-for with v-if - only displays False tasks </p>
    <ul>
      <template v-for="todo in todos" :key="todo.id">
        <li v-if="!todo.isComplete">
          {{ todo.name }}
        </li>
      </template>
    </ul>
  </div>

  <!-- Task 6e - v-for with a Component -->
  <div class="task task6e">
    <p>Task 6e: v-for with a Component</p>
    <div class="task-items">
      <TaskItem
        v-for="(todo, index) in todos"
        :key="todo.id"
        :item="todo"
      />
    </div>
  </div>

  <!-- Task 7a - Using Inline Handlers -->
  <div class="task task7a">
    <p>Task 7a: Using Inline Handlers</p>
    <button @click="incrementCounter2">Increment Counter</button>
    <button @click="decrementCounter2">Decrement Counter</button>
    <p>Counter: {{ counter }}</p>
  </div>

  <!-- Task 7b - Using Method Handlers -->
  <div class="task task7b">
    <p>Task 7b: Using Method Handlers</p>
    <button @click="greetUser">Greet User</button>
  </div>

  <!-- Task 8a - v-model with Input Elements -->
  <div class="task task8a">
    <p>Task 8a: v-model with Input Elements</p>
    <p>Text Input: <input type="text" v-model="textInput" /></p>
    <p>Checkbox: <input type="checkbox" v-model="isChecked" /></p>
    <p>Radio:
      <input type="radio" id="radio1" value="Option 1" v-model="radioOption" />
      <label for="radio1">Option 1</label>
      <input type="radio" id="radio2" value="Option 2" v-model="radioOption" />
      <label for="radio2">Option 2</label>
    </p>
    <p>Dropdown:
      <select v-model="selectedOption">
        <option value="Option 1">Option 1</option>
        <option value="Option 2">Option 2</option>
        <option value="Option 3">Option 3</option>
      </select>
    </p>
    <p>Textarea: <textarea v-model="textAreaInput"></textarea></p>
  </div>

<!-- Task 8b - v-model Modifiers -->
<div class="task task8b">
  <p>Task 8b: v-model Modifiers</p>

  <!-- Lazy Modifier -->
  <p>Lazy Modifier: <input type="text" v-model.lazy="lazyText" /></p>
  <p>Lazy Text: {{ lazyText }}</p>
  
  <!-- Number Modifier -->
  <p>Number Modifier: <input type="number" v-model.number="numericValue" /></p>
  <p>Numeric Value: {{ numericValue }}</p>

  <!-- Trim Modifier -->
  <p>Trim Modifier: <input type="text" v-model.trim="trimmedText" /></p>
  <p>Trimmed Text: {{ trimmedText }}</p>
</div>

<!-- Task 9 - watchers -->
<div class="task task9">
  <p>
   Task 9 - Ask a yes/no question:
    <input v-model="question" />
  </p>
  <p>{{ answer }}</p>
  </div>

    <p>Task 10a&b</p>

  	<div :style="{ fontSize: postFontSize + 'em' }">
    <BlogPost
      v-for="post in posts"
      :key="post.id"
      :title="post.title"
      @enlarge-text="postFontSize += 0.1"
    ></BlogPost>
  </div>


   <!-- Using the AlertBox component with custom content -->
    <AlertBox>
      Something bad happened. 
    </AlertBox>


  
</template>

<script setup>
import { ref, computed, watch } from 'vue';
import TaskItem from './TaskItem.vue';
import BlogPost from './BlogPost.vue';
import Home from './Home.vue';
import About from './About.vue';
import NotFound from './NotFound.vue'

// Data property for Task 1a - Text Interpolation
const msg = 'Hello, Vue!'

// Data property for Task 1b - Raw HTML
const rawHtml = '<span style="color: red;">Im red!!</span>'

// Data property for Task 1c - Attribute Binding
const dynamicId = 'my-dynamic-id'

// Data properties for Task 1d - JavaScript Expressions
const number = 5
const ok = true
const message = 'Hello, World!'
const id = 42
const date = new Date()

// Helper functions for date formatting
const formatDate = (date) => {
  return date.toLocaleDateString()
}

const toTitleDate = (date) => {
  return date.toISOString()
}

// Data property for Task 3 - Reactivity Fundamentals with ref()
const count = ref(0)

// Function to increment the counter for Task 3
function increment() {
  count.value++
}

// Data property for Task 2 - Methods
const task2Counter = ref(0)

// Function to increment the counter for Task 2
function incrementCounter() {
  task2Counter.value++
}

// Function to decrement the counter for Task 2
function decrementCounter() {
  if (task2Counter.value > 0) {
    task2Counter.value--
  }
}

// Data for Task 4 - Computed Properties
const author = {
  name: 'Dev Gurung',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
}

// Computed property for Task 4
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})

// Data properties for Task 5a - Binding HTML Classes
const isActive = ref(false)

// Function to toggle the isActive class for Task 5a
function toggleClass() {
  isActive.value = !isActive.value
}

// Data properties for Task 5b - Binding Inline Styles
const textColor = ref('black')
const bgColor = ref('lightgray')

// Data for Task 6a - v-for with an Object
const myObject = {
  title: 'How to do lists in Vue',
  author: 'Mohamed El-Hassan',
  publishedAt: '2001-08-17'
}

// Data for Task 6b - v-for with a Range
// No additional data required for this task

// Data for Task 6c - v-for on <template>
const items = ref([{ msg: 'Item 1' }, { msg: 'Item 2' }, { msg: 'Item 3' }])

// Data for Task 6d and 6e - v-for with v-if
const todos = ref([
  { id: 1, name: 'Task 1', isComplete: false },
  { id: 2, name: 'Task 2', isComplete: true },
  { id: 3, name: 'Task 3', isComplete: false },
  // Add more todo objects as needed
]);


// Data for Task 7a
const counter = ref(0);

// Event handler methods for Task 7a
const incrementCounter2 = () => {
  counter.value++;
};

const decrementCounter2 = () => {
  if (counter.value > 0) {
    counter.value--;
  }
};


// Event handler method for Task 7b
const greetUser = () => {
  const name = 'Dev';
  alert(`Hello ${name}!`);
};


// Data properties for Task 8a - v-model with Input Elements
const textInput = ref('');
const isChecked = ref(false);
const radioOption = ref('');
const selectedOption = ref('');
const textAreaInput = ref('');

// Data properties for Task 8b - v-model Modifiers
const lazyText = ref('');
const numericValue = ref(0);
const trimmedText = ref('');

//Data for Task 9 - watchers

const question = ref('')
const answer = ref('Questions usually contain a question mark. ;-)')

// watch works directly on a ref
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.indexOf('?') > -1) {
    answer.value = 'Thinking...'
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    } catch (error) {
      answer.value = 'Error! Could not reach the API. ' + error
    }
  }
})


const posts = ref([
  { id: 1, title: 'Hello' },
  { id: 2, title: 'Dev' },
  { id: 3, title: ':)' }
])

const postFontSize = ref(1)

// Import the AlertBox component
import AlertBox from './AlertBox.vue';

const routes = {
  '/': Home,
  '/about': About
}

const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})

</script>

<style scoped>

/* Style for Task 5a - Binding HTML Classes */
.task5 .active {
  background-color: yellow;
  color: black; 
  cursor: pointer;
}

/* Style for Task 5b - Binding Inline Styles */
.task5 div {
  margin-top: 1rem;
  padding: 1rem;
  cursor: pointer;
  color: black; 
  background-color: lightgray; 
}

/* Styles for Task 6 */
/* Style for Task 6a - v-for with an Object */
.task6a ul {
  list-style-type: none;
  padding: 0;
}

.task6a li {
  margin-bottom: 0.5rem;
}

/* Style for Task 6b - v-for with a Range */
.task6b span {
  margin-right: 0.5rem;
}

/* Style for Task 6c - v-for on <template> */
.task6c ul {
  list-style-type: none;
  padding: 0;
}

.task6c li {
  margin-bottom: 0.5rem;
}

.task6c .divider {
  border-top: 1px solid #ccc;
  margin: 0.25rem 0;
}

/* Style for Task 6e - v-for with a Component */
.task6e .task-items {
  display: flex;
  flex-direction: column;
}

.alert-box {
  /* ... */
}
</style>
