<script context="module">
  const authorColors = {}
</script>

<section class="message" class:mine={message.author === me}>
  <span class="author {authorColors[message.author]}">
    {message.author}
  </span>

  {message.body}
</section>

<script>
  export let message, me

  const colors = [
    'text-red-500',
    'text-green-500',
    'text-purple-500',
    'text-yellow-500',
    'text-teal-500',
    'text-pink-500',
    'text-blue-500',
    'text-orange-500',
    'text-indigo-500',
  ]

  /**
   * What's happening here is that we're assigning a color
   * to each author. So that we can make their names
   * visually distinct in the chat box.
   */
  if (message.author !== me && !authorColors[message.author]) {
    const i = Object.keys(authorColors).length
    const n = colors.length
    authorColors[message.author] = colors[i%n]
  }
</script>

<style>
  .message {
    @apply float-left inline-block
           shadow-sm
           rounded-lg border border-gray-200
           mr-16 pp-2 max-h-full overflow-hidden
           bg-white;
  }

  .mine {
    @apply float-right mr-0 ml-16
           border-green-300 bg-green-200;

    .author {
      @apply hidden;
    }
  }

  .author {
    @apply block text-xs font-medium;
  }
</style>